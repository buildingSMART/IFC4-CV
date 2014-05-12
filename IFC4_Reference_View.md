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

The second Model View Definition that is proposed in parallel to the IFC4 Reference View, the IFC4 Design Transfer View, is an extension of this model view. In other words, the IFC4 Reference View is a true subset of the IFC4 Design Transfer View.

Complying software interfaces, that implements import of the IFC4 Design Transfer View, shall also be able to correctly import IFC4 Reference View data sets. But not vice versa, a complying software interface, that implements import of the IFC4 Reference View will not be capable to import IFC4 Design Transfer View data sets. It is however required that a compliant software interface for importing IFC4 Reference View displays an agreed error messange showing the IFC version, and the IFC Model View Definition of the imported IFC file, that does not match "IFC4 Reference View" with an explanation, that a non-compatible IFC file has been received.

> NOTE The correct error message and the link to further information on the buildingSMART website explaining the purpose of the different IFC Model View Deinitions need to be agreed upon.

# 1 Scope

## 1.1 General scope definition
The general scope defines the main functionalities of the IFC4 Reference View as an overview. It includes a complete listing of the model elements and model element types that are included in the Model View Definition.

The detailed scope of the IFC4 Reference View is determined by the concept templates that are included. A detailed description of each concept template is provided by "4 Fundamental concepts and assumptions".

## 1.2 Model elements
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

| Foundation & Frame | Reinforcement      | Fastener, etc. |
|--------------------|--------------------|----------------|
| IfcFooting         | IfcReinforcingBar  | IfcFastener
| IfcPile            | IfcReinforcingMesh | IfcMechanicalFastener
| IfcMember          | IfcTendonAnchor    | IfcBuildingElementPart
| IfcPlate-          | IfcTendon          | IfcDiscreteAccessory

> NOTE: Architectural elements, like IfcWall, IfcSlab, IfcBeam, etc, are also used in structural models, and vice versa

**Building service model elements**

The model element specialization structure within the building service domain within the IFC standard is organized accoring to its function within a distribution system, and not primarily according to the main building service discipline, within it is mainly used.

The internal specialization structure for building service elements at its highest level is also independed of the fluid used within the distribution system:
- flow segments
- flow fittings
- flow terminals
- flow moving devices
- flow storage devices
- flow controller
- energy conversion device
- distribution control elements

The following tables intents to assign the model elements to the various disciplines within the building service system domain.

| general MEP elements  | used for gases and fluids | ports for connectivity |
| ----------------------|---------------------------|------------------------|
| IfcEngine *           | IfcFlowMeter *            | IfcDistributionPort    |
| IfcMedicalDevice *    | IfcFilter *               | -                      |
| IfcUnitaryEquipment * | -                         | -                      |


| Heating, Cooling   | Plumbing                     | Common         |
|--------------------|------------------------------|----------------|
| IfcBoiler *        | IfcFireSuppressionTerminal * | IfcPipeSegment *
| IfcBurner *        | IfcInterceptor *             | IfcPipeFitting *
| IfcCoil *          | IfcSanitaryTerminal *        | IfcPump *
| IfcSpaceHeater *   | IfcStackTerminal *           | IfcValve *
| IfcTubeBundle *    | IfcTank *                    | -
| -                  | IfcWasteTerminal *           | -


| Ventilation         | Air conditioning          | Common
| --------------------|---------------------------|-------
| IfcAirTerminalBox * | IfcAirToAirHeatRecovery * | IfcDuctSegment *
| IfcDamper *         | IfcChiller *              | IfcDuctFitting *
| IfcDuctSilencer *   | IfcCondenser *            | IfcAirTerminal *
| -                   | IfcCooledBeam *           | IcFan *
| -                   | IfcCoolingTower *         | -
| -                   | IfcEvaporativeCooler *    | -
| -                   | IfcEvaporator *           | -
| -                   | IfcHeatExchanger *        | -
| -                   | IfcHumidifier *           | -
| -                   | IfcCompressor *           | -


