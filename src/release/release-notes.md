The OSCAL Project has releases Milestone 3, Milestone 2 and Milestone 1, given here in reverse order of release date.

# OSCAL 1.0.0 Milestone 3
--

## Understanding this change log

The models are described using OSCAL Metaschema terminology. Depending on the OSCAL representation you prefer (for example, XML or JSON), the object in question may be represented as a labeled property or unlabeled array member (in JSON) or as an element or attribute (XML). Similarly, in either case it may be an object with or without a nominal data value associated (such as at leaf nodes of the nominal information network), or alternatively a composite of other objects.

Refer to docs on Metaschema language and mappings into data objects, especially 
Terminology [https://pages.nist.gov/metaschema/specification/concepts/terminology/] and Mapping [https://pages.nist.gov/metaschema/specification/mapping/].

Users of object notations should take note that individual objects described in the metaschema model may, when serialized as JSON, take the form of array members without keys, the semantic key (a grouping key) being assigned to the group of like objects. So a 'prop' object defined in the metaschema appears in the JSON as a member of an object 'properties'.

## Notation

In the log below, [M3} indicates the Milestone 3 definitions, while [M2] indicates Milestone 2 definitions.

Assembly models are noted with DTD (RNC) notation indicating cardinality: suffix '*' indicates zero-or-more, '+' is one-or-more, '?' is zero-or-one (i.e., optional), no indicator is used for one-only (required). So (a, b, b) and (a, b, c) are valid to pattern expression (a, b+, c*), but (a, c) is not.

# Changes from OSCAL 1.0.0 Milestone 3 (M3) to Release Candidate 1 (RC1)

Changes in this release have been focused on the following major areas:
- Making naming in XML and JSON/YAML more consistent.
- Ensuring that all data types and cardinalities are appropriate.
- Refactoring to cleanup models, making them: 1) more consistent with the other OSCAL models, 2) making them more simple when possible, and 3) providing room for future addition of new features.

## Changes common to all models

- many elements in XML, and properties in JSON and YAML, have been renamed to make the naming more consistent between elements names in XML and property names in JSON and YAML. Now JSON properties that contain an array of objects use a plural form of the XML element name. The one exception is "prop" in XML vs "properties" in JSON and YAML. This decision was made to make the XML use of "prop" more concise, since "prop" elements are used a good deal in OSCAL XML formats.

### Changes to all XML formats

In {top-level-element}/metadata:
- renamed "revision-history" to "revisions"
- renamed "doc-id" to "document-id"

In {top-level-element}/metadata/document-id:
- renamed "type" to "scheme"

In {top-level-element}/metadata/link:
- Defined allowed values for the "rel" property

In {top-level-element}/metadata/location:
- renamed "email" to "email-address"
- renamed "phone" to "telephone-number"

In {top-level-element}/metadata/location/prop:
- Defined allowed values for the "name" attribute. Using the "type" as the name attribute value, you can now specify that a location is a "data-center" location and also use the "class" attribute to qualify the data center location as "primary" or "alternate".

In {top-level-element}/metadata/party:
- renamed "party-name" to "name" 
- renamed "email" to "email-address"
- renamed "phone" to "telephone-number"
- changed sequencing of address
- made use of address and location-uuid mutually exclusive, since either a static address or a reference to location provides similar functionality. The "location-type" attribute has been removed. This should data should now be described on the referenced "location" element using a prop element with a name of "type".

In {top-level-element}/metadata/party/prop:
- Defined allowed values for the "name" attribute. This can be used to provide a "mail-stop", "office", or "job-title".

In {top-level-element}/metadata/party/external-id:
- renamed "type" to "scheme" 

In {top-level-element}/metadata/role:
- renamed "desc" to "description"

In {top-level-element}/back-matter/resource:
- renamed "desc" to "description"
- renamed "doc-id" to "document-id"

In {top-level-element}/back-matter/resource/prop:
- defined allowed values "type", "version", and "published" for the "name" property.

In {top-level-element}/metadata/resource/document-id:
- renamed "type" to "scheme"

In {top-level-element}/back-matter/resource/rlink:
- changed type from "uri" to "uri-reference"
- renamed "hash-value" to "hash"

