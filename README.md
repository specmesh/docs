# specmesh

![specmesh-logo-400](https://user-images.githubusercontent.com/71075996/190342554-e0d8cd5d-7025-41fe-910e-665e91438c6b.png)

### Specification driven data mesh for the enterprise

**Goal**: 
To make Data Mesh simple, Open Source and available to all; without vendor lock-in, without complex tooling and to use an approach centered around ‘specifications’, existing tools and baking in a ‘domain’ model. 

(insert image here)

### Scope
- Running OTS infrastructure like connectors and all things, webservices, microservices or processors…. They are the problem of the client, not the Mesh itself. 

### Problem Statement:
- Everyone is touting Data Mesh as the next big thing and throwing lots of tech at it; and it’s getting confusing, many bespoke, many commercial solutions… it should be accessible & simple, without lock-in
- We see Data Mesh as a natural, formalisation of building the Central Nervous System (CNS) (everything via streams of topic data)
- CNS has existed for many years and implemented by some of the largest organisations in the world
- CNS focuses on streams-of-events (Kafka topics), but during implementation includes most of the guiding principles of Data mesh (ownership by domain, as-a-product, self-service, governance)
- We should strive to avoid vendor lock-in (doesn't need to be all encompassing and conflict with existing data infra)
- Most Data Mesh solutions don't provide SDLC/development tools for test and infrastructure. Data-Ops and Testing is the last thing vendors consider. 

### What
- [Specifications](https://www.asyncapi.com/) are used to define the data-product, the domain model and drive resource provisioning; they are the sharing contract with the org.
- Data resources should only include Streams (realtime events i.e. Apache Kafka topics) and Storage (i.e. AWS S3). Because not everything fits in a stream.
- Each product repository (set of services) will contain a [Specification](https://www.asyncapi.com/docs/reference/specification/v2.4.0) that specifies the data resources to publish/write and subscribe/read.
- Provisioning of data resources (data-ops) via build-plugin + specifications fixes the Kafka resource mess/grave-yard. Resources have clearly identified ownership through the use of the *root.id* attribute. (Terraform)
- Testing support. SpecMesh includes full developer SDLC through Gradle (Java) and PyTest (Python). Unlike most products, this includes UnitTesting, localised, data resource provisioning (TestContainers) as well as during build-pipeline execution. DataOps and testing should be automated!
- Repeatability -> provides guard-rails, reuse, reliable, simple and consistent approach for all
- Specifications are published to a searchable Off-The-Shelf (OTS) Data Catalogue and automation plugins are used to incorporate self-service governance and access control. 
- Specification tags are injected into the associated environments Data Catalogue when the spec is promoted through the build pipeline, to aid discoverability. 
- - Not just Kafka and Storage, but eventually Kinesis, G PubSub, EventHubs, S3, from OnPrem to Cloud, multiple envs, clusters etc

### Data Mesh Principle Mapping
- Domain ownership is captured using the [ID](https://www.asyncapi.com/docs/reference/specification/v2.4.0#A2SIdString) of the spec (i.e. id: 'urn:example:com:smartylighting:streetlights:server')
- Data as a product is reflected by the Spec itself, the spec is used to provision resources (example) (more later)
- Data available everywhere (discoverable) - built using existing tools such as AWS Glue Data Catalogue, Collibra and others
- Data governed everywhere - using streams and storage we build a integration to the data catalogue, and integrate access requests through the use of private, protected, public topics & storage while automating restrictive controls (i.e. ACLs in Kafka, principle mapping etc). 


### How To Contribute
To become part of the community you can create a GitIssue (feature request or other) and tag any of the committers to start a conversation. If you see an existing feature then do a '+1' or thumbs up to see its progress.  
