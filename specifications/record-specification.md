# GEDCOM X Record

## Status

This document specifies a set of extensions to [GEDCOM X](http://www.gedcomx.org) for the
purpose of providing a mechanism to exchange field-based genealogical record data.

The current state of this document is as a DRAFT, and as such, the document
may be subject to changes, including backwards-incompatible changes, according to the
discussion and suggestions for improvement.

## Copyright Notice

Copyright Intellectual Reserve, Inc.

## License

This document is distributed under a Creative Commons Attribution-ShareAlike license.
For details, see:

http://creativecommons.org/licenses/by-sa/3.0/

<a name="intro"/>

# 1. Introduction

GEDCOM X Record Extensions is a specification that defines extensions to the
[core GEDCOM X specification set](https://github.com/FamilySearch/gedcomx/blob/master/specifications/)
to exchange data specific to genealogical records, including field-based record extraction.

## Table Of Contents

* [1. Introduction](#intro)
  * [1.1 Identifier, Version and Dependencies](#id-and-version)
  * [1.2 Notational Conventions](#notational-conventions)
    * [1.2.1 Keywords](#keywords)
    * [1.2.2 Compliance](#compliance)
    * [1.2.3 Namespace Prefixes](#namespace-prefixes)
* [2. Data Type Extensions](#data-type-extensions)
  * [2.1 The "Collection" Data Type](#collection)
    * [2.1.1 The "Collection" XML Type and Element](#collection-type-element)
    * [2.1.2 The "Collection" JSON Type and Member](#collection-type-member)
  * [2.2 The "CollectionContent" Data Type](#collection-content)
    * [2.2.1 The "CollectionContent" XML Type](#collection-content-type)
    * [2.2.2 The "CollectionContent" JSON Type](#collection-content-json-type)
  * [2.3 The "Field" Data Type](#field)
    * [2.3.1 The "Field" XML Type and Element](#field-xml-type-element)
    * [2.3.2 The "Field" JSON Type and Element](#field-json-type-element)
  * [2.4 The "FieldValue" Data Type](#field-value-data-type)
    * [2.4.1 Known Field Value Types](#known-field-value-types)
    * [2.4.2 Known Field Value Data Types](#known-field-value-data-types)
    * [2.4.3 The "FieldValue" XML Type](#field-value-xml-type)
    * [2.4.4 The "FieldValue" JSON Type](#field-value-json-type)
  * [2.5 The "RecordDescriptor" Data Type](#record-descriptor)
    * [2.5.1 The "RecordDescriptor" XML Type and Element](#record-descriptor-xml-type-element)
    * [2.5.2 The "RecordDescriptor" JSON Type and Member](#record-descriptor-json-type)
  * [2.6 The "FieldDescriptor" Data Type](#field-descriptor)
    * [2.6.1 The "FieldDescriptor" XML Type](#field-descriptor-xml-type)
    * [2.6.2 The "FieldDescriptor" JSON Type](#field-descriptor-json-type)
  * [2.7 The "FieldValueDescriptor" Data Type](#field-value-descriptor)
    * [2.7.1 The "FieldValueDescriptor" XML Type](#field-value-descriptor-type)
    * [2.7.2 The "FieldValueDescriptor" JSON Type](#field-value-descriptor-type)
* [3. Property Extensions](#property-extensions)
  * [3.1 Extensions to the "Fact" Data Type](#extensions-fact-data-type)
    * [3.1.1 "Fact" XML Type Extensions](#fact-xml-type-extensions)
    * [3.1.2 "Fact" JSON Type Extensions](#fact-json-type-extensions)
  * [3.2 Extensions to the "Person" Data Type](#extensions-person-data-type)
    * [3.2.1 "Person" XML Type Extensions](#person-xml-type-extensions)
    * [3.2.2 "Person" JSON Type Extensions](#person-json-type-extensions)
  * [3.3 Extensions to the "SourceDescription" Data Type](#extensions-source-data-type)
    * [3.3.1 "SourceDescription" XML Type Extensions](#source-xml-type-extensions)
    * [3.3.2 "SourceDescription" JSON Type Extensions](#source-json-type-extensions)
  * [3.4 Extensions to the "SourceReference" Data Type](#extensions-source-reference-data-type)
    * [3.4.1 "SourceReference" XML Type Extensions](#source-reference-xml-type-extensions)
    * [3.4.2 "SourceReference" JSON Type Extensions](#source-reference-json-type-extensions)
  * [3.5 Extensions to the "Coverage" Data Type](#extensions-coverage-data-type)
    * [3.5.1 "Coverage" XML Type Extensions](#coverage-xml-type-extensions)
    * [3.5.2 "Coverage" JSON Type Extensions](#coverage-json-type-extensions)
* [4. The GEDCOM X XML Record Set](#recordset)
  * [4.1 GEDCOM X XML Record Set Element QName](#gedcomx-xml-element-qname)
  * [4.2 GEDCOM X Record Set Element Data Type](#gedcomx-element-data-type)

<a name="id-and-version"/>

## 1.1 Identifier, Version, and Dependencies

The identifier for this specification is:

`http://gedcomx.org/records/v1`

For convenience, GEDCOM X Record Extensions may be referred to as "GEDCOM X Record Extensions 1.0".
This specification uses "GEDCOM X Record Extensions" internally.

This specification references the GEDCOM X Conceptual Model specification identified
by [`http://gedcomx.org/conceptual-model/v1`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md).

This specification references the GEDCOM X XML specification identified
by [`http://gedcomx.org/xml/v1`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md).

This specification references the GEDCOM X JSON specification identified
by [`http://gedcomx.org/json/v1`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md).

This specification refers to the GEDCOM X Field Types specification identified
by [`http://gedcomx.org/field-types/v1`](https://github.com/FamilySearch/gedcomx-record/blob/master/specifications/field-types-specification.md)
to recommend field types to be used.

<a name="notational-conventions"/>

## 1.2 Notational Conventions

<a name="keywords"/>

### 1.2.1 Keywords

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14,
[RFC2119](http://tools.ietf.org/html/rfc2119), as scoped to those conformance
targets.

<a name="compliance"/>

## 1.2.2 Compliance

An implementation of the GEDCOM X Record Extensions is "non-compliant" if it fails to satisfy
one or more of the MUST or REQUIRED level requirements. An implementation that satisfies all of
the  MUST or REQUIRED and all of the SHOULD level requirements is said to be "unconditionally
compliant"; and implementation that satisfies all of the MUST level requirements but not all of the
SHOULD level requirements is said to be "conditionally compliant".

<a name="namespace-prefixes"/>

### 1.2.3 Namespace Prefixes

This specification uses the same namespace prefix conventions that are used by the
[GEDCOM X XML](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md)
specification.

<a name="data-type-extensions"/>

# 2. Data Type Extensions

This section defines a set of extensions to the [GEDCOM X Conceptual Model](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md)
and provides the representations of those data types in both XML and JSON as extensions to
[GEDCOM X JSON](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md) and
[GEDCOM X XML](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md).

<a name="collection"/>

## 2.1 The "Collection" Data Type

The `Collection` data type defines a collection of genealogical data.

### identifier

The identifier for the `Collection` data type is:

`http://gedcomx.org/v1/Collection`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
id | A local identifier for the collection. | string | OPTIONAL.  The id is to be used as a "fragment identifier" as defined by [RFC 3986, Section 3.5](http://tools.ietf.org/html/rfc3986#section-3.5). As such, the constraints of the id are provided in the definition of the media type (e.g. XML, JSON) of the data structure.
lang | The locale identifier for the collection. | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag | OPTIONAL. If not provided, the locale is determined per [Internationalization Considerations](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#il8n).
content | Information about the content of the collection. | List of [`http://gedcomx.org/v1/CollectionContent`](#collection-content). Order is preserved. | OPTIONAL.
title | A title for the collection. | string | OPTIONAL.
size | An indication of the size of the collection. The units of size are left unspecified. | integer | OPTIONAL.
attribution | The attribution of this collection. | [`http://gedcomx.org/Attribution`](#attribution) | OPTIONAL. If not provided, the attribution of the containing data set (e.g. file) of the source description is assumed.

<a name="collection-type-element"/>

### 2.1.1 The "Collection" XML Type and Element

The `gx:Collection` XML type is used to (de)serialize the `http://gedcomx.org/v1/Collection`
data type. The `gx:collection` XML element is used to provide instances of the `gx:Collection` XML type.
The `gx:collection` element SHOULD be expected as an extension element to the
[`Gedcomx` XML Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#gedcomx-type).

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
id | The identifier for the XML element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#fragment-ids). | id (attribute) | xsd:string
lang | The locale identifier for the collection. | xml:lang (attribute) | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag
content | Information about the content of the collection. | gx:content | [`gx:CollectionContent`](#collection-content).
title | A title for the collection. | gx:title | xsd:string
size | An indication of the size of the collection. | gx:size | xsd:int
attribution | The attribution of this data set. | gx:attribution | [`gx:Attribution`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#attribution)

### examples

```xml
<gx:collection id="local_id" lang="en">
  <gx:content>
    ...
  </gx:content>
  ...
  <gx:title>...</gx:title>
  <gx:size>...</gx:size>
  <gx:attribution>
    ...
  </gx:attribution>

  ...

  <!-- possibility of extension elements -->

</gx:collection>
```

<a name="collection-type-member"/>

### 2.1.2 The "Collection" JSON Type and Member

The `Collection` JSON type is used to (de)serialize the `http://gedcomx.org/v1/Collection`
data type. The `collections` member is used to provide instances of the `Collection` JSON type.
The `collections` member SHOULD be expected as an extension to the
[`Gedcomx` JSON Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#gedcomx-type).

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
id | The identifier for the collection. The id attribute MUST conform to the constraints defined in [GEDCOM X JSON, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#fragment-ids). | id | string
lang | The locale identifier for the collection. | lang | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag
content | Information about the content of the collection. | content | array of [`CollectionContent`](#collection-content).
title | A title for the collection. | title | string
size | An indication of the size of the collection. | size | number
attribution | The attribution of this data set. | attribution | [`Attribution`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#attribution)

### examples

```json
"collections" : [ {
  "id" : "...",
  "lang" : "...",
  "content" : [ { ... } , { ... } ],
  "title" : "...",
  "size" : ...,
  "attribution" : { ... },

  ...possibility of extension elements...

}
]
```

<a name="collection-content"/>

## 2.2 The "CollectionContent" Data Type

The `CollectionContent` data type provides information about the contents of a collection.

### identifier

The identifier for the `CollectionContent` data type is:

`http://gedcomx.org/v1/CollectionContent`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
resourceType | Enumerated value identifying the type of resource in the collection. | [Enumerated Value](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#enumerated-value) | REQUIRED. MUST identify a resource type, and use of a [known resource type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#known-resource-types) is RECOMMENDED.
count | The count of resources of the specified `resourceType` in the collection. | integer | OPTIONAL.
completeness | An indication of how "complete" is the collection of resources of the specified `resourceType`. A value of "1.0" implies that all resources of the specified `resourceType` are accounted for by the collection.  | double | OPTIONAL. If provided, MUST be a number between 0 and 1.

<a name="collection-content-type"/>

### 2.2.1 The "CollectionContent" XML Type

The `gx:CollectionContent` XML type is used to (de)serialize the `http://gedcomx.org/v1/CollectionContent`
data type.

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
resourceType | URI identifying the type of resource being described. | gx:resourceType | [anyURI](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)
count | The count of resources of the specified `resourceType` in the collection. | gx:count | xsd:int
completeness | An indication of how "complete" is the collection of resources of the specified `resourceType`. | gx:completeness | xsd:double

### examples

```xml
<...>
  <gx:resourceType>...</gx:resourceType>
  <gx:count>...</gx:count>
  <gx:completeness>...</gx:completeness>

  <!-- possibility of extension elements -->

</...>
```

<a name="collection-content-json-type"/>

### 2.2.2 The "CollectionContent" JSON Type

The `CollectionContent` JSON type is used to (de)serialize the `http://gedcomx.org/v1/CollectionContent`
data type.

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
resourceType | URI identifying the type of resource being described. | resourceType | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)
count | The count of resources of the specified `resourceType` in the collection. | count | number
completeness | An indication of how "complete" is the collection of resources of the specified `resourceType`. | completeness | number

### examples

```json
{
  "resourceType" : "...",
  "count" : ...,
  "completeness" : ...,

  ...possibility of extension elements...

}
```

<a name="field"/>

## 2.3 The "Field" Data Type

The `Field` data type provides information about the fields of a record from which genealogical data is extracted.
Fields are bounded regions of a record. A rectangle of a digital image is an example of a field. Tools that enable
data extraction (a.k.a. "indexing") define fields to aid a user in the extraction process. Fields may have multiple
values that capture both the "original" text as stated in the field as well as "interpreted" text that captures
the way the original value was interpreted, either by a user or by an automated system. A field may also provide a
"type" that indicates the type of information what is extracted (e.g. name, age, birth, etc.).

Instances of `Field` can be reasonably expected as extension elements to any GEDCOM X data type, especially on
person and relationship data. For example, an instance of `Field` may be found as an extension element on the `Gender`
of a person, the birth `Fact` of a person, the marriage `Fact` of a relationship, etc.

### identifier

The identifier for the `Field` data type is:

`http://gedcomx.org/v1/Field`

### extension

This data type extends the following data type:

`http://gedcomx.org/v1/Conclusion`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
id | A local identifier for the field. | string | OPTIONAL.  The id is to be used as a "fragment identifier" as defined by [RFC 3986, Section 3.5](http://tools.ietf.org/html/rfc3986#section-3.5). As such, the constraints of the id are provided in the definition of the media type (e.g. XML, JSON) of the data structure.
type | Enumerated value identifying the type of the field. | [Enumerated Value](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#enumerated-value) | OPTIONAL. If provided, MUST identify a field type, and use of a [known field type](https://github.com/FamilySearch/gedcomx-record/blob/master/specifications/field-types-specification.md) is RECOMMENDED.
values | The values of the data extracted from the field. | List of [`http://gedcomx.org/v1/FieldValue`](#field-value) | OPTIONAL

<a name="field-xml-type-element"/>

### 2.3.1 The "Field" XML Type and Element

The `gx:Field` XML type is used to (de)serialize the `http://gedcomx.org/v1/Field` data type.
The `gx:field` XML element is used to provide instances of the `gx:Field` XML type as extension elements.

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
id | The identifier for the XML element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#fragment-ids). | id (attribute) | xsd:string
type | URI identifying the type of field. | type (attribute) | [anyURI](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)
values | The values of the data extracted from the field. | gx:value | [`gx:FieldValue`](#field-value).

### examples

```xml
<gx:field id="..." type="...">
  <gx:value>
    ...
  </gx:value>
  ...

  <!-- possibility of extension elements -->

</gx:field>
```

<a name="field-json-type-element"/>

### 2.3.2 The "Field" JSON Type and Element

The `Field` JSON type is used to (de)serialize the `http://gedcomx.org/v1/Field` data type.
The `fields` JSON member is used to provide instances of the `Field` JSON type as extension elements.

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
id | The identifier for the field. The id attribute MUST conform to the constraints defined in [GEDCOM X JSON, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#fragment-ids). | id | string
type | URI identifying the type of field. | type | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)
values | The values of the data extracted from the field. | values | array of [`FieldValue`](#field-value).

### examples

```json
"fields" : [ {
  "id" : "...",
  "type" : "...",
  "values" : [ { ... } , { ... } ],

  ...possibility of extension elements...
}
]
```

<a name="field-value-data-type"/>

## 2.4 The "FieldValue" Data Type

The `FieldValue` data type provides information about the value of a field.

### identifier

The identifier for the `FieldValue` data type is:

`http://gedcomx.org/v1/FieldValue`

### extension

This data type extends the following data type:

`http://gedcomx.org/v1/Conclusion`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
type | Enumerated value identifying the type of the field value. | [Enumerated Value](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#enumerated-value) | OPTIONAL. If provided, MUST identify a field value type, and use of a [known field value type](#known-field-value-types) is RECOMMENDED.
labelId | A local id for the label of the field value. | string| OPTIONAL.
text | The text of the field value. | string | OPTIONAL.
datatype | Enumerated value identifying the data type of the text of the field value. | [Enumerated Value](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#enumerated-value) | OPTIONAL. If provided, MUST identify a data type, and use of a [known field value data type](#known-field-value-data-types) is RECOMMENDED.
resource | Reference to the resource that is the value. For example, if the value of a field is the male gender, the resource would be `http://gedcomx.org/Male`. | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#uri) | OPTIONAL.

<a name="known-field-value-types"/>

### 2.4.1 Known Field Value Types

The following field value types are defined by GEDCOM X:

URI | description
----|------------
`http://gedcomx.org/Original`| The field value carries the original value of the field; the verbatim text as stated on the record.
`http://gedcomx.org/Interpreted`| The field value carries an interpretation of the value of the field.

<a name="known-field-value-data-types"/>

### 2.4.2 Known Field Value Data Types

The following field value data types are defined by GEDCOM X:

URI | description
----|------------
`http://www.w3.org/2001/XMLSchema#boolean`| The text of the field value is to be interpreted as a boolean.
`http://www.w3.org/2001/XMLSchema#int`| The text of the field value is to be interpreted as an integer.
`http://www.w3.org/2001/XMLSchema#dateTime`| The text of the field value is to be interpreted as a date.

<a name="field-value-xml-type"/>

### 2.4.3 The "FieldValue" XML Type

The `gx:FieldValue` XML type is used to (de)serialize the `http://gedcomx.org/v1/FieldValue`
data type.

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
type | Enumerated value identifying the type of the field value. | type (attribute) | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)
labelId | A local id for the label of the field value. | labelId (attribute) | xsd:string
text | The text of the field value. | gx:text | xsd:string
datatype | Identifier for the data type of the text of the field value. | datatype (attribute) | [anyURI](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)
resource | Reference to the resource that is the value. | resource (attribute) | [anyURI](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)

### examples

```xml
<... type="..." datatype="..." resource="..." labelId="...">

  <!-- ...the members of [gx:Conclusion](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#conclusion)... -->

  <gx:text>...</gx:text>

  <!-- possibility of extension elements -->

</...>
```

<a name="field-value-json-type"/>

### 2.4.4 The "FieldValue" JSON Type

The `FieldValue` JSON type is used to (de)serialize the `http://gedcomx.org/v1/FieldValue`
data type.

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
type | Enumerated value identifying the type of the field value. | type | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)
labelId | A local id for the label of the field value. | labelId | string
text | The text of the field value. | text | string
datatype | Identifier for the data type of the text of the field value. | datatype | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)
resource | Reference to the resource that is the value. | resource (attribute) | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)

### examples

```json
{
  ...the members of [Conclusion](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#conclusion)...,

  "type" : "...",
  "labelId" : "...",
  "text" : "...",
  "datatype" : "...",
  "resource" : "...",

  ...possibility of extension elements...

}
```

<a name="record-descriptor"/>

## 2.5 The "RecordDescriptor" Data Type

The `RecordDescriptor` data type provides metadata about the structure and layout of a record, as
well as the expected data to be extracted from a record.

### identifier

The identifier for the `RecordDescriptor` data type is:

`http://gedcomx.org/v1/RecordDescriptor`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
id | A local identifier for the record descriptor. | string | OPTIONAL.  The id is to be used as a "fragment identifier" as defined by [RFC 3986, Section 3.5](http://tools.ietf.org/html/rfc3986#section-3.5). As such, the constraints of the id are provided in the definition of the media type (e.g. XML, JSON) of the data structure.
lang | The locale identifier for the record descriptor. | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag | OPTIONAL. If not provided, the locale is determined per [Internationalization Considerations](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#il8n).
fields | The descriptors for the fields of a record. | List of [`http://gedcomx.org/v1/FieldDescriptor`](#field-descriptor). Order is preserved. | OPTIONAL.

<a name="record-descriptor-xml-type-element"/>

### 2.5.1 The "RecordDescriptor" XML Type and Element

The `gx:RecordDescriptor` XML type is used to (de)serialize the `http://gedcomx.org/v1/RecordDescriptor`
data type. The `gx:recordDescriptor` XML element is used to provide instances of the `gx:RecordDescriptor` XML type.
The `gx:recordDescriptor` element SHOULD be expected as an extension element to the
[`Gedcomx` XML Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#gedcomx-type).

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
id | The identifier for the XML element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#fragment-ids). | id (attribute) | xsd:string
lang | The locale identifier for the record descriptor. | xml:lang (attribute) | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag
fields | The descriptors for the fields of a record. | gx:field | [`gx:FieldDescriptor`](#field-descriptor).

### examples

```xml
<gx:recordDescriptor id="local_id" lang="en">
  <gx:field>
    ...
  </gx:field>
  ...

  <!-- possibility of extension elements -->

</gx:recordDescriptor>
```

<a name="record-descriptor-json-type"/>

### 2.5.2 The "RecordDescriptor" JSON Type and Member

The `RecordDescriptor` JSON type is used to (de)serialize the `http://gedcomx.org/v1/RecordDescriptor`
data type. The `recordDescriptors` member is used to provide instances of the `RecordDescriptor` JSON type.
The `recordDescriptors` member SHOULD be expected as an extension to the
[`Gedcomx` JSON Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#gedcomx-type).

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
id | The identifier for the record descriptor. The id attribute MUST conform to the constraints defined in [GEDCOM X JSON, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#fragment-ids). | id | string
lang | The locale identifier for the record descriptor. | lang | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag
fields | The descriptors for the fields of a record. | fields | [`FieldDescriptor`](#field-descriptor).

### examples

```json
"fields" : [ {
  "id" : "...",
  "lang" : "...",
  "fields" : [ { ... } , { ... } ],

  ...possibility of extension elements...

}
]
```

<a name="field-descriptor"/>

## 2.6 The "FieldDescriptor" Data Type

The `FieldDescriptor` data type provides metadata about the structure and layout of a field, as
well as the expected data to be extracted from a field.

### identifier

The identifier for the `FieldDescriptor` data type is:

`http://gedcomx.org/v1/FieldDescriptor`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
id | A local identifier for the field descriptor. | string | OPTIONAL.  The id is to be used as a "fragment identifier" as defined by [RFC 3986, Section 3.5](http://tools.ietf.org/html/rfc3986#section-3.5). As such, the constraints of the id are provided in the definition of the media type (e.g. XML, JSON) of the data structure.
originalLabel | The text of the label for the field as originally stated on the record | string | OPTIONAL.
descriptions | The human-readable descriptions for the fields. | List of [`http://gedcomx.org/TextValue`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#text-value). Order is preserved. | OPTIONAL. If more than one description is provided, descriptions are assumed to be given in order of preference, with the most preferred description in the first position in the list.
values | The descriptors for the field values of the field. | List of [`http://gedcomx.org/v1/FieldValueDescriptor`](#field-value-descriptor). Order is preserved. | OPTIONAL.

<a name="field-descriptor-xml-type"/>

### 2.6.1 The "FieldDescriptor" XML Type

The `gx:FieldDescriptor` XML type is used to (de)serialize the `http://gedcomx.org/v1/FieldDescriptor`
data type.

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
id | The identifier for the XML element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#fragment-ids). | id (attribute) | xsd:string
originalLabel | The text of the label for the field as originally stated on the record | gx:originalLabel | xsd:string
descriptions | The human-readable descriptions for the fields. | gx:description | [`gx:TextValue`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#text-value)
values | The descriptors for the field values of the field. | gx:value | [`gx:FieldValueDescriptor`](#field-value-descriptor)

### examples

```xml
<... id="local_id">
  <gx:originalLabel>...</gx:originalLabel>
  <gx:description>
    ...
  </gx:description>
  ...
  <gx:value>
    ...
  </gx:value>
  ...

  <!-- possibility of extension elements -->

</...>
```

<a name="field-descriptor-json-type"/>

### 2.6.2 The "FieldDescriptor" JSON Type

The `FieldDescriptor` JSON type is used to (de)serialize the `http://gedcomx.org/v1/FieldDescriptor`
data type.

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
id | The identifier for the field descriptor. The id attribute MUST conform to the constraints defined in [GEDCOM X JSON, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#fragment-ids). | id | string
originalLabel | The text of the label for the field as originally stated on the record | originalLabel | string
descriptions | The human-readable descriptions for the fields. | descriptions | [`TextValue`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#text-value)
values | The descriptors for the field values of the field. | values | [`FieldValueDescriptor`](#field-value-descriptor)

### examples

```json
{
  "id" : "...",
  "originalLabel" : "...",
  "descriptions" : [ { ... } , { ... } ],
  "values" : [ { ... } , { ... } ],

  ...possibility of extension elements...

}
```

<a name="field-value-descriptor"/>

## 2.7 The "FieldValueDescriptor" Data Type

The `FieldValueDescriptor` data type provides metadata about the structure and layout of a field, as
well as the expected data to be extracted from a field.

### identifier

The identifier for the `FieldValueDescriptor` data type is:

`http://gedcomx.org/v1/FieldValueDescriptor`

### properties

name  | description | data type | constraints
------|-------------|-----------|------------
id | A local identifier for the field value descriptor. | string | OPTIONAL.  The id is to be used as a "fragment identifier" as defined by [RFC 3986, Section 3.5](http://tools.ietf.org/html/rfc3986#section-3.5). As such, the constraints of the id are provided in the definition of the media type (e.g. XML, JSON) of the data structure.
type | Enumerated value identifying the type of the field value. | [Enumerated Value](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#enumerated-value) | OPTIONAL. If provided, MUST identify a field value type, and use of a [known field value type](#known-field-value-types) is RECOMMENDED.
labelId | The id for the label of this field value. Field values can be associated with their descriptor by comparing the value of the `lableId`. | string | OPTIONAL.
optional | Whether the field value was considered optional on the record. Used as a hint to whether the field value should be displayed even if the value is empty. | boolean | OPTIONAL
labels | The human-readable labels for the field values. | List of [`http://gedcomx.org/TextValue`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#text-value). Order is preserved. | OPTIONAL. If more than one display label is provided, display labels are assumed to be given in order of preference, with the most preferred display label in the first position in the list.
displaySortKey | A sort key for sorting this field value relative to other field values according to how they should be displayed for viewing. | string | OPTIONAL
entrySortKey | A sort key for sorting this field value relative to other field values according to how they should be entered for editing. | string | OPTIONAL
entryRequired | Whether some kind of entry is required when entering data for editing. | boolean | OPTIONAL
editable | Whether the field value is editable. Some field values might be composed from other field values or otherwise calculated by the system. | boolean | OPTIONAL
parentLabelId | The id of the label for the "parent" field value. For example, the parent field value of a "given name" field value might be the "name" field value. | string | OPTIONAL

<a name="field-value-descriptor-type"/>

### 2.7.1 The "FieldValueDescriptor" XML Type

The `gx:FieldValueDescriptor` XML type is used to (de)serialize the `http://gedcomx.org/v1/FieldValueDescriptor`
data type.

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
id | The identifier for the XML element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#fragment-ids). | id (attribute) | xsd:string
type | Enumerated value identifying the type of the field value. | type (attribute) | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)
labelId | The id for the label of this field value. | labelId (attribute) | xsd:string
optional | Whether the field value was considered optional on the record. | optional (attribute) | xsd:boolean
labels | The human-readable labels for the field values. | gx:label | [`gx:TextValue`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#text-value)
displaySortKey | A sort key for sorting this field value relative to other field values according to how they should be displayed for viewing. | displaySortKey (attribute) | xsd:string
entrySortKey | A sort key for sorting this field value relative to other field values according to how they should be entered for editing. | entrySortKey (attribute) | xsd:string
entryRequired | Whether some kind of entry is required when entering data for editing. | entryRequired (attribute) | xsd:boolean 
editable | Whether the field value is editable. Some field values might be composed from other field values or otherwise calculated by the system. | editable (attribute) | xsd:boolean
parentLabelId | The id of the label for the "parent" field value. For example, the parent field value of a "given name" field value might be the "name" field value. | parentLabelId (attribute) | xsd:string

### examples

```xml
<... id="..." type="..." labelId="..." optional="..." editable="..." displaySortKey="..." entrySortKey="..." entryRequired="..." parentLabelId="...">
  <gx:label>
    ...
  </gx:label>
  ...


  <!-- possibility of extension elements -->

</...>
```

<a name="field-value-descriptor-json-type"/>

### 2.7.2 The "FieldValueDescriptor" JSON Type

The `FieldDescriptor` JSON type is used to (de)serialize the `http://gedcomx.org/v1/FieldDescriptor`
data type.

### properties

name | description | JSON member | JSON object type
-----|-------------|-------------|-----------------
id | The identifier for the JSON element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#fragment-ids). | id | string
type | Enumerated value identifying the type of the field value. | type | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)
labelId | The id for the label of this field value. | labelId | string
optional | Whether the field value was considered optional on the record. | optional | boolean
labels | The human-readable labels for the field values. | labels | [`TextValue`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#text-value)
displaySortKey | A sort key for sorting this field value relative to other field values according to how they should be displayed for viewing. | displaySortKey | string
entrySortKey | A sort key for sorting this field value relative to other field values according to how they should be entered for editing. | entrySortKey | string
entryRequired | Whether some kind of entry is required when entering data for editing. | entryRequired | boolean 
editable | Whether the field value is editable. Some field values might be composed from other field values or otherwise calculated by the system. | editable | boolean
parentLabelId | The id of the label for the "parent" field value. For example, the parent field value of a "given name" field value might be the "name" field value. | parentLabelId | string

### examples

```json
{
  "id" : "...",
  "type" : "...",
  "labelId" : "...",
  "optional" : ...,
  "labels" : [ { ... } , { ... } ],
  "displaySortKey" : "...",
  "entrySortKey" : "...",
  "entryRequired" : ...,
  "editable" : ...,
  "parentLabelId" : "...",

  ...possibility of extension elements...

}
```
<a name="property-extensions"/>

# 3. Property Extensions

This section defines a set of extensions to data types already defined by the
[GEDCOM X Conceptual Model](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md)
and and describes how the properties are included as extensions to
[GEDCOM X JSON](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md) and
[GEDCOM X XML](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md).

<a name="extensions-fact-data-type"/>

## 3.1 Extensions to the "Fact" Data Type

The following properties are defined as extensions to the
[`Fact` Data Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#fact):

name  | description | data type | constraints
------|-------------|-----------|------------
primary | An indication of whether a given fact on a person or relationship is considered the "primary" fact in the context of a record. | boolean | OPTIONAL.

<a name="fact-xml-type-extensions"/>

### 3.1.1 "Fact" XML Type Extensions

name | XML property | XML type
-----|-------------|----------
primary | primary (attribute) | xsd:boolean

<a name="fact-json-type-extensions"/>

### 3.1.2 "Fact" JSON Type Extensions

name | JSON member | JSON object type
-----|-------------|-------------
primary | primary | boolean

<a name="extensions-person-data-type"/>

## 3.2 Extensions to the "Person" Data Type

The following properties are defined as extensions to the
[`Person` Data Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#person):

name  | description | data type | constraints
------|-------------|-----------|------------
principal | An indication of whether a person considered the "principal" person in the context of a record. | boolean | OPTIONAL.

<a name="person-xml-type-extensions"/>

### 3.2.1 "Person" XML Type Extensions

name | XML property | XML type
-----|-------------|--------------
principal | principal (attribute) | xsd:boolean

<a name="person-json-type-extensions"/>

### 3.2.2 "Person" JSON Type Extensions

name | JSON member | JSON object type
-----|-------------|-------------
principal | principal | boolean

<a name="extensions-source-data-type"/>

## 3.3 Extensions to the "SourceDescription" Data Type

The following properties are defined as extensions to the
[`SourceDescription` Data Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#source-description):

name  | description | data type | constraints
------|-------------|-----------|------------
titleLabel | A label for the title of the resource being described. | string | OPTIONAL.
sortKey | A key that can be alphanumerically compared to the sort keys of other resources that indicates the order of records in a collection. | string | OPTIONAL.
descriptorRef | A reference to the descriptor for the record being described. | [URI](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#uri) | OPTIONAL. If provided, MUST resolve to an instance of [`http://gedcomx.org/v1/RecordDescriptor`](#record-descriptor).

<a name="source-xml-type-extensions"/>

### 3.3.1 "SourceDescription" XML Type Extensions

name | XML property | XML type
-----|-------------|--------------
titleLabel | gx:titleLabel | xsd:string
sortKey | sortKey (attribute) | xsd:string
descriptorRef | gx:descriptor | [`gx:ResourceReference`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#resource-reference)

<a name="source-json-type-extensions"/>

### 3.3.2 "SourceDescription" JSON Type Extensions

name | JSON member | JSON object type
-----|-------------|-------------
titleLabel | titleLabel | string
sortKey | sortKey | string
descriptorRef | descriptor | [`ResourceReference`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#resource-reference)

<a name="extensions-source-reference-data-type"/>

## 3.4 Extensions to the "SourceReference" Data Type

The following properties are defined as extensions to the
[`SourceReference` Data Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#source-reference):

name  | description | data type | constraints
------|-------------|-----------|------------
qualifiers | Qualifiers for the reference, used to identify specific fragments of the source that are being referenced. | List of [http://gedcomx.org/v1/Qualifier](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#qualifier) | OPTIONAL. If provided, use of a [known source reference qualifier](#known-source-reference-qualifiers) is RECOMMENDED.

<a id="known-source-reference-qualifiers"/>

#### Known Source Reference Qualifiers

The following name part qualifiers are defined:

name | value
-----|-------
`http://gedcomx.org/CharacterRegion`|A region of text in a digital document, in the form of `a,b` where `a` is the start character and `b` is the end character. The meaning of this qualifier is undefined if the source being referenced is not a digital document.
`http://gedcomx.org/RectangleRegion`|A rectangular region of a digital image. The value of the qualifier is interpreted as a series of four comma-separated numbers. If all of the numbers is less than 1, the value is interpreted in the form of `x1,y1,x2,y2` where `x1,y1` is the relative percentage-based coordinates of the top-left corner of the rectangle and `x2,y2` is the relative percentage-based coordinates of the bottom-right corner of the rectangle. If any of the numbers is more than 1, the value is interpreted in the form of `x,y,w,h` where `x` is the point on the X axis of the image in pixels, `y` is the point on the Y axis in pixels, `w` is the width of the rectangle in pixels, and `h` in the height of the rectangle in pixels.  The meaning of this qualifier is undefined if the source being referenced is not a digital image.
`http://gedcomx.org/TimeRegion`|A region of time of a digital audio or video recording, in the form of `a,b` where `a` is the starting point in milliseconds and `b` is the ending point in milliseconds. The meaning of this qualifier is undefined if the source being referenced is not a digital audio or video recording.

<a name="source-reference-xml-type-extensions"/>

### 3.4.1 "SourceReference" XML Type Extensions

name | XML property | XML type
-----|-------------|--------------
qualifiers | gx:qualifier | [`gx:Qualifier`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#qualifier)

<a name="source-reference-json-type-extensions"/>

### 3.4.2 "SourceReference" JSON Type Extensions

name | JSON member | JSON object type
-----|-------------|-------------
qualifiers | qualifiers | array of [`Qualifier`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#qualifier)


<a name="extensions-coverage-data-type"/>

## 3.5 Extensions to the "Coverage" Data Type

The following properties are defined as extensions to the
[`Coverage` Data Type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#coverage):

name  | description | data type | constraints
------|-------------|-----------|------------
recordType | URI identifying the type of record being covered. | [Enumerated Value](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#enumerated-value) | REQUIRED. MUST identify a resource type, and use of a [known resource type](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#known-resource-types) is RECOMMENDED.

<a name="coverage-xml-type-extensions"/>

### 3.5.1 "Coverage" XML Type Extensions

name | XML property | XML type
-----|-------------|--------------
recordType | gx:recordType | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#uri)

<a name="coverage-json-type-extensions"/>

### 3.5.2 "Coverage" JSON Type Extensions

name | JSON member | JSON object type
-----|-------------|-------------
recordType | recordType | [`URI`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/json-format-specification.md#uri)

<a name="recordset"/>

# 4. The GEDCOM X XML Record Set

As a convenience for exchanging sets of records in a single bundle, this specification defines an additional media type:

`application/x-gedcomx-records-v1+xml`

<a name="gedcomx-xml-element-qname"/>

## 4.1 GEDCOM X XML Record Set Element QName

The QName of a GEDCOM X XML Record Set element is defined by a `LocalPart` of the value `records` and the `NamespaceURI`
of the value `http://gedcomx.org/v1/`.

<a name="gedcomx-element-data-type"/>

## 4.2 GEDCOM X Record Set Element Data Type

The data type of the GEDCOM X Record Set element is defined as follows:

### properties

name | description | XML property | XML type
-----|-------------|--------------|---------
id | The identifier for the XML element. The id attribute MUST conform to the constraints defined in [GEDCOM X XML, Section 7, "Fragment Identifiers"](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#fragment-ids). | id (attribute) | xsd:string
lang | The locale identifier for the record set. | [IETF BCP 47](http://tools.ietf.org/html/bcp47) locale tag | OPTIONAL. If not provided, the locale is determined per [Internationalization Considerations](https://github.com/FamilySearch/gedcomx/blob/master/specifications/conceptual-model-specification.md#il8n).
metadata | A container for metadata common to all records in the record set. Examples include collection hierarchy and record descriptors. | gx:metadata | [`gx:Gedcomx`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#gedcomx-type)
records | The records in the data set. | gx:record | [`gx:Gedcomx`](https://github.com/FamilySearch/gedcomx/blob/master/specifications/xml-format-specification.md#gedcomx-type)

## Example

The following is an example of the structure of a GEDCOM X XML Element:

```xml
<records xmlns="http://gedcomx.org/v1/">
  <metadata>...</metadata>
  <record>...</record>
  <record>...</record>
  <record>...</record>
  <record>...</record>
  ...

  <!-- possibility of extension elements -->
</gedcomx>
```
