# Foreword

To be updated from [standard foreword boiler plate text] (http://www.buildingsmart-tech.org/ifc/IFC4/final/html/foreword.htm)

# Introduction

## Purpose

The overall goal of the IFC4 Library View is to provide building information that may be fully edited by design applications independently of any specific parameters or formulas for calculating geometry.

To enable such editing, geometric attributes are bound to formulas based on higher-level parameters. While this model view provides examples of parameters at particular elements, it does not require specific parameters; rather the originating application may encode formulas used for generating the geometry and downstream applications may re-use such formulas for regenerating geometry. The IfcMetric and IfcAppliedValue entities [expanded in IFC4] are used for representing such formulas. Attributes may be bound to formulas based on arithmetic operations of other parameters and tables of available configurations. Elements may be decomposed into parts dynamically where the count and placement may vary according to formula. Moveable parts may also be described (e.g. drawer sliding, door opening). Such capabilities should fully support parametric behavior that can be described in existing design-related applications (e.g. Sketchup). Examples of usage include floor tiles (defining dimensions, texture, pattern, boundary, etc.), framed walls (stud type, stud spacing, plate type, axis path, etc.), junction boxes (number of gangs), concrete columns (rebar count, rebar cover, etc.), and virtually any product having multiple configurations.

The Library View is currently out-of-scope, but is described herein to better illustrate how the other Model Views relate and how they may fit into future roadmaps. 
