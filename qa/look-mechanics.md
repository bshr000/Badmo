# 坏墨 look mechanics

## Natural motion

坏墨 is a compact soft-bodied fox-cat with a separate head, large physical eyes, two ears (one folded), a fluffy tail, and a snug scarf. The paws and lower torso stay anchored to one stable baseline. The eyes lead each look by rotating together inside their existing apertures; eyelids reshape subtly. The head follows with restrained yaw or pitch, then the upper chest and ears follow by a smaller amount. The tail and scarf knot remain attached and lag only slightly. No whole-sprite rotation, affine tilt, or broad raster warp is appropriate.

## Motion budget

Every 22.5-degree step changes the eyes first, then head angle, then a small upper-body follow-through by roughly equal visual increments. Body height, foot position, tail root, scarf attachment, folded-ear identity, and overall scale remain stable. The turn must never cause a lateral registration jump, prop flip, or sudden silhouette pop.

## Cardinal pose families

- `000 up`: both pupils sit clearly above eye centers; upper eyelids open toward the brow; muzzle tips slightly upward; chin lifts; ear tips follow upward. The lower body and tail root remain fixed. More underside of the muzzle is visible; scarf stays centered and attached.
- `090 screen-right`: pupils and nose tip cross to the image-right side of the head center; head yaws right; the image-left cheek and ear become more visible while the far cheek compresses slightly. The folded ear remains identifiable. Scarf knot follows the chest without switching sides.
- `180 down`: both pupils sit clearly below eye centers; eyelids lower; muzzle and chin tuck; ears angle forward slightly. More forehead is visible while the lower face is mildly occluded. Feet, torso base, tail root, and scarf attachment remain anchored.
- `270 screen-left`: pupils and nose tip cross to the image-left side of the head center; head yaws left; the image-right cheek and ear become more visible while the far cheek compresses slightly. This must visibly oppose `090`. The folded ear remains identifiable and the scarf stays attached.

## Interpolation and continuity

Diagonals combine both required axes: up-right/up-left show elevated pupils plus the corresponding head yaw; down-right/down-left show lowered pupils plus the corresponding yaw. The loop advances clockwise in even steps with no backtracking. `157.5 -> 180`, `337.5 -> 000`, and the row boundary must be one ordinary step. The neutral/rest pose is not a direction and must remain visually distinct from every look cell.

## Eye, ear, tail, and scarf constraints

Preserve the original jade eye construction, whites, pupils, rims, highlights, and eyelids as one physical system; never add replacement googly eyes or detached eye dots. The upright ear leads subtly and the folded ear follows without unfolding. Tail motion is minimal and continuous at its rooted base. The short vermilion scarf knot stays snug against the neck with no loose floating ends, side swap, or detached red component.
