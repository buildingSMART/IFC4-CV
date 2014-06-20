# Foreword

To be updated from [standard foreword boiler plate text] (http://www.buildingsmart-tech.org/ifc/IFC4/final/html/foreword.htm)

# Introduction

## Purpose

The overall goal of the Design Transfer View is to provide building information with support for editing of interconnected elements. Such applications enable inserting, deleting, moving, and modifying physical building elements and spaces. The target scenario is an architect providing building design information to an engineer for a particular discipline, where geometric modifications may need to be made.

To enable such editing, higher-level design parameters must be preserved, and applications must generate downstream geometry consistently according to such parameters. The scope of parameters is limited to those that impact interconnected elements: for example, increasing window dimensions impacts composition of walls; moving walls impacts geometry of connected walls, adjoining spaces, coverings, and embedded elements; adjusting pipes or ducts may require resizing openings. The scope of parameters does NOT include those that only impact a specific element (e.g. stair tread dimensions) -- such scope is reserved for a Library Model View currently defined as illustrative. All geometry is supported in the Design Transfer, including Constructive Solid Geometry (CSG) and new Non-Uniform Rational B-Spline (NURBS) geometry defined in IFC4 for precisely describing arbitrary curved surfaces.

## Objective

## Compatibility concerns

As the Design Transfer View is intended to be compatible with the IFC2x3 Coordination View, every effort will be made to retain such compatibility while supporting new IFC4 concepts where applicable that enhance editing capability (e.g. IfcMaterialProfileSet, IfcAdvancedBrep).
