<img align="right" height="200" width="330" src="./assets/img/logo-black.png">

# TUBES System Ontology

<br clear="left">
<br clear="left">

## Uses
The scope of the TUBES System Ontology is to explicitly define interconnected building service system in the AECO industry, their hierarchical subdivisions, structural and functional aspects, and links to spatial entities. As such, TSO supports the effort to represent linkable information in a future semantic web of building data. It has a strong alignment to other ontologies within the W3C community.

A persistent URI namespace for the TUBES System Ontology (tso) will be provided by [W3ID](https://w3id.org) at <https://w3id.org/tso>.

## Documentation
The latest version of TSO is provided in <a href="https://raw.githubusercontent.com/RWTH-E3D/tso/master/tubes.ttl" download="tubes.ttl"> Turtle</a>, <a href="https://raw.githubusercontent.com/RWTH-E3D/tso/master/tubes.rdf" download="tubes.rdf"> RDF/XML</a> and <a href="https://raw.githubusercontent.com/RWTH-E3D/tso/master/tubes.json" download="tubes.json">JSON-LD</a> format. Extensive [documentation](./documentation/) is also available.

## Concept
The three main classes of the TUBES System Ontology are *tso:System*, *tso:Zone* and *tso:State*.  A *tso:Zone* is defined as a part of the physical world or a virtual world that is inherently both located in this world and has a 3D spatial extent. It has a strong alignment to the zone concept of the Building Topology Ontology (BOT). The object properties *tso:servesZone* and *tso:servesSystem* define relationships linking states of systems and zones to describe that a zone is served by a system, respectively a system serves a zone. *tso:locatedIn* and *tso:contains* define relationships to describe that a system is located in a zone, respectively a zone contains a system. *tso:State* defines the internal condition of a (planned) system. To link a state to a system, respectively a system to a state, the inverse properties *tso:stateOf* and *tso:hasState* are defined. A *tso:System* is a model of a whole which is isolated from the world or a supersystem, which may consists of interconnected components or subsystems and has links between attributes such as inputs, outputs and states. Within this definition there are three concepts with are further detailed in the following.

<p align="center">
  <img src="./assets/img/TSO_v3_HauptK_v3.pdf">
</p>

#### Hierarchical Concept
The hierarchical concept describes a system as a model of a whole which is isolated from the world or a supersystem. To represent the these aspects of building service systems the four subclasses *tso:IntegratedSystem*, *tso:FunctionalSystem*, *tso:TechnicalSystem* and *tso:Component* of *tso:System* are given in TSO. In the following the term “system” is used to describe all of them. *tso:IntegratedSystem* represents the coupling of different functional systems with independent inherent functions which are interconnected. *tso:FunctionalSystem* denotes a system which is defined by its overall inherent function. Typical examples would be *tso:HeatingSystem*, *tso:CoolingSystem* or *tso:VentilationSystem*. *tso:TechnicalSystem* is defined as a system with a coherent technical solution with which the inherent function (of the upper functional system) is fulfilled. Existing subclasses contain *tso:DistributionSystem* and *tso:ConversionSystem*. *tso:Component* denotes a system, for which the boundary that isolates it from the environment is defined by the manufacturer in terms of the product. Therefore, an air handling unit as well as the included rotary wheel heat exchanger or sensor could be instances of *tso:Component*. To classify components, TSO is aligned with ifcOWL. *tso:subSystemOf* defines a relationship linking a system to its supersystem. *tso:hasSubSystem* is defined as the inverse of *tso:subSystemOf* and describes a relationship linking a system to its subsystem. Both object properties have their range and domain defined as *tso:System*.

<p align="center">
  <img src="./assets/img/TSO_v3_HK_v3.pdf">
</p>

#### Structural Concept
The structural concept describes a system as a model of a whole which may consists of interconnected components or subsystems. To represent the topological aspects of building service systems and answer CQ2, TSO builds upon the concepts *tso:ConnectionPoint* and *tso:Connection* proposed in SEAS and extends these by the subclasses *tso:InnerConnection* and *tso:OuterConnection* to differentiate between the connections inside a system and between different systems. *tso:ConnectionPoint* refers to an inlet or outlet of a system for a connection to other systems or within the same system, where some kind of matter, energy or data can be transmitted. Using these concepts and the object properties which define the relationships between them, the symmetric object property *tso:connects* can be qualified to describe that two systems are connected. These concepts can be implemented to represent the system topology on every hierarchy level introduced in the last section.

<p align="center">
  <img src="./assets/img/TSO_v3_SK_v4.pdf">
</p>

#### Functional Concept
The functional concept describes a system as a model of a whole which has links between attributes such as inputs, outputs and states. To represent the functional aspects of building service systems TSO relies heavily on the concept of states. A *tso:State* is defined as the internal condition of a (planned) system. It can be used to add a level of abstraction to represent systems where the function, and therefore the flow of matter, energy or data, can change due to given states. Hence, a system can have multi- ple potential states assigned via the *tso:hasState* object property. To represent “what” is exchanged between different systems or inside a certain system, the classes *tso:Matter*, *tso:Energy* and *tso:Data* as well as multiple subclasses are defined. These classes can be linked via *tso:hasInput* and *tso:hasOutput* to the states of different systems. Based on these concepts the inverse object properties *tso:supplies* and *tso:suppliedBy*, which link the states directly, can be inferred, as well as their subproperties to denote what is supplied. To represent the flow inside a system, the classes *tso:Matter*, *tso:Energy* and *tso:Data* can be connected to the given state by using the *tso:hasInnerExchange* object property. To qualify the exchange the considered matter, energy or data can be linked to a *tso:Connection* via *tso:transmitsThrough* or to the *tso:ConnectionPoints* via *tso:transmitsFrom* and *tso:transmitsTo*.

<p align="center">
  <img src="./assets/img/TSO_v3_FK_v3.pdf">
</p>

#### Alignments
Within the W3C linked building data ecosystem several alignments are proposed. Currently, these are available:

## Examples
Examples for the use of TSO are provided for an application example of an active cooled beam, the [DigitalHub](https://github.com/RWTH-E3D/DigitalHub) project and CUBE project.

- [ACB v0.3.0](./examples/acb-example.ttl)
- [DigitalHub v0.3.0](./examples/digitalhub.ttl)
- [CUBE v0.3.0](./examples/CUBE.ttl)

## Contacts

* Nicolas Pauen <pauen@e3d.rwth-aachen.de>
* Dominik Schlütter <schluetter@e3d.rwth-aachen.de>
