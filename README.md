# iprs-geometry

Dimensions of the inverted planetary roller screw mechanism

TL;DR

|     | PRS (common knowledge) | IPRS (this paper) |
|---------|----------|----------|
| screw  | `nut * (starts - 2 ) / starts`    | `nut * starts / (starts + 2)`   |
| roller | `nut / starts` | `nut / (starts + 2)`  |

  - [Abstract](#abstract)
  - [Introduction](#introduction)
  - [Geometry](#geometry)
    - [Planetary geometry](#planetary-geometry)
    - [Thread starts](#thread-starts)
    - [PRS geometry](#prs-geometry)
    - [IPRS geometry](#iprs-geometry)
    - [Differences between PRS and IPRS geometry](#differences-between-prs-and-iprs-geometry)
  - [Discussion](#discussion)
  - [Conclusion](#conclusion)
  - [References](#references)
  - [Citations](#citations)

# Dimensions of the inverted planetary roller screw mechanism

## Abstract

Planetary roller screws (PRS) and inverted planetary roller screws (IPRS) are mechanisms
that convert rotation into linear movement. A spur gear on the roller prevents roller over/under rotation.
In a PRS the second gear is a ring gear on the nut, whereas in an IPRS, the second gear is on the screw.
This difference results in different screw and roller geometry calculations for the PRS and IPRS mechanisms. The thread start count multiplied by the roller radius defines a critical radius. For a PRS it is the nut radius, but for an IPRS it is the screw radius. The remaining geometry is derived from this relationship.

## Introduction

The roller screw is family of mechanisms that turns rotation into linear movement.
It is first described in a 1954 patent by Carl Bruno Strandgren [1]. The roller screw may be a planetary roller screw (PRS) or an inverted planetary roller screw (IPRS).

They consists of a nut, carrier-bound planetary threaded rods, a screw and a spur gear.
The key defining parameters of the mechanism are the nut diameter, the thread pitch and the
number of thread starts in the screw and nut.

The nut and the screw have the same number of thread starts and the planet typically has a single
thread start.

The spur gear ensures the rollers do not over- or under-rotate and cause axial migration and
mechanism failure. The rollers have a spur gear cut into the ends of the thread.
The counterpart to the spur gear depends on whether the mechanism is a PRS or and IRPS.

A PRS has the spur gear is a ring gear in the nut and the planet moves along a hypocycloid (inside the nut). An IPRS has the spur gear is a gear on the screw and the planet moves along an epicyclioid (around the surface of the screw).

This difference in spur gear location is the reason that the PRS and IPRS have
different geometry. This work presents the IPRS geometry which was previously absent from literature.

## Geometry

### Planetary geometry

The screw is orbited by the planetary rollers, and this must fit in the nut

```
diameter_nut = diameter_screw + 2 * diameter_roller
```
Or using radii:
```
radius_nut = radius_screw + 2 * radius_roller   (1)
```

### Thread starts

The thread starts on the nut and screw act as teeth that mesh with the single tooth on the planet.

For every rotation of the nut or screw, the planet must rotate once for every thread start:
- Roller inside nut. Both static and rotating on their axes.
    - For every rotation of the nut, the roller rotates once for every thread start
- Roller beside screw. Both static and rotating on their axes.
    - For every rotation of the screw, the roller rotates once for every thread start

Hence the general rule is:
```
spur_gear_ratio = num_thread_starts
```

The PRS has a long screw, a short nut and the spur gear is a ring gear on the nut.
The IPRS has a long nut, a short screw and the spur gear is a spur gear on the screw.

In the PRS (gear on nut), for every rotation of the nut, the roller rotates thread start times.
In the IPRS (gear on rod), for every rotation of the screw, the roller rotates thread start times.

Thus, the relationsips are:
```
radius_nut_prs = num_thread_starts * radius_roller_prs (2)
```
```
radius_screw_iprs = num_thread_starts * radius_roller_iprs (3)
```

### PRS geometry

For PRS, rearrange (2) to get the roller size:

```
radius_roller_prs = radius_nut_prs / num_thread_starts       (4)
```
Recall (1)
```
radius_nut_prs = radius_screw_prs + 2 * radius_roller_prs       (5)
```
Substitute (4) into (5) to get the the screw size:
```
radius_nut_prs = radius_screw_prs + 2 * radius_nut_prs / num_thread_starts
```
Rearrange and simplify:
```
radius_nut_prs = radius_screw_prs + 2 * radius_nut_prs / num_thread_starts
```
```
radius_screw_prs = radius_nut_prs - 2 * radius_nut_prs / num_thread_starts
```
```
radius_screw_prs = radius_nut_prs * (1 - 2 / num_thread_starts)        (6)
```

Thus, fo a given nut size and thread start count, the PRS geomery of the roller and screw are defined by (4) and (6).

### IPRS geometry

For PRS, recall (1)
```
radius_nut_iprs = radius_screw_iprs + 2 * radius_roller_iprs      (7)
```
Substitute (2) into (7):
```
radius_nut_iprs = num_thread_starts * radius_roller_iprs + 2 * radius_roller_iprs
```
Simplify:
```
radius_roller_iprs = radius_nut_iprs / (num_thread_starts + 2)        (8)
```
Recall (3) and rearrange:
```
radius_screw_iprs = num_thread_starts * radius_roller_iprs
```
```
radius_roller_iprs = radius_screw_iprs / num_thread_starts      (9)
```
Substitute (9) into (7)
```
radius_nut_iprs = radius_screw_iprs + 2 * radius_screw_iprs / num_thread_starts
```
Rearrange and simplify:
```
radius_screw_iprs = radius_nut_iprs * num_thread_starts / (num_thread_starts + 2)       (10)
```

Thus, fo a given nut size and thread start count, the IPRS geomery of the roller and screw are defined by (8) and (10).

### Differences between PRS and IPRS geometry

From the above equations, the relative size of the nut to the screw can be found as a function
of the number of thread starts.

For PRS, substitute (4) into (5):
```
radius_nut_prs = radius_screw_prs + 2 * radius_nut_prs / num_thread_starts
```
```
radius_nut_prs * (1 - 2 / num_thread_starts) = radius_screw_prs
```
```
radius_nut_prs * (num_thread_starts - 2) / num_thread_starts = radius_screw_prs
```
Rearrange:
```
radius_nut_prs/radius_screw_prs = num_thread_starts / (num_thread_starts - 2)
```
```
nut_to_screw_multiple_prs = num_thread_starts / (num_thread_starts - 2)        (11)
```
For IPRS, rearrange (10):
```
radius_screw_iprs = radius_nut_iprs * num_thread_starts / (num_thread_starts + 2)
```
```
nut_to_screw_multiple_iprs = (num_thread_starts + 2) / num_thread_starts     (12)
```

For a given nut size and number of starts, an IPRS has a larger screw and smaller rollers
than a PRS.

Where (12) is a hyperbola that asymptotes to num_thread_starts=0, (11) asymptotes to num_thread_starts=2.
This implies that a PRS must at least 3 thread starts, but an IPRS must have 1 or more.


## Discussion

The use of the PRS geometry equations in an IPRS design causes the
roller to interact with a the screw at a pitch circle that is too close
to the roller. The result is axial migration of rollers and spur gear locking.

The PRS equation restricts the thread start count to three but the IPRS equation does not (may have one or more). As lower thread starts results in a lower lead, this
configuration could be favourable for applications that require a large mechanical advantage. An IPRS with one thread start have
rollers the same diameter as the screw and would provide three times the mechanical advantage of an equivalent screw with three thread starts.

## Conclusion

The IPRS mechanism has a spur gear pair that involves the screw, rather than the nut. As such,
the geometry of the IPRS is defined by differently to the PRS.

PRS geometry:

```
radius_roller_prs = radius_nut_prs / num_thread_starts
```
```
radius_screw_prs = radius_nut_prs * (num_thread_starts - 2 ) / num_thread_starts
```
IPRS geometry:
```
radius_roller_iprs = radius_nut_iprs / (num_thread_starts + 2)
```
```
radius_screw_iprs = radius_nut_iprs * num_thread_starts / (num_thread_starts + 2)
```

These relationships allow the sound construction of an IPRS.
They also show that unlike a PRS, an IPRS can also be constructed with fewer than three thread starts. This is relevant for applications requiring high mechanical advantage.

## References

1. Strandgren, Carl Bruno, "Screw-threaded mechanism", published 1954-07-13

## Citations

```
cff-version: 1.2.0
message: "If you would like to refer this work, please cite it as below."
authors:
- family-names: "scifi"
  given-names: "ceramic"
title: "Dimensions of the inverted planetary roller screw mechanism"
version: 0.1.0
date-released: 2024-05-23
url: "https://github.com/ceramic-sf/iprs-geometry"
```