Changes to all "prop" elements:
- changed the data type of "ns" to "uri"
- renamed "id" to "uuid" and changed type to "uuid"

Changes to all "annotation" elements:
- changed the data type of "ns" to "uri"
- renamed "id" to "uuid" and changed type to "uuid"

### Changes to all JSON and YAML formats

In {top-level-object}/metadata:
- renamed "revision-history" to "revisions"
- renamed "properties" to "props"

In {top-level-object}/metadata/revisions:
- renamed "properties" to "props"

In {top-level-object}/metadata/document-ids:
- renamed "type" to "scheme" and changed to data type from "string" to "uri"

In {top-level-object}/metadata/links:
- Defined allowed values for the "rel" property

In {top-level-object}/metadata/locations
- renamed "URLs" to "urls"
- renamed "properties" to "props"

In {top-level-object}/metadata/locations/props:
- Defined allowed values for the "name" property. Using the "type" prop name, you can now specify that a location is a "data-center" location and also use the "class" property to qualify the data center location as "primary" or "alternate".

In {top-level-object}/metadata/parties:
- renamed "party-name" to "name" 
- renamed "properties" to "props"
- made use of addresses and location-uuids mutually exclusive, since either a static address or a reference to location provides similar functionality. The "location-type" property on "location-uuid" has been removed. This should data should now be described on the referenced "location" element using a prop element with a name of "type".

In {top-level-object}/metadata/parties/props:
- defined allowed values for the "name" property. This can be used to provide a "mail-stop", "office", or "job-title".

In {top-level-object}/metadata/parties/external-ids:
- renamed "type" to "scheme" 

In {top-level-object}/metadata/roles:
- renamed "desc" to "description"
- renamed "properties" to "props"

In {top-level-object}/back-matter/resources:
- renamed "desc" to "description"
- renamed "properties" to "props"

In {top-level-object}/back-matter/resources/props:
- defined allowed values "type", "version", and "published" for the "name" property.

In {top-level-object}/back-matter/resources/citation:
- renamed "properties" to "props"

In {top-level-object}/back-matter/resources/document-ids:
- renamed "type" to "scheme" and changed to data type from "string" to "uri"

In {top-level-object}/back-matter/resources/rlinks:
- changed type from "uri" to "uri-reference"
- renamed "hash-values" to "hashes"

Changes to all "props" objects:
- changed the data type of "ns" to "uri"

Changes to all "annotations" objects:
- changed the data type of "ns" to "uri"
- the "value" property is now required.

Changes to all "address" or "addresses" objects:
- renamed "postal-address" to "addr-lines"

Changes to all "responsible-party" objects:
- renamed "properties" to "props"

Changes to all "responsible-role" objects:
- renamed "properties" to "props"
- renamed "party-ids" to "party-uuids"

## Changes to common to the catalog and profile models

The following changes have been made to format structures that are shared between the formats for the catalog and profile models.

### Changes affecting the catalog and profile XML formats

Changes to all "part" elements:
- changed the data type of "ns" to "uri"

Changes to all "param" elements:
- added the "prop" and "link" elements.
- changed the sequencing of "link" to be consistent with other elements that include "link".
- changed the data type of "usage" from "markup-line" to "markup-multiline"
- changed "constraint" from an element with a text value, to an element with child elements. The text value is now contained in the "description" element. Also changed the "test" attribute to be a sequence of child "test" elements, with the text value now contained in the "expression" attribute.
- changed the cardinality of "value" to allow for multiple values". The data type of a value has changed from markup-line to string.

### Changes affecting the catalog and profile JSON and YAML formats

Changes to all "part" or "parts" objects:
- changed the data type of "ns" to "uri"
- renamed "properties" to "props"
- added allowed values "label" and "sort-id" for props/name.

Changes to all "param" or "params" objects:
- added the "props" and "links" properties.
- changed the data type of "usage" from "markup-line" to "markup-multiline"
- renamed "guidance" to "guidelines"
- renamed "value" to "values". Also, changed the cardinality of "value" to allow for multiple "values". The data type of a value has changed from markup-line to string.
- changed the sequencing of "link" to align with similar elements in OSCAL.

