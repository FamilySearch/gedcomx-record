# GEDCOM X Event Types

## Status

This document enumerates a set of field types to be used for genealogical data exchange,
and requests discussion and suggestions for improvements.

The current state of this document is as a DRAFT, and as such, the document
may be subject to changes, including backwards-incompatible changes, according to the
discussion and suggestions for improvement.

## Copyright Notice

Copyright 2011-2014 Intellectual Reserve, Inc.

## License

This document is distributed under a Creative Commons Attribution-ShareAlike license.
For details, see:

http://creativecommons.org/licenses/by-sa/3.0/

# 1. Introduction

An enumeration of types of fields provides the means for fields to be
be semantically processed by applications, rather than being only interpreted by people. This
specification provides such an enumeration by identifying specific field types and defining
the semantic significance of each type.

## 1.1 Identifier and Version

The identifier for this specification is:

`http://gedcomx.org/field-types/v1`

For convenience, this specification may be referred to as "GEDCOM X Field Types 1.0".
This specification uses "GEDCOM X Field Types" internally.

## 1.2 Notational Conventions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14,
[RFC2119](http://tools.ietf.org/html/rfc2119), as scoped to those conformance
targets.

## 1.2.1 The URI Reference

The Uniform Resource Identifier ("URI") is used to identify event types. The URI is
specified by [RFC 3986](http://tools.ietf.org/html/rfc3986). This specification uses the term
"URI" to refer to both a "URI" and a "URI Reference" as defined by
[RFC 3986](http://tools.ietf.org/html/rfc3986).

# 2. Field Types

The following event types are specified:

URI | description
----|-------------
`http://gedcomx.org/Age`| A field that provides the age of a person.
`http://gedcomx.org/Date`| A field that provides a date.
`http://gedcomx.org/Place`| A field that provides a place.
`http://gedcomx.org/Gender`| A field that provides the gender of a person.
`http://gedcomx.org/Name`| A field that provides the name person.
`http://gedcomx.org/Role`| A field that provides the role person, such as the role of a person in a household.
`http://gedcomx.org/Years`| A field that provides a number of years.
`http://gedcomx.org/Months`| A field that provides a number of months.
`http://gedcomx.org/Days`| A field that provides a number of days.
`http://gedcomx.org/Hours`| A field that provides a number of hours.
`http://gedcomx.org/Minutes`| A field that provides a number of minutes.
`http://gedcomx.org/Year`| A field that provides the year of a date.
`http://gedcomx.org/Month`| A field that provides the month of a date.
`http://gedcomx.org/Day`| A field that provides the day of a date.
`http://gedcomx.org/Hour`| A field that provides the hour of a date.
`http://gedcomx.org/Minute`| A field that provides the minute of a date.
`http://gedcomx.org/Address`| A field that provides an address.
`http://gedcomx.org/Cemetery`| A field that provides the name of a cemetery.
`http://gedcomx.org/City`| A field that provides the name of a city.
`http://gedcomx.org/Church`| A field that provides the name of a church.
`http://gedcomx.org/County`| A field that provides the name of a county.
`http://gedcomx.org/Country`| A field that provides the name of a country.
`http://gedcomx.org/District`| A field that provides the name of a district.
`http://gedcomx.org/Hospital`| A field that provides the name of a hospital.
`http://gedcomx.org/Island`| A field that provides the name of an island.
`http://gedcomx.org/MilitaryBase`| A field that provides the name of a military base.
`http://gedcomx.org/Mortuary`| A field that provides the name of a mortuary.
`http://gedcomx.org/Parish`| A field that provides the name of a parish.
`http://gedcomx.org/PlotNumber`| A field that provides a plot number.
`http://gedcomx.org/PostOffice`| A field that provides the name of a post office.
`http://gedcomx.org/PostalCode`| A field that provides a postal code.
`http://gedcomx.org/Prison`| A field that provides the name of a prison.
`http://gedcomx.org/Province`| A field that provides the name of a province.
`http://gedcomx.org/Section`| A field that provides the name of a section.
`http://gedcomx.org/Ship`| A field that provides the name of a ship.
`http://gedcomx.org/State`| A field that provides the name of a state.
`http://gedcomx.org/Territory`| A field that provides the name of a territory.
`http://gedcomx.org/Town`| A field that provides the name of a town.
`http://gedcomx.org/Township`| A field that provides the name of a township.
`http://gedcomx.org/Ward`| A field that provides the name of a ward.
`http://gedcomx.org/Prefix`| A field that provides a name prefix.
`http://gedcomx.org/Suffix`| A field that provides a name suffix.
`http://gedcomx.org/Given`| A field that provides a given name.
`http://gedcomx.org/Surname`| A field that provides a surname.
`http://gedcomx.org/Abusua`| A field that provides the abusua.
`http://gedcomx.org/BatchNumber`| A field that provides the batch number.
`http://gedcomx.org/Caste`| A field that provides the caste.
`http://gedcomx.org/Clan`| A field that provides the clan.
`http://gedcomx.org/CommonLawMarriage`| A field that indicates a common law marriage.
`http://gedcomx.org/Education`| A field that describes the education of a person.
`http://gedcomx.org/Ethnicity`| A field that describes the ethnicity of a person.
`http://gedcomx.org/FatherBirthPlace`| A field that provides the birth place of the father of a person.
`http://gedcomx.org/MotherBirthPlace`| A field that provides the birth place of the mother of a person.
`http://gedcomx.org/NeverHadChildren`| A field that indicates a person never had children.
`http://gedcomx.org/NeverMarried`| A field that indicates a person was never married.
`http://gedcomx.org/NumberOfChildren`| A field that provides a number of children of a person.
`http://gedcomx.org/NumberOfMarriages`| A field that provides the number of marriages of a person.
`http://gedcomx.org/Household`| A field that indicates the household of a person.
`http://gedcomx.org/IsHeadOfHousehold`| A field that indicates whether a person is the head of a household.
`http://gedcomx.org/MaritalStatus`| A field that provides the marital status of a person.
`http://gedcomx.org/MultipleBirth`| A field that indicates a multiple birth (e.g. twin).
`http://gedcomx.org/NameSake`| A field that provides the namesake of a person.
`http://gedcomx.org/NationalId`| A field that provides the national id of a person.
`http://gedcomx.org/Nationality`| A field that provides the nationality of a person.
`http://gedcomx.org/Occupation`| A field that provides the occupation of a person.
`http://gedcomx.org/PhysicalDescription`| A field that provides the physical description of a person.
`http://gedcomx.org/Property`| A field that provides the property of a person.
`http://gedcomx.org/Race`| A field that provides the race of a person.
`http://gedcomx.org/Religion`| A field that provides the religion of a person.
`http://gedcomx.org/RelationshipToHead`| A field that indicates the relationship to the head of household of a person.
`http://gedcomx.org/Stillbirth`| A field that indicates a stillbirth.
`http://gedcomx.org/TitleOfNobility`| A field that provides the title of nobility of a person.
`http://gedcomx.org/Tribe`| A field that provides the tribe of a person.