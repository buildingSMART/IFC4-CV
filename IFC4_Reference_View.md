# Foreword

To be updated from [standard foreword boiler plate text] (http://www.buildingsmart-tech.org/ifc/IFC4/final/html/foreword.htm)

# Introduction

## Background


## Motivation


## Workflow support
The overall goal of the Reference View is to provide workflows where building information models are to be consumed by the widest array of software applications that do not require modifying geometry. Such applications enable viewing, estimating, building, operating, and other downstream analysis. 

> EXAMPLE One target scenario is an architect providing building design information to a contractor or facility manager. It is expected that the resulting geometry would reflect sufficient realism for viewing in software (dimensions, normals, colors, textures), but not of rendering quality for artistic presentations (lighting, shader effects, curve interpolation, rasterizing).

To support the widest array of consuming applications, the resulting schema should be as limited as possible for representing geometry in the interest of minimizing resources required of application developers. Such schema should also be as compact as possible to enable downstream use on mobile devices with limited network bandwidth. It is proposed that the resulting geometry is limited to triangles with normal vectors and texture coordinates and simple sweeped solids with applied textures.

## Compatibility concerns

As the IFC4 Reference View is new (there is no corresponding concept in the IFC2x3 Coordination View), there is no constraint for compatibility, and the resulting schema will leverage new triangulation definitions in IFC4 to support more efficient data transfer.

# 1 Scope

# 2 Normative references

# 3 Terms, definitions, and abbreviated terms

# 4 Fundamental concepts and assumptions

