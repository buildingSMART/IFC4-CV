# IFC4 Coordination View project overview

The goal of this project is to specify the subset of the [new IFC4 release] (http://www.buildingsmart-tech.org/specifications/ifc-releases/ifc4-release/ifc4-release-summary) that supports coordination activities, also known as Coordination View. The work will be based on the [IFC2x3 CV] (http://www.buildingsmart-tech.org/certification/ifc-certification-2.0/ifc2x3-cv-v2.0-certification/ifc2x3-cv-v2.0-certification-summary) that is currently used by buildingSMART for software certification. Instead of developing another single IFC4 Coordination View, this project proposes to develop two (later three) correlated partial views:
* [IFC4 Reference View](/IFC4_Reference_View.md)
* [IFC4 Design Transfer View](/IFC4_DesignTransfer_View.md)
* [IFC Library View](/IFC4_Library_View.md) [illustrative, since not part of this project]


## Available documentation

### General information on scope
- [latest powerpoint overview] (https://github.com/BuildingSMART/IFC4-CV/blob/master/Scope/P2%20GeneralScopeIFC4CordinationView%2020140423.pdf)
  The general scope statement defines the requirements on the two successors of the Coordination View from the IFC exchange work flow perspective and from the expected user experience.

- [latest version of mindmap]  (https://github.com/BuildingSMART/IFC4-CV/blob/master/Scope/P2%20DetailedScopeIFC4CoordinationView%20V0.6.pdf)
  Overall mindmap showing the scope of the IFC Reference and IFC Design Transfer View based on the Model elements and Concept templates used and showing main IFC entities included.
 
### IFC4 Reference View (NEWS)

In order to achieve a broad engagement, a public review period is set up to start today and to end on Sept 30, 2014. All necessary information, the achieved improvements, the beta version specifications, the change logs and resolved issue lists, as well as the overall objective and scope definitions are published on the buildingSMART website.

- IFC4 Reference View - see [IFC4 RV at buildingsmart-tech.org] (http://www.buildingsmart-tech.org/specifications/ifc-view-definition/ifc4-reference-view)
- IFC4 Addendum 1 - see [IFC4 Add1 at buildingsmart-tech.org] (http://www.buildingsmart-tech.org/specifications/ifc-releases/ifc4-add1-release)

There you will also find a short introduction on how to join the review process, information on the issue database to be used, and how to join the new email exploder for all IFC4 related work in order to stay connected.



Documentation:
- Purpose, objective and scope, see [IFC4 Reference View Specification] (https://github.com/BuildingSMART/IFC4-CV/blob/master/IFC4_Reference_View.md)
 

### IFC4 Design Transfer View

- Overview, see [IFC4 Design Transfer View Specification] (https://github.com/BuildingSMART/IFC4-CV/blob/master/IFC4_DesignTransfer_View.md)


### IFC4 Library View [Illustrative]

- Overview, see [IFC4 Library View Specification] (https://github.com/BuildingSMART/IFC4-CV/blob/master/IFC4_Library_View.md)

 

## Additional explanation

**Purpose of the IFC4 Coordination View Successors**

The goal of these Model Views is to represent building design information that may be delivered across disciplines in design, construction, and operations. These Model Views are limited to physical building products and systems, and exclude all other lifecycle information (actors, controls, processes, resources). This model view may reference type definition information used by a building (e.g. common geometry for product models), but does not encapsulate product libraries – a separate Model View may be defined for that in the future (i.e. IFC4 Library View). Full connection information is within scope (element connections, ports, interference relationships), as is decomposition information (aggregation, voiding, filling).

Several Model Views are defined with increasing levels of design intent: Reference View, Design Transfer View, and Library View. These model views do not correlate with level of detail; higher or lower LOD may be indicated in any of these model views; rather they differ on the level of parametric information captured which impacts required capabilities of software applications. It is conceivable that these Model Views could be supported separately or combined within a single file (e.g. A: reference geometry only, B: design geometry only, C: parameters and formulas only, A+B, B+C, A+C, A+B+C) – such granularity would allow the widest range of portability while at the same time supporting optimized retrieval (e.g. a mobile application could request downloading a project limited to a particular subset).

Each of these model views will be explicitly defined in mvdXML format, which enables automation of implementations: if application software is designed to support IFC and mvdXML, then it can theoretically support any model view automatically. Automated filtering, translation, importing, exporting, validation, and user interface customization are possible.
 
