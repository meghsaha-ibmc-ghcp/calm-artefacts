# Standards

Standards are JSON Schema documents that extend core CALM definitions with organization-specific requirements. We use them to keep shared rules consistent across architectures without duplicating schema logic in every model.

CALM Standards are composed with the core schema using `allOf`. The first schema in the composition is the core CALM definition, and the second schema adds the company-specific properties we want to enforce. This means the resulting schema still behaves like a CALM node or relationship, while also requiring our own fields.

## Company Node Standard

The company node standard extends the core CALM node definition with these required or controlled properties:

- `costCenter`: required string in the form `CC-1234`
- `owner`: required string describing the team or individual responsible
- `environment`: optional string limited to `development`, `staging`, or `production`

This standard is intended for any node that needs ownership, cost allocation, and deployment environment metadata.
The schema file is [company-node-standard.json](company-node-standard.json).

## Company Relationship Standard

The company relationship standard extends the core CALM relationship definition with these required properties:

- `dataClassification`: required string limited to `public`, `internal`, `confidential`, or `restricted`
- `encrypted`: required boolean indicating whether the connection is encrypted

This standard is intended for relationships that need security and data sensitivity metadata.
The schema file is [company-relationship-standard.json](company-relationship-standard.json).
