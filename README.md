LAWD
====

An ontology for Linked Ancient World Data

The goal of LAWD is to fill in the cracks between the data used and published by projects with a focus on the 
ancient world and the standard Linked Data vocablary schemes, like Dublin Core, the Open Annotation Collaboration, 
and CIDOC-CRM. LAWD will accomplishe this by defining just enough new classes and properties to permit the semantic 
modeling of things like manuscript collation, relating provenance to geography, and prosopography. 

### namespace: http://lawd.info/ontology/ 
### prefixes:
dc: http://purl.org/dc/elements/1.1

dct: http://purl.org/dc/terms/

crm: http://www.cidoc-crm.org/cidoc-crm/

geo: http://geovocab.org/spatial#


## Modeling written works:

### Classes

#### `ConceptualWork`
The idea of a work, which may have any number of written expressions (which may themselves have derivatives). 
Analogous to a Work in FRBR.  

#### `WrittenWork`
#### ≣ crm:E33_Linguistic_Object
##### subclasses: `AssembledWork`, `Edition`, `Translation`, `Hand`
A written work (whether extant or not) that is a version of a `ConceptualWork`. Subclasses are `AssembledWork`, 
`Edition`, `Translation`, and `Hand`. A `WrittenWork` may be part of another `WrittenWork` (e.g. a manuscript 
written in multiple hands), it may embody one or more `ConceptualWork`s (e.g. a codex comprised of several works), 
and it may have one or more `WrittenWork`s as a source (e.g. an edition or translation that makes use of 
several versions).

#### `Citation`
##### subclasses: `Siglum`
A `Citation` models a bibliographic reference in long or short form that may be used to represent the thing 
it references (like an entry in a bibliography, for example). When the cited work is a Non Information Resource, a
`Citation` may be used as the Information Resource analog for the cited work. A `Siglum` is a specialized citation
used in the context of critical apparatus that uses a symbol to refer to a source, such as a manuscript.

### Object Properties

#### `embodies` 
Domain: `WrittenWork`
Range: `ConceptualWork`

#### `dct:source`
used to indicate the source of a `WrittenWork` (which will be one or more `WrittenWork`s)

### Object Properties

#### `represents`
#### `representedBy`
These relate `Citation`s to `WrittenWork`s

## Modeling Persons and Names

### Classes
#### `Agent`
##### subclasses: `Person`, `Deity`, `Association`
An Agent is an abstract entity which has agency or is considered capable of acting in some way.

#### `Person`
#### ≣ crm:E21_Person

#### `Deity`

#### `CorporateBody`

#### `Name`
##### subclasses: `PersonalName`, `PlaceName`
An abstract name, which has one or more primary forms and any number of variant forms.

#### `PersonalName`
A name belonging to a `lawd:Person`

#### `PlaceName`
A name belonging to a `lawd:Place`

### Data Properties

#### `primaryForm`
Indicates the primary form of a `Name`

#### `variantForm`
Indicates a variant form of a `Name`

## Modeling Evidence

### Classes
#### `EvidentiaryItem`
##### subclasses: `
A superclass for types of evidence.

#### `Attestation`
An Attestation models a piece of evidence for something in a text (e.g. the mention of a person in a document). Typically it is the conjunction of a Citation and an entity like a name or person.

### Object Properties

#### `hasCitation`
Indicates a `Citation` that refers to the source for an `Attestation`

#### `hasAttestation`
Indicates an `Attestation` providing evidence for a `Name`, `Person`, etc.

## Modeling the relationship of artifacts to places

### Classes
#### Place
#### ≣ crm:E27_Site
#### ≣ geo:Feature

### Object Properties

#### `origin`
Range: `Place`

#### `foundAt`
Range: `Place`

## Modeling the relationship of artifacts to existing typologies


### Object Properties

#### ≣ crm:P2_has_type


## Modeling collation and critical apparatus:

### Classes

#### `CollationItem`
##### subclasses: `EditorialComment`, `Reference`
Models an alternate reading in a manuscript source, an editor's comment on a reading, or the observation that
a reading has a parallel elsewhere.








