Generating JSON Schemas from schema.org data
==============

The schemas at http://schema.org/ are very helpful for formats like JSON-LD, but they lack a canonical JSON representation.

This tool generates schemas describing a canonical plain-JSON serialisation for each of the schema.org types.

## Multiplicity of relations

The documentation at schema.org gives no indication which properties/relations can have multiple entries.  A `PostalAddress` should (intuitively) only have one `streetAddress`, but many other properties are one-to-many mappings (represented in JSON as arrays instead of direct values).

Most of these were initially guessed based on whether their descriptions started with "A(n)" or "The".  This is sometimes inaccurate (e.g. http://schema.org/follows), so hand-edits should be made to `property-multiplicity.json`.

## `#/definitions/possibleRef`

This definition is added to all generated schemas, and it represents a type that can either be a reference (URL string) to an external resource or an actual inlined resource.