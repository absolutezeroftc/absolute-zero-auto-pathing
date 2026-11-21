# Absolute Zero — Auto Pathing

Static site showing every autonomous route for **Team Absolute Zero**, BioBuzz (2026–2027).

**Live:** https://absolutezeroftc.github.io/absolute-zero-auto-pathing/

Each route is drawn point-for-point on the official BioBuzz field, with its waypoint table,
headings, control points and the exact Java that builds it.

## Routes

| Route | Alliance | Legs | Path length |
|---|---|---|---|
| Red Left | Red | 4 + park | 211″ |
| Blue Left | Blue | 4 + park | 211″ |
| Red Middle | Red | 4 + park | 217″ |
| Blue Middle | Blue | 4 + park | 217″ |
| Red Right | Red | 4 + park | 258″ |
| Blue Right | Blue | 4 + park | 258″ |
| Blue Left Left | Blue | 5 + park | 400″ |

## Where the drawings come from

The path geometry is the [Pedro Pathing Visualizer](https://visualizer.pedropathing.com)'s own
rendered output, captured as SVG and composited over the official BioBuzz field image. The curves
are Pedro's actual Bézier math for the control points in the robot code, not an approximation.

## Accuracy

Every coordinate was read directly from the Java sources in
`TeamCode/src/main/java/org/firstinspires/ftc/teamcode/auto/` of the
[robot repo](https://github.com/RoboticsForYouth/az-biobuzz-pp-quickstart), then verified three ways:

- a script re-extracted every point from each drawn SVG and diffed it against the Java poses —
  all seven routes matched exactly, including control points and the park spot;
- all three red/blue mirror pairs are identical leg-for-leg;
- the computed length for Red Left (211″) matches what the visualizer reported independently.

No drive times are shown anywhere: Pedro is not tuned yet (`pedro/Constants.java` still holds
placeholders), so any time estimate would be fiction.

## Known gap

The `singleshooter` (1S) code set has no turret, so its autos insert a short `approachPath()`
toward the hive — up to 8″ — before shooting at each point. 1T and 2T shoot in place.
**Those approach segments are not drawn**, because they aim at `FieldPositions.Blue.GOAL`, which
is still a `TODO(field)` placeholder at `(14, 130)`. They can be added once the real goal pose is
measured.

## Contents

Plain HTML and one CSS file. No JavaScript, no build step — open `index.html`.
