# Foreword

To be updated from [standard foreword boiler plate text] (http://www.buildingsmart-tech.org/ifc/IFC4/final/html/foreword.htm)

# Introduction

## Background
With the publication of the IFC4 release, that has been accepted as ISO16739 by the International Standardization Organization, several enhancements and improvements over the previous IFC releases are now available for improved open BIM interoperability using the IFC protocol.

The main purpose of this document is to define a standardized subset of the IFC4 schema, a Model View Definition MVD, that is particularly suitable for all BIM workflows, where the the exchange is mainly one-directional. Here requested modifications of the BIM data, mainly of the shape representation, are handled by a change request, and are not executed upon the imported IFC data.

Examples of this workflow are:
- Coordination planning (combining different discipline specific IFC models for visual checking)
- Clash detection (finding clashes between different discipline specific IFC models)
- Background reference (loading an IFC model, usually from a different discipline) as a linked model
- Quantity take-off (determine the quantities of the various model elements)
- Construction sequencing (taking the IFC model and associating it to a construction schedule)
- Visual presentation (for presenting the IFC model to a broad audience)
- ...


## Objective
The main objective of the IFC Reference View is the widest possible proliferation of open-format BIM data across a big range of software application types supporting different communication and collaboration workflows.

The IFC Reference View is characterized by the ability to publish BIM data following that subset of IFC definitions that enables semantically rish content of building data, and to some degree also other built environment data, to be exchanges with a streamlined geometric representation that is optimized for analysis and display, but excludes dimension-driven geometric parameters. The geometric representation is therefore suitable for all workflow scenarios, where the imported IFC model is displayed, analysed, compared, clashed, but not parametriclly modified for futher work processes.

Semantic building data models being exchanged using the IFC Reference View would typically include:
- physical elements with explicit geometry, properties, quantities, material, and classification
- types of elements with associated physical elements to group common definitions (geometry, properties, material, and classification)
- spatial elements (spaces, zones) with explicit geometry, properties, quantities, and classification
- spatial structure elements (site, building, story), but also spatial zones for non-vertical construction
- element breakdown structure between physical elements (assemblies, sub-assemblies, parts)
- spatial breakdown structure between spatial elements (spatial decomposition of building, story or zones)
- spatial containment structure between spatial elements and physical elements (elements in spatial zone)
- logical system structure and assignment (physical elements assigned to systems and sub systems)
- topological structure of system networks (element to port, and port to port, relationship)
- common context of the building model, providing units, coordinate system and GIS positions
- general object identification using globally unique identifier

The scope of geometric shape representations of physical and spatial elements is:
- tesselated geometry
- basic swept solid geometry
- advanced swept solid geometry of circular cross sections

with the scope for presentation capabilities:
- coloring (per solid, per face)
- rendering
- texturing

for visually adaquate representations of model elements that are semantically rich in terms of property content and relationships to other elements and structures. 

## Workflow support
The overall goal of the IFC Reference View is to provide workflows where building information models are to be consumed by the widest array of software applications that do not require modifying geometry. Such applications enable viewing, estimating, building, operating, and other downstream analysis. 

> EXAMPLE One target scenario is an architect providing building design information to a contractor or facility manager. It is expected that the resulting geometry would reflect sufficient realism for viewing in software (dimensions, normals, colors, textures), but not of rendering quality for artistic presentations (lighting, shader effects, curve interpolation, rasterizing).

To support the widest array of consuming applications, the resulting schema should be as limited as possible for representing geometry in the interest of minimizing resources required of application developers. Such schema should also be as compact as possible to enable downstream use on mobile devices with limited network bandwidth. It is proposed that the resulting geometry is limited to triangles with normal vectors and texture coordinates and simple sweeped solids with applied textures.

## Compatibility concerns

As the IFC4 Reference View is new (there is no corresponding concept in the IFC2x3 Coordination View), there is no constraint for compatibility, and the resulting schema will leverage new triangulation definitions in IFC4 to support more efficient data transfer.

# 1 Scope



