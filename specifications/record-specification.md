# GEDCOM X Record

## Status

This document specifies a set of extensions to [GEDCOM X](http://www.gedcomx.org) for the
purpose of providing a mechanism to exchange field-based genealogical record data.

The current state of this document is as a DRAFT, and as such, the document
may be subject to changes, including backwards-incompatible changes, according to the
discussion and suggestions for improvement.

## Copyright Notice

Copyright 2011-2012 Intellectual Reserve, Inc.

## License

This document is distributed under a Creative Commons Attribution-ShareAlike license.
For details, see:

http://creativecommons.org/licenses/by-sa/3.0/

# 1. Introduction

GEDCOM X Record is a specification that defines extensions to the [core GEDCOM X specification set](https://github.com/FamilySearch/gedcomx/blob/master/specifications/) to exchange field-based genealogical record data.

## 1.1 Identifier, Version, and Dependencies

The identifier for this specification is:

`http://record.gedcomx.org/v1`

For convenience, GEDCOM X Record may be referred to as "GEDCOM X Record 1.0". This specification uses "GEDCOM X Record" internally.

This specification references the GEDCOM X XML specification identified
by [`http://gedcomx.org/xml/v1`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md).

This specification also references the GEDCOM X JSON specification identified
by [`http://gedcomx.org/json/v1`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md).

## 1.2 Notational Conventions

### 1.2.1 Keywords

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14,
[RFC2119](http://tools.ietf.org/html/rfc2119), as scoped to those conformance
targets.

# 2. Data Type Extensions

This section defines a set of extensions to the [GEDCOM X Conceptual Model](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md) and provides the representations of those data types in both XML and JSON as extensions to
[GEDCOM X JSON](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md) and
[GEDCOM X XML](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md).

## 2.1 The "Record" Data Type

todo:

### identifier

The identifier for the `Record` data type is:

`http://gedcomx.org/v1/Record`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | |

### extension

todo:

### 2.1.1 The "Record" XML Element

todo:

### 2.1.2 The "Record" JSON Member

todo:


## 2.2 The "Field" Data Type

todo:

### identifier

The identifier for the `Field` data type is:

`http://gedcomx.org/v1/Field`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | |

### 2.2.1 The "Field" XML Element

todo:

### 2.2.1 The "Field" JSON Element

todo:


## 2.3 The "FieldValue" Data Type

todo:

### identifier

The identifier for the `FieldValue` data type is:

`http://gedcomx.org/v1/FieldValue`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | |

### 2.3.1 The "FieldValue" XML Element

todo:

### 2.3.1 The "FieldValue" JSON Element

todo:


## 2.4 The "Collection" Data Type

todo:

### identifier

The identifier for the `Collection` data type is:

`http://gedcomx.org/v1/Collection`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | | 

### 2.4.1 The "Collection" XML Element

todo:

### 2.4.1 The "Collection" JSON Element

todo:


## 2.4 The "CollectionCoverage" Data Type

todo:

### identifier

The identifier for the `CollectionCoverage` data type is:

`http://gedcomx.org/v1/CollectionCoverage`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | |

### 2.4.1 The "CollectionCoverage" XML Element

todo:

### 2.4.1 The "CollectionCoverage" JSON Element

todo:


## 2.5 The "Facet" Data Type

todo:

### identifier

The identifier for the `Facet` data type is:

`http://gedcomx.org/v1/Facet`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | |

### 2.5.1 The "CollectionCoverage" XML Element

todo:

### 2.5.1 The "CollectionCoverage" JSON Element

todo:


## 2.6 The "FacetValue" Data Type

todo:

### identifier

The identifier for the `Facet` data type is:

`http://gedcomx.org/v1/Facet`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | |

### 2.6.1 The "FacetValue" XML Element

todo:

### 2.6.1 The "FacetValue" JSON Element

todo:


## 2.7 The "RecordDescriptor" Data Type

todo:

### identifier

The identifier for the `RecordDescriptor` data type is:

`http://gedcomx.org/v1/RecordDescriptor`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | | 

### 2.7.1 The "RecordDescriptor" XML Element

todo:

### 2.7.1 The "RecordDescriptor" JSON Element

todo:


## 2.8 The "FieldDescriptor" Data Type

todo:

### identifier

The identifier for the `FieldDescriptor` data type is:

`http://gedcomx.org/v1/FieldDescriptor`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
todo: | | | 

### 2.8.1 The "FieldDescriptor" XML Element

todo:

### 2.8.1 The "FieldDescriptor" JSON Element

todo:


