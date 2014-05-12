# Foreword

To be updated from [standard foreword boiler plate text] (http://www.buildingsmart-tech.org/ifc/IFC4/final/html/foreword.htm)

# Introduction

## Purpose
With the publication of the IFC4 release, that has been accepted as ISO16739 by the International Standardization Organization, several enhancements and improvements over the previous IFC releases are now available for improved open BIM interoperability using the IFC protocol.

The main purpose of this document is to define a standardized subset of the IFC4 schema, a Model View Definition MVD, that is particularly suitable for all BIM workflows that are based on reference models, where the exchange is mainly one-directional. Here requested modifications of the BIM data, mainly of the shape representation, are handled by a change request to the original author, and changes not executed upon the imported IFC data to be sent back to the original source.

Examples of this reference workflow are:
- Coordination planning (combining different discipline specific IFC models for visual checking)
- Clash detection (finding clashes between different discipline specific IFC models)
- Background reference (loading an IFC model, usually from a different discipline) as a linked model
- Quantity take-off (determine the quantities of the various model elements with the IFC model)
- Construction sequencing (taking the IFC model and associating it to a construction schedule)
- Visual presentation (for presenting the IFC model to a broad audience)

Common characteristics of the workflow using reference models are:
- The source of the BIM information remains with the originator
- The full parametric behaviour, and thereby the intellectual engineering property, remains with the originator
- The ownership of the model, and responsibility for its correctness, remains with the originator 
- The original model is published as IFC4 Reference View model reflecting the as-is status
- The receiver of the IFC4 Reference View model has access to the full model content
- The receiver of the IFC4 Reference View is not supposed to modify the model
- The receiver of the IFC4 Reference View can analyse and extract the information of the model
- If the receiver suggests or demands a change, it has to be communicated as a change request to the originator
- The buildingSMART standard BCF (BIM Collaboration Format) is developed to efficiently support these change requests. 

The Level of Detail of the shape representation and the Level of Information for the property content of the actual reference models depends on the source model. The buildingSMART standard IDM (Information Delivery Manual) can be used to determine the minimum content for a particular workflow support. The IFC4 Reference View allows rich content to be published, see next chapter Objective for more details. 

## Objective
The main objective of the IFC Reference View is the widest possible proliferation of IFC BIM data across a big range of software application types supporting different communication and collaboration workflows.

The IFC Reference View is characterized by the ability to publish BIM data following that subset of IFC definitions that enables semantically rish content of building data, and to some degree also other built environment data, to be exchanges with a streamlined geometric representation that is optimized for analysis and display, but excludes dimension-driven geometric parameters. The geometric representation is therefore suitable for all workflow scenarios, where the imported IFC model is displayed, analysed, compared, clashed, but not parametricly modified for futher work processes.

Semantic building data models being exchanged using the IFC4 Reference View would typically include:
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

Additional capabilities for enriching the semantic information exposed by the IFC4 Reference View can be defined as an Add-on Model View Definition. Forseeable examples are capturing 4D models with the addition of the work schedule related entities, or 5D models with the addition of construction resource related entities.

## Workflow support
The overall goal of the IFC Reference View is to provide workflows where building information models are to be consumed by the widest array of software applications that do not require modifying geometry. Such applications enable viewing, estimating, building, operating, and other downstream analysis. 

> EXAMPLE One target scenario is an architect providing building design information to a contractor or facility manager. It is expected that the resulting geometry would reflect sufficient realism for viewing in software (dimensions, normals, colors, textures), but not of rendering quality for artistic presentations (lighting, shader effects, curve interpolation, rasterizing).

To support the widest array of consuming applications, the resulting schema should be as limited as possible for representing geometry in the interest of minimizing resources required of application developers. Such schema should also be as compact as possible to enable downstream use on mobile devices with limited network bandwidth. It is proposed that the resulting geometry is limited to triangles with normal vectors and texture coordinates and simple sweeped solids with applied textures.

## Compatibility concerns

As the IFC4 Reference View is new (there is no corresponding concept in the IFC2x3 Coordination View), there is no constraint for compatibility, and the resulting schema will leverage new triangulation definitions in IFC4 to support more efficient data transfer.

# 1 Scope

## 1.1 General scope definition

### 1.1.1 Model elements
The main components of the IFC4 Reference View are the semantic model elements that carry a predefined meaning. The complete breakdown of all model elements declared in IFC4 are also known as the IFC4 built-in classification following an element by function classification.

**Architectural model elements**

| shell and core | finishing, etc. |
|----------------|-----------------|
| IfcBeam        | IfcCovering 
| IfcColumn      | IfcRailing
| IfcChimney *   | IfcShadingDevice
| IfcRamp +      | IfcCurtainWall
| IfcStair ++    | IfcDoor
| IfcRoof        | IfcWindow
| IfcSlab        | IfcFurniture
| IfcWall        | IfcSystemFurnitureElement

> Legend: * new in IFC4, + includes IfcRampFlight, ++ includes IfcStairFlight


**Structural model elements**

| Foundation | Frame     | Reinforcement      | Fastener, etc. |
|------------|-----------|--------------------|----------------|
| IfcFooting | IfcMember | IfcReinforcingBar  | IfcFastener
| IfcPile    | IfcPlate  | IfcReinforcingMesh | IfcMechanicalFastener
|            |           | IfcTendonAnchor    | IfcBuildingElementPart
|            |           | IfcTendon          | IfcDiscreteAccessory

> NOTE: Architectural elements, like IfcWall, IfcSlab, IfcBeam, etc, are also used in structural models, and vice versa

**Building service model elements**

**Other model elements**

| Other elements |
|----------------|
| IfcBuildingElementProxy +
| IfcCivilElement *++
| IfcGeographicElement *
| IfcDistributionChamberElement
| IfcElementAssembly
| IfcTransportElement

> Legend: * new in IFC4, + also used as general element proxy ++ provided as stub for future infrastructure extensions


**Spatial elements, spatial structure and grouping elements**

| Spatial structure | other structure          | others  |
|-------------------|--------------------------|---------|
| IfcSpace          | IfcZone                  | IfcGrid
| IfcBuildingStorey | IfcSystem                |
| IfcBuilding       | IfcBuildingSystem *      |
| IfcSite           | IfcDistributionSystem *  |
| IfcSpatialZone *+ | IfcDistributionCircuit * |
|                   | IfcGroup                 |

> Legend: * new in IFC4, + provided as a stub for non vertical constructions


### 1.1.2 Geometric shape representation
The objective of the IFC4 Reference View is to enable the exchange of highly accurate, not non-parametric, geometric representations of the model elements. In order to minimize the effort for receiving and interpreting the geometic representations by the receiving software systems, in terms of development effort, processing power and loading times, the complexity and variety of geometric models has been minimized for the IFC4 Reference View.

In scope of geometric shape representations of physical and spatial elements is:
- tessellated geometry

It is the default geometric representation of all model elements, allowing for a surface model representation with an indicator for closed shells (and therefore true volumes). The tessellated representation offers a very efficient way of exchanging 3D shape date, both for data set sizes and for processing time. Optionally the face normals can be exchanged as well.

Since curved shapes would lead to very densely triangulated areas, the following swept solid based representations are also in scope of the IFC4 Reference View, balancing simplicity and compactness of representation:

- extruded solid geometry
- revolved solid geometry
- advanced swept solid geometry of circular cross sections

All other geometric models are out of scope of the IFC4 Reference View, in particular Boolean operations required for Constructive Solid Geometry CSG.

> NOTE: The IFC2x3 Coordination View included CSG capabilities, the IFC4 Reference View therefore imposes a more restricted geometric representation of model elements. The IFC4 Design Handover View should be used, if more complex geometric representations are required by the workflow. In particular, if a dimension-driven parametric representation, used by the IFC4 standard case elements, is needed.

### 1.1.3 Geometric presentation
Visual appearance is an important factor for the communication process using BIM data. The objective is not to support photo-realistic rendering of reference models, but to use color, basic rendering, and texture information to add visually accessible meaning to the model elements.
 
In scope of presentation capabilities for the appearance of model element shapes are:
- coloring, as single color or rendering per solid, or as one color per face
- texturing

The visually adaquate presentation of model elements is constraint by the shapre representation
- for tessellated geometry: color per face, texture per face
- for swept solid geometry: color and rendering information per solid, texture applied to solid using standard mapping

### 1.1.4 Property information
