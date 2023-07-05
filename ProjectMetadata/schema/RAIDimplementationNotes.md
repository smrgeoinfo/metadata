# Notes on implementation of RAID 0.5 model 

Implementation is intended to validate with schema.org validator, and also be useful as JSON-LD. 

The @id for the record identifies metadata record, there is an 'about' key,  and the @id for the object there is the RAID (or other URI) for the project.  see discussion [JSONLD-IDinSchemaOrgMetadata.md](../../JSONLD-IDinSchemaOrgMetadata.md).

sdo:identifier is used for alternateIdentifiers as sdo:PropertyValue (an ESIP science on schema.org pattern). 

instead of contributors, all the people involved in the project are sdo:participants, using the sdo Role construction to assign roles. Position and Role in RAID are both considered roles.  A participant can have multiple roles. 

Organization relationships use sdo:affiliation, probably the biggest stretch in property semantics.  sdo really doesn't have a generic related organization property; could just put these in relatedLink.  

sdo:funding is used to link to a Grant (which has to cover 'contract' etc...), and Grant has a funder giving link to agency (instead of relatedLink). The Grant can have an identifier, name, description, etc. 

sdo:relatedLink for RAID elements relatedObject and relatedRAID. Uses sdo:LinkRole and sdo:EntryPoint to capture details about the link and its target.-- closest I can get to IEFT RFC8288 (Web Linking) with sdo.  Use of contentType on the EntryPoint will be important to identify kinds of link targets.

use sdo:ethicsPolicy to cover TraditionalKnowledgeLabelScheme, in samples we want a way to recognize CARE principles as well; there's probably other ones...

use sdo:DefinedTerm for keywords from FAIR vocabularies (that have a resolvable URI and label), tags are just keyword with string value. 

location allows simple place name, and/or geometry with bounding box or point location.

### Add
- status -- enumeration, e.g. {planned, in progress, complete, abandoned, on hold}
- instrument -- for e.g. lab projects using particular instrumentation, expedition using a research ship, sensor-based observation projects.
- result-- links to project products, or text description of outcomes.
- authorized_by -- this is one the biologists are interested in when they need permits to collect living things in protected areas; probably applies to various other kinds of field research or human subject projects. 