| Electrical                     | cont.                       | Common
|--------------------------------|-----------------------------|-------
| IfcElectricAppliance *         | IfcAudioVisualAppliance *   | IfcCableSegment *
| IfcElectricDistributionBoard * | IfcCommunicationAppliance * | IfcCableFitting *
| IfcElectricGenerator *         | IfcJunctionBox *            | IfcCableCarrierSegment *
| IfcElectricMotor *             | IfcLamp *                   | IfcCableCarrierFitting *
| IfcElectricStorageDevice *     | IfcLightFixture *           | -
| IfcElectricTimeControl *       | IfcSolarDevice *            | -
| IfcMotorConnection *           | IfcSwitchingDevice *        | -
| IfcProtectiveDevice *          | IfcTransformer *            | -


| Building automation   | cont.                              | cont.
|-----------------------|-----------------------------------|------
| IfcActuator *         | IfcFlowInstrument *               | IfcSensor *
| IfcAlarm *            | IfcProtectiveDeviceTrippingUnit * | -
| IfcController *       | IfcUnitaryControlElement *        | -

> Legend * new in IFC4, note all building service occurrence elements are new, the previous IFC2x3 release only included the generic occurrence elements: _IfcFlowSegment_, _IfcFlowFitting_, _IfcFlowTerminal_, _IfcFlowMovingDevice_, _IfcFlowStorageDevice_, _IfcFlowController_, _IfcEnergyConversionDevice_ and _DistributionControlElement_
 

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


### 1.3 Model element types
Model element types are part of the IFC4 Reference View. They enable to describe and share common model element information that are shared by multiple occurrences of the same type. Sharable type information includes:
- Geometric shape representation;
- Property information;
- Material information.

> EXAMPLE: A particular air outlet as an article, with its shape, its material and its manufacturer information being described once as a type and then having several occurrences, each placed within the building, referencing the same type and hence its shape, material and properties.


## 1.4 Overview on major concepts used

### 1.4.1 Object attribute
All model elements, listed in the previous section, are defined by several generic and direct object attributes, some specific model elements do carry additional direct attributes. The usage of the direct generic attributes is defined within the following concept templates (see also Chapter 4 "fundamental concepts and assumptions"):
- "_Software Identity_", it defines how to apply the Globally Unique Id and how to compress it during exchange;
- "_User identity_", it defins the meaning of _Name_, _Description_, _LongName_ and _Tag_ attributes;
- "_Object occurrence predefined type_", it defines how to use the _PredefinedType_ and in case of user defined types, how to assign the user defined type information within the _ObjectType_ attribute for occurrences of model elements;
- "_Element type predefined type_" it defines how to use the _PredefinedType_ and in case of user defined types, how to assign the user defined type information within the _ElementType_ attribute for types of model elements.


### 1.4.2 Project context
There is a single instance of _IfcProject_ within each IFC data set. It sets the context for the exchange, including units, geometric context, global positioning and classification systems used within the data set. The usage of the project context is defined within the following concept templates (see also Chapter 4 "fundamental concepts and assumptions"):
- "_Project Units_", declaration of the units used within this data set, all geometric representations are forced to use the global units (e.g. for length measure and plane angle measure), property values may override global unit declarations;
- "_Project Representation Context_", declaration of the 3D and 2D representation contexts, including precision factors;
- "_Project Global Positioning_" (new in IFC4), positioning the project engineering coordinate system (right handed Cartesian coordinate system) within a global coordinate reference system;
- "_Project Classification Information_", providing the name and version information about the classification systems used within the data set.


### 1.4.3 Object definition
A main objective of the IFC4 Reference View is to enable rich information content for each model element. General properties or attributes are attached to model elements as propert sets, either directly to the model element occurrence, or to its type.

Property sets hold, as the name suggests, a set of properties grouped by a common theme. Each individual property has:
- a name
- an optional description
- a value, or number of values, of a given datatype
- a unit or the information of being unitless