For params/select/how-many:
- renamed "alternatives" to "choices"

For params/select/how-many/alternatives:
- renamed "RICHTEXT" property to "value"

For params/constraints:
- renamed "detail" to "description". Change the data type from "string" to "markup-multiline".
- renamed "test" to "tests", which is now an array of objects.
  - The original "test" string value is now stored in the child object's "expression" property.
  - Added a new "remarks" property.


## Changes to the catalog model

### Changes to the catalog XML format

For /catalog//group and /catalog//control:
- defined allowed values for prop/@name

### Changes to the catalog JSON and YAML formats

For /catalog, /catalog//groups, and /catalog//controls:
- renamed "parameters" to "params"

For /catalog//groups and /catalog//controls:
- renamed "properties" to "props"
- defined allowed values for props/name

## Changes to the profile model

### Changes to profile XML format

For /profile/merge/custom//groups:
- added "annotation" and "link"

For /profile/modify/set-parameter:
- added "prop" and "annotation"
- change sequencing of "link"

For /profile/modify/alter/add:
- defined allowed values for prop/@name

### Changes to profile JSON and YAML formats

For /profile/imports/(include|exclude):
- renamed "id-selectors" to "calls"
- renamed "pattern-selectors" to "matches"

For /profile/merge/custom//groups:
- renamed "parameters" to "params"
- renamed "properties" to "props"
- added "annotations" and "links"

For /profile/modify:
- renamed "parameter-settings" to "set-parameters"
- renamed "alterations" to "alters"

For /profile/modify/set-parameters:
- added "props" and "annotations"
- renamed "usages" to "usage", and changed data type from an array of "string" to "markup-multiline"

For /profile/modify/alters:
- renamed "removals" to "removes"
- renamed "additions" to "adds"

For /profile/modify/alters/adds:
- renamed "parameters" to "params"
- renamed "properties" to "props"
- defined allowed values for props/name

## Changes to the SSP model

### Changes to the SSP XML format

For /system-security-plan/system-characteristics:
- added allowed values for prop/@name, annotation/@name, link/@rel, and responsible-roles/role-id

For /system-security-plan/system-characteristics/*/diagram:
- added "annotation"
- changed the data type of "caption" from "string" to "markup-line"
- added allowed values for link/@rel="diagram", which allows for the linking of an image to use for the diagram.

For /system-security-plan/system-characteristics/system-information/information-type:
- renamed "id" to "uuid"
- changed structure of "information-type-id" to be wrapped by an outer characterization, which now defines the "system" for all referenced information type identifiers.
- added "annotation"

For /system-security-plan/system-characteristics/system-information/information-type/*-impact:
- added "annotation" and "link"

For /system-security-plan/system-characteristics/authorization-boundary:
- the "description" text is now wrapped with a "description" element

For /system-security-plan/system-characteristics/network-architecture:
- the "description" text is now wrapped with a "description" element

For /system-security-plan/system-characteristics/data-flow:
- the "description" text is now wrapped with a "description" element

For /system-security-plan/system-implementation/leveraged-authorization:
- defined additional allowed values "implementation-point", "leveraged-authorization-uuid", "inherited-uuid" for prop/@name, which provides traceability to a leveraged SSP
- defined allowed values for link/@rel

For /system-security-plan/system-implementation/user:
- defined allowed values for annotation/@name and role-id

For /system-security-plan/system-implementation/component:
- renamed "component-type" to "type", and updated allowed values
- defined allowed values for prop/@name, annotation/@name, link/@rel, and responsible-role/@role-id

For /system-security-plan/system-implementation/inventory-item:
- moved "@asset-id" to a required prop/@name
- defined allowed values for prop/@name, annotation/@name, link/@rel, and responsible-role/@role-id

For /system-security-plan/system-implementation/inventory-item/implemented-component:
- renamed "component-id" to "component-uuid"
- defined allowed values for prop/@name, annotation/@name, and responsible-party/@role-id
- removed "use", since this is capturing similar information to the component's type

For /system-security-plan/control-implementation/implemented-requirement:
- removed "description"
- added allowed values for annotation/@name including "implementation-status", "control-origination"
- added allowed values for prop/@name including "leveraged-authorization" to indicate if a control implementation is inherited from an underlying authorized system
- added allowed values for responsible-role/$role-id

For /system-security-plan/control-implementation/implemented-requirement/by-component:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

For /system-security-plan/control-implementation/implemented-requirement/statement:
- removed "description"

For /system-security-plan/control-implementation/implemented-requirement/statement/by-component:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

### Changes to the SSP JSON and YAML formats

For /system-security-plan/system-characteristics:
- renamed "properties" to "props"
- added allowed values for props/name, annotations/name, links/rel, and responsible-roles/role-id

For /system-security-plan/system-characteristics/*/diagrams:
- added "annotation"
- changed the data type of "caption" from "string" to "markup-line"
- added allowed values for link/@rel="diagram", which allows for the linking of an image to use for the diagram.

