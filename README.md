IFC4 Coordination View
======================

The goal of this project is to specify the subset of the [new IFC4 release] (http://www.buildingsmart-tech.org/specifications/ifc-releases/ifc4-release/ifc4-release-summary) that supports  coordination activities, also known as Coordination View. The work will be based on the [IFC2x3 CV] (http://www.buildingsmart-tech.org/certification/ifc-certification-2.0/ifc2x3-cv-v2.0-certification/ifc2x3-cv-v2.0-certification-summary) that is currently used by buildingSMART for software certification. Two correlated partial views will be developed:
* Design handover view 
* Reference view


Purpose of the IFC4 Coordination Views

The goal of these model views is to represent building design information that may be delivered across disciplines in design, construction, and operations. These model views are limited to physical building products and systems, and exclude all other lifecycle information (actors, controls, processes, resources). This model view may reference type definition information used by a building (e.g. common geometry for product models), but does not encapsulate product libraries – a separate Model View may be defined for that in the future. Full connection information is within scope (element connections, ports, interference relationships), as is decomposition information (aggregation, voiding, filling).

Several model views are defined with increasing levels of design intent: Reference View, Design Handover View, and Parametric View. These model views do not correlate with level of detail; higher or lower LOD may be indicated in any of these model views; rather they differ on the level of parametric information captured which impacts required capabilities of software applications. It is conceivable that these model views could be supported separately or combined within a single file (e.g. A: reference geometry only, B: design geometry only, C: parameters and formulas only, A+B, B+C, A+C, A+B+C) – such granularity would allow the widest range of portability while at the same time supporting optimized retrieval (e.g. a mobile application could request downloading a project limited to a particular subset).

Each of these model views will be explicitly defined in mvdXML format, which enables automation of implementations: if application software is designed to support IFC and mvdXML, then it can theoretically support any model view automatically. Automated filtering, translation, importing, exporting, validation, and user interface customization are possible.
 
 
IFC4 Reference View

The overall goal of the Reference View is to provide building information that may be consumed by the widest array of software applications that do not require modifying geometry. Such applications enable viewing, estimating, building, operating, and other downstream analysis. The target scenario is an architect providing building design information to a contractor or facility manager. It is expected that the resulting geometry would reflect sufficient realism for viewing in software (dimensions, normals, colors, textures), but not of rendering quality for artistic presentations (lighting, shader effects, curve interpolation, rasterizing).

To support the widest array of consuming applications, the resulting schema should be as limited as possible for representing geometry in the interest of minimizing resources required of application developers. Such schema should also be as compact as possible to enable downstream use on mobile devices with limited network bandwidth. It is proposed that the resulting geometry is limited to triangles with normal vectors and texture coordinates (IfcTriangulatedFaceSet).

As the Reference View is new (there is no corresponding concept in the IFC2x3 Coordination View), there is no constraint for compatibility, and the resulting schema will leverage new triangulation definitions in IFC4 to support more efficient data transfer.
 

IFC4 Design Handover View

The overall goal of the Design Handover View is to provide building information with support for editing of interconnected elements. Such applications enable inserting, deleting, moving, and modifying physical building elements and spaces. The target scenario is an architect providing building design information to an engineer for a particular discipline, where geometric modifications may need to be made.

To enable such editing, higher-level design parameters must be preserved, and applications must generate downstream geometry consistently according to such parameters. The scope of parameters is limited to those that impact interconnected elements: for example, increasing window dimensions impacts composition of walls; moving walls impacts geometry of connected walls, adjoining spaces, coverings, and embedded elements; adjusting pipes or ducts may require resizing openings. The scope of parameters does NOT include those that only impact a specific element (e.g. stair tread dimensions) -- such scope is reserved for a Parametric Model View currently defined as illustrative. All geometry is supported in the Design Handover, including Constructive Solid Geometry (CSG) and new Non-Uniform Rational B-Spline (NURBS) geometry defined in IFC4 for precisely describing arbitrary curved surfaces.

As the Design Handover View is intended to be compatible with the IFC2x3 Coordination View, every effort will be made to retain such compatibility while supporting new IFC4 concepts where applicable that enhance editing capability (e.g. IfcMaterialProfileSet, IfcAdvancedBrep).
 

IFC4 Parametric View [Illustrative]

The overall goal of the Parametric View is to provide building information that may be fully edited by design applications independently of any specific parameters or formulas for calculating geometry.

To enable such editing, geometric attributes are bound to formulas based on higher-level parameters. While this model view provides examples of parameters at particular elements, it does not require specific parameters; rather the originating application may encode formulas used for generating the geometry and downstream applications may re-use such formulas for regenerating geometry. The IfcMetric and IfcAppliedValue entities [expanded in IFC4] are used for representing such formulas. Attributes may be bound to formulas based on arithmetic operations of other parameters and tables of available configurations. Elements may be decomposed into parts dynamically where the count and placement may vary according to formula. Moveable parts may also be described (e.g. drawer sliding, door opening). Such capabilities should fully support parametric behavior that can be described in existing design-related applications (e.g. Sketchup). Examples of usage include floor tiles (defining dimensions, texture, pattern, boundary, etc.), framed walls (stud type, stud spacing, plate type, axis path, etc.), junction boxes (number of gangs), concrete columns (rebar count, rebar cover, etc.), and virtually any product having multiple configurations.

The Parametric View is currently out-of-scope, but is described herein to better illustrate how the other model views relate and how they may fit into future roadmaps. 
 
