# Project metadata development

A project is a continuant in the view of this model. We adopt the definition from CitizenScience.org 'A Project is an organized effort carefully designed to achieve a particular goal.'(https://core.citizenscience.org/docs/project/). 

JSON schema in the schema folder represent evolving metadata models, implemented using (mostly) schema.org vocabulary.  In order to validate with validator.schema.org, have to declare @types for the proejct metadata to include {ResearchProject, MedicalStudy, Event, Action, CreativeWork}. Can't validate multiple types with JSON schema, so root @type property is not in the schema; this allows including properties relevant to projects but scoped more narrowly in schema.org domainIncludes.


ProjectSchema0.2.json uses schema.org entities and properties, and a sampling of metadata for projects on DataCite (https://metadatagamechangers.com/blog/2023/5/2/project-metadata-in-datacite) and in the Ocean Info Hub (https://book.oceaninfohub.org/thematics/projects/README.html) as models for content.

ProjectSchemaRAID.json uses schema.org entities and properties to implement the RAID0.5 model.  'status','instrument','result', and 'authorized_by' are extensions of the RAID model. 'funding' is represented as an explicit property instead as a 'relatedObject' (relatedLink in schema.org).
This implementation uses @id for the container to identify the metadata record, and the 'about' key content to represent to project. The @id in the about section is the project identifier. The @type property in the 'about' section should be an array with include {ResearchProject, MedicalStudy, Event, Action, CreativeWork} to get instances to validata with the schema.org validator. 

The example folder contains some example instances for testing and demonstration.

test-FairIslandProject.json is a relatively complete project description based on ProjectSchema0.2.json, and should be considered the best prototype example for using that scheme.