For /system-security-plan/system-characteristics/system-information:
- renamed "properties" to "props"

For /system-security-plan/system-characteristics/system-information/information-types:
- renamed "id" to "uuid"
- changed structure of "information-type-id" to be wrapped by an outer characterization, which now defines the "system" for all referenced information type identifiers.
- added "annotations"

For /system-security-plan/system-characteristics/system-information/information-types/*-impact:
- added "annotations" and "links"

For /system-security-plan/system-characteristics/authorization-boundary:
- renamed "properties" to "props"

For /system-security-plan/system-characteristics/network-architecture:
- renamed "properties" to "props"

For /system-security-plan/system-characteristics/data-flow:
- renamed "properties" to "props"

For /system-security-plan/system-implementation:
- renamed "properties" to "props"

For /system-security-plan/system-implementation/leveraged-authorizations:
- defined additional allowed values "implementation-point", "leveraged-authorization-uuid", "inherited-uuid" for prop/name, which provides traceability to a leveraged SSP
- defined allowed values for links/rel

For /system-security-plan/system-implementation/users:
- defined allowed values for annotation/name and role-id

For /system-security-plan/system-implementation/components:
- renamed "component-type" to "type", and updated allowed values
- defined allowed values for props/name, annotations/name, links/rel, and responsible-roles/role-id

For /system-security-plan/system-implementation/inventory-items:
- moved "asset-id" to a required props/name
- defined allowed values for props/name, annotations/name, links/rel, and responsible-parties/role-id

For /system-security-plan/system-implementation/inventory-items/implemented-components:
- renamed "component-id" to "component-uuid"
- defined allowed values for props/name, annotations/name, and responsible-parties/role-id
- removed "use", since this is capturing similar information to the component's type

For /system-security-plan/control-implementation/implemented-requirements:
- removed "description"
- renamed "properties" to "props"
- added allowed values for annotations/name including "implementation-status", "control-origination"
- added allowed values for props/name including "leveraged-authorization" to indicate if a control implementation is inherited from an underlying authorized system
- added allowed values for responsible-roles/role-id

For /system-security-plan/control-implementation/implemented-requirements/by-components:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

For /system-security-plan/control-implementation/implemented-requirements/statements:
- removed "description"

For /system-security-plan/control-implementation/implemented-requirements/statements/by-components:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

## Changes to the component definition model

### Changes to the component definition XML format

For /XXX/system-implementation/component:
- renamed "component-type" to "type", and updated allowed values
- defined allowed values for prop/@name, annotation/@name, link/@rel, and responsible-role/@role-id

For /XXX/system-implementation/user:
- defined allowed values for annotation/@name and role-id

For /XXX/system-implementation/inventory-item:
- moved "@asset-id" to a required prop/@name
- defined allowed values for prop/@name, annotation/@name, link/@rel, and responsible-role/@role-id

For /XXX/system-implementation/inventory-item/implemented-component:
- renamed "component-id" to "component-uuid"
- defined allowed values for prop/@name, annotation/@name, and responsible-party/@role-id

For /system-security-plan/control-implementation/implemented-requirements:
- removed "description"

For /system-security-plan/control-implementation/implemented-requirements/by-component:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

For /system-security-plan/control-implementation/implemented-requirements/statements:
- removed "description"

For /system-security-plan/control-implementation/implemented-requirements/statements/by-component:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

### Changes to the component definition JSON and YAML formats

For /XXX/system-implementation/components:
- renamed "component-type" to "type", and updated allowed values
- defined allowed values for props/name, annotations/name, links/rel, and responsible-roles/role-id

For /XXX/system-implementation/users:
- defined allowed values for annotation/name and role-id

For /XXX/system-implementation/inventory-items:
- moved "asset-id" to a required props/name
- defined allowed values for props/name, annotations/name, links/rel, and responsible-parties/role-id

For /XXX/system-implementation/inventory-items/implemented-components:
- renamed "component-id" to "component-uuid"
- defined allowed values for props/name, annotations/name, and responsible-parties/role-id

For /system-security-plan/control-implementation/implemented-requirements:
- removed "description"

For /system-security-plan/control-implementation/implemented-requirements/by-components:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

For /system-security-plan/control-implementation/implemented-requirements/statements:
- removed "description"

For /system-security-plan/control-implementation/implemented-requirements/statements/by-components:
- renamed "component-id" to "component-uuid"
- added "export", "inherited", and "satisfied" to support documenting leveraged authorizations
- added "remarks" to allow for adding general commentary

## Changes to the assessment plan model

### Changes to the assessment plan XML format

### Changes to the assessment plan JSON and YAML formats


## Changes to the assessment results model

### Changes to assessment results XML format

### Changes to assessment results JSON and YAML formats


## Changes to the plan of actions and milestones (PO&M) model

### Changes to the plan of actions and milestones XML formats

### Changes to the plan of actions and milestones JSON and YAML formats


# Changes from OSCAL 1.0.0 Milestone 2 (M2) to M3
--

## New OSCAL models

The following new models have been added to OSCAL.

- Component Definition model: Allows for the definition of a set of *components* that each provide a description of the controls supported by a specific implementation of a hardware, software, or service; or by a given policy, process, procedure, or compliance artifact (e.g., FIPS 140-2 validation).
- Assessment Plan model: Represents the planning for a periodic or continuous assessment.
- Assessment Results model: Represents the findings of a periodic or continuous assessment of a specific system.
- Plan of Action and Milestones (POA&M) model: Represents the known risks for a specific system, as well as the identified deviations, remediation plan, and disposition status of each risk.

## Changes to all Models

### Changing 'name' flag to 'title' field

On several assemblies, what had been represented with a 'name' flag is now represented with a 'title' field, which permits inline markup.

'title' now appears in these assemblies: 'metadata', 'revision', 'location', 'resource', 'role', 'information-type', 'leveraged-authorization', 'user', 'authorized-privilege', 'component', and 'protocol'.

### Changes of ID to UUID

A number of assemblies that used to carry 'id' flags now carry 'uuid' flags instead. These include (in the SSP model) : 'location', 'party', 'resource', 'diagram', 'user', 'component', 'protocol', 'inventory-item', 'implemented-requirement', 'statement', and 'by-component'. In all models, it includes 'location', 'party', and 'resource'. Finally, the full assemblies 'catalog', 'profile' and 'system-security-plan' fall into this category.

Similarly, flags and fields that are named to indicate they provide a point of reference, are now renamed '-uuid' reflecting when their references is given specifically as a 'uuid' (and validated as such) not as an 'id'. These include 'location-uuid' and 'party-uuid'.

### 'metadata' changes

Milestone 3 has two assemblies in the metadata, revision for tracking a revision history, and location, an abstraction (and alternative) to the older address modeling.

[M2] model: title (field), published? (field), last-modified (field), version (field), oscal-version (field), doc-id* (field), prop* (field), link* (field), role* (assembly), party* (assembly), responsible-party* (assembly), remarks? (field)

[M3] model: title (field), published? (field), last-modified (field), version (field), oscal-version (field), revision* (assembly), doc-id* (field), prop* (field), link* (field), role* (assembly), location* (assembly), party* (assembly), responsible-party* (assembly), remarks? (field)

#### New 'revision' assembly: Revision History Entry (all models)

Tracking revisions can now be done by capturing a snapshot of metadata at an earlier point, potentially with properties or remarks added to indicate revision status or purpose.

[M3] model: title? (field), published? (field), last-modified? (field), version? (field), oscal-version? (field), prop* (field), link* (field), remarks? (field)

#### New 'location' assembly: Location (all models)

A new assembly permits factoring out geographic or contact information (an address or contact point) into a separate data structure, for reference using its 'uuid' flag.

[M3] model: title? (field), address (assembly), email* (field), phone* (field), url* (field), prop* (field), annotation* (assembly), link* (field), remarks? (field)

#### New 'location-uuid': Location Reference

#### 'party' changes (all models)

'party' is for Party (organization or person). It has been refactored to reflect the (somewhat arbitrary) 'organization' vs 'person' distinction into a 'type' flag.

Where before, we had an 'id' flag, now we have 'uuid'. We also have 'type', a flag whose value can capture "person" or "organization".

We also have new fields for linking to other assemblies, including 'member-of-organization'. Instead of 'org-name' and 'person-name' we simply have 'party-name'.

[M2] flags: id?

[M3] flags: uuid?, type?

[M2] model: person* (assembly), org? (assembly), prop* (field), annotation* (assembly), link* (field), remarks? (field)

[M3] model: party-name (field), short-name? (field), external-id* (field), prop* (field), annotation* (assembly), link* (field), address* (assembly), email* (field), phone* (field), member-of-organization (field), location-uuid (field)**, remarks? (field)

#### New field 'party-uuid': Party Reference

Replaces 'person/id' and 'org/id' from the M2 model.

#### New field 'external-id': Personal Identifier

Replaces 'party-id' and 'org-id' from the M2 model.

#### New field 'member-of-organization': Organizational Affiliation

Used to associate a person or organization with another organization. This can be used to create organization hierarchies.

#### New field 'party-name': Party Name

Replaces 'org-name' and 'person-name' from the M2 model.

### 'back-matter' changes

In the back matter, the old 'citation' element has been refactored as a special case of 'resource'.

[M2] model: citation* (assembly), resource* (assembly)

[M3] model: resource* (assembly)

#### Refactored 'resource': Resource

The old 'citation' assembly is now a child, not a sibling of resource within 'back-matter'. As such it has been remodeled to support as much specialized citation information as may be available for a resource.

[M2] flag: id?

[M3] flags: uuid?

[M2] model: desc? (field), prop* (field), (A choice: rlink* (assembly), base64? (field) ) , remarks? (field)

[M3] model: title? (field), desc? (field), prop* (field), doc-id* (field), citation? (assembly), rlink* (assembly), base64* (field), remarks? (field), (any)

New assemblies and fields to support the citation model.

#### New field 'text': Biblographic Text

A plain-text capture of a bibliographic citation.

#### New assembly 'biblio': Bibliographic Definition

A structured representation of a bibliographic resource (an extension point).

#### 'citation' changes

A 'citation' now appears only as a child of a 'resource'.

[M2] flag: id?

[M3] flag: [none]

[M2] model:  target* (field), title? (field), desc? (field), doc-id* (field), prop* (field), ? (any)

[M3] model: text (field), prop* (field), biblio? (assembly)


## Changes to the Profile Model

### Change to 'add': Addition (profile model)

A new 'id-ref' flag permits targeting an addition to a particular object (branch) within the structure addressed for addition. Additionally, an 'annotation' element may also be added.

[M2] flag: position?

[M3] flags: position?, id-ref?

[M2] model: title? (field), param* (assembly), prop* (field), link* (field), part* (assembly)

[M3] model: title? (field), param* (assembly), prop* (field), annotation* (assembly), link* (field), part* (assembly)

## Changes to the System Security Plan (SSP) Model

### 'system-implementation' changes

An assembly for 'leveraged-authorization' has been added. 'leveraged-authorization' used to be in 'system-characteristics'.

[M2] model: prop* (field), annotation* (assembly), link* (field), user* (assembly), component* (assembly), service* (assembly), interconnection* (assembly), system-inventory? (assembly), remarks? (field)

[M3] model: prop* (field), annotation* (assembly), link* (field), leveraged-authorization* (assembly), user* (assembly), component* (assembly), system-inventory? (assembly), remarks? (field)

### 'component' changes

The component assembly has been remodeled to permit greater generality and expressiveness. New assemblies include 'title', 'purpose', and 'protocol'.

[M2] flags: id?, name?, component-type?

[M3] flags: uuid?, component-type?

[M2] model: description (field), prop* (field), annotation* (assembly), link* (field), status (assembly), responsible-role* (assembly), remarks? (field)

[M3] model: title (field), description (field), purpose? (field), prop* (field), annotation* (assembly), link* (field), status (assembly), responsible-role* (assembly), protocol* (assembly), remarks? (field)

### Rename 'set-param' to 'set-parameter'

In profile SSP models, the assembly used to set a parameter is consistently called 'set-parameter'.



# Changes from OSCAL 1.0.0 Milestone 1 (M1) to M2
--

## New OSCAL Features

- A System Security Plan (SSP) model has been added to OSCAL for use by organizations to document the implementation of security and privacy controls in an information system.

## Breaking Changes

The following content model changes have been made to the catalog and profile models that may break content compatibility:

### Document metadata

  * `last-modified` is now required. Its value must be a date-time with time zone (i.e., a timestamp). The old element `last-modified-date` is no longer permitted.
  * `published` is permitted for a nominal publication date, as assigned by the owner or publisher of the catalog or resource. An electronic version of a previously published catalog should carry its own publication date, if any, not that of the original resource (which can be described elsewhere with its own metadata).
  * `role-id` is now assigned as an element in the XML, not an attribute. This permits it to be tokenized more explicitly.

### Control structures in the catalog model

#### New property in SP800-53 catalog data

In the SP800-53 catalog, we have added a property called `sort-id` to controls and enhancements. Its string value represents the control's ID in a (zero-padded) notation that will sort gracefully against other `sort-id` values. This permits a robust reordering of controls in receiving systems without having to refer to an out-of-line document to restore the canonical order.

#### Controls inside controls, but no "subcontrols"

Control enhancements are now represented using `control` not `subcontrol`. The advantages of restricting to two levels of hierarchy (even given groups and parts) became too few in view of the sacrifices to expressiveness so we have gone back to clean recursion.

### Data type handling

Data type handling has been extended in several respects to provide for the validating of lexical forms of nominal datatypes. Datatypes for dates and times have been added. Several XML-peculiar datatypes have been removed.

#### Value enumeration on terminal nodes

The schema has also been extended to support validation against enumerated values, either exclusively (only declared values may appear) or inclusively (enumerations are documented while other values are also permitted). All allowed values now being declared (Milestone 2) are inclusive of other values (user- or application-defined), so this is not a breaking change.

Affected data points (in both models): `prop/name`, `address/type`, `phone/type`, `hash/algorithm`, `role-id`. The enumerated values provided for each are documented.

#### Lexical datatyping at points

Supported for lexical datatyping has also been added to `link/href`, `rlink/href` (URI references), `published` and `last-modified` (timestamps), `email` (a nominal email address), `url` (a URI), `img/src`.

### Profile model enhancements

#### Calling control enhancements (old "subcontrols")

From call statements, since `subcontrol` has been dropped from the catalog model, `subcontrol-id` has been replaced with `control-id`, and `with-subcontrols` has been replaced by `with-child-controls` (on `call`, `all` and `match`). Essentially, a subcontrol is now represented as a control that is a child another parent control.

#### Expanded model for new groups

Elements besides control references are now permitted inside `group` within the `merge` construct, so profile authors can provide titles and introductory content to groups they define for their represented aggregate control structures.

#### Parameter settings

Added 'guideline' to profile model. It was omitted in error.

XXX see Issues #494, #288 (adding 'guideline' to profile model)


# OSCAL 1.0.0 Milestone 1 (M1)
--

- The first official OSCAL release
- Provides stable versions of the OSCAL catalog and profile models in XML and JSON formats, along with associated XML and JSON schemas.
- Includes draft versions of the NIST SP 800-53 revision 4 OSCAL content and FedRAMP baselines in OSCAL XML, JSON, and YAML formats.
- Provides content converters that are capable of accurately converting between OSCAL catalog and profile content in OSCAL XML to OSCAL JSON format and vice versa.