The semantic meaning of each property is provided by its name. Properties, that are semantically declared within the scope of the IFC4 Reference View, are based on a property definition template that is published as an instrict part of the Model View Definition. Extensions to the property definitions can also be defined outside the property definition scope of the IFC4 Reference View, however the name prefix for property sets "Pset_" is restricted to properties defined within the original scope of IFC.

There are two ways to declare property templates:
- using the Property Set Definition PSD schema, an XML schema developed independent of the IFC specification,
- using the newly introduced IFC4 property set template and property template 

> NOTE The PSD Schema has been used since many earlier versions of the IFC standard and has a broad legancy. The newer property set template definitions are now part of the IFC schema and can therefore be embedded within an IFC data set directly. Both schemas can be mapped without information loss.


### 1.4.4 Object association
Beside using general property sets, the following model element information is handled specificly within IFC4:
- name and description of the model element as direct attributes
- predefined element type and user defined element type as direct attributes
- quantities as specific quantity sets
- classification as specific classification reference either to an external classification system, or embedding the classification within the IFC data set
- material as either single material, and material constituent sets assigning material information, or by material layer sets and material profile sets combining material information with dimensions.

> NOTE Material dimensions are layer thicknesses, or profile geometries for e.g. a column with an embedded steel profile and a concrete protection. Within the IFC4 Reference View, such material dimensions are used exclusively as alphanumeric information, and not as part of a dimension driven parametric shape representation.


### 1.4.5 Product shape
The first main objective of the IFC4 Reference View is to enable the exchange of highly accurate, not non-parametric, geometric representations of the model elements. Each model element is placed directly or indirectly within the project coordinate system, defining its own object coordinate system. The geometric representation items describing its shape are positioned within this object coordinate system.

In order to minimize the effort for receiving and interpreting the geometic representations by the receiving software systems, in terms of development effort, processing power and loading times, the complexity and variety of geometric models has been minimized for the IFC4 Reference View.

#### 1.4.5.1 Product placement

#### 1.4.5.2 Product geometric representation

In scope of geometric shape representations of physical and spatial elements is:
- tessellated geometry

It is the default geometric representation of all model elements, allowing for a surface model representation with an indicator for closed shells (and therefore true volumes). The tessellated representation offers a very efficient way of exchanging 3D shape date, both for data set sizes and for processing time. Optionally the face normals can be exchanged as well.

Since curved shapes would lead to very densely triangulated areas, the following swept solid based representations are also in scope of the IFC4 Reference View, balancing simplicity and compactness of representation:

- extruded solid geometry
- revolved solid geometry
- advanced swept solid geometry of circular cross sections

All other geometric models are out of scope of the IFC4 Reference View, in particular Boolean operations required for Constructive Solid Geometry CSG.

> NOTE: The IFC2x3 Coordination View included CSG capabilities, the IFC4 Reference View therefore imposes a more restricted geometric representation of model elements. The IFC4 Design Transfer View should be used, if more complex geometric representations are required by the workflow. In particular, if a dimension-driven parametric representation, used by the IFC4 standard case elements, is needed.

The geometric shape representation can either be directly assigned to a model element, or to its type. In case of type-based geometry, a fifth representation type is used at the model element:
- mapped representation

A mapped representation uses Cartesian transformation operations to place the type-based geometry within its  object coordinate system.

#### 1.4.5.3 Geometric presentation
Visual appearance is an important factor for the communication process using BIM data. The objective is not to support photo-realistic rendering of reference models, but to use color, basic rendering, and texture information to add visually accessible meaning to the model elements.
 
In scope of presentation capabilities for the appearance of model element shapes are:
- coloring, as single color or rendering per solid, or as one color per face
- texturing

The visually adaquate presentation of model elements is constraint by the shapre representation
- for tessellated geometry: color per face, texture per face
- for swept solid geometry: color and rendering information per solid, texture applied to solid using standard mapping


### 1.4.6 Object Composition

### 1.4.7 Object Assignment

### 1.4.8 Object Connectivity
