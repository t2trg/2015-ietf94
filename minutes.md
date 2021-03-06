# Joint W3C IG WoT/Thing-to-Thing PRG Minutes

## SATURDAY, October 31, 2015

### 0914-0943 10 Welcome (Carsten)
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/00-t2trg-94-welcome.pdf

- Summary of the focus of the RG
- W3C WoT IG introduction
```
      Dave Raggett: Are things always physical?
      Carsten: IoT is about connecting physical devices to the Internet ("Internet with Things")
      Dave: WoT is also about abstract services
      Carsten: "Web Things" may refer to virtual proxies
```
- Areas of interest (REST, state/event duality, distribution, mobile code)

      Dave: Scalability not only about number of messages, but also communication patterns and their support by protocols

- Objectives (benchmark scenario, documentation of best practices, prepare work for IETF WGs
- IETF WGs (on IoT)
- Organization of the IRTF RG
- This meeting (topics, agenda)

### 0943-1007 Report from W3C IG WoT meeting (Joerg)
Slides: [TBD]

- Motivation to launch W3C WoT IG (convergence of silos, use cases)
- Work so far ("atmoic use cases", technical landscape: script API, discovery, description, security, not much existing work on actuation)
- WoT building blocks (framework emerging from the technical landscape)
- 1st Plug fest (10 implementations, many on NodeMCU and RaspPi, but also one for Cortex-M3)

### 1007-1026 WoT Thing Description (TD) (Sebastian Käbisch)
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/10b-w3c_td_overview.pdf

- Motivation (who, what data/function, how to access)
- Metadata (name, protocol, encoding)
- Properties (name, data type, R/RW)
- Actions (usually a process that takes a while)
- JSON-LD
- Implementations on GitHub (github.com/w3c/wot/tree/master/... waiting for slides) (e.g., TD Interpreter & Client)
- Bindings (TD to actual instance, ongoing work -> HATEOAS)
- W3C Breakout results (TD size, collaborate with Special Data (SDW) WG)
- Next (security considerations, more non-REST examples (TD is agnostic), more bindings)
```
      Daniel ???: TD JSON available on each device? Is there a standard way to get it from any object?
      Sebastian: Yes, but discovery still work in progress (e.g., latest version of TD).
      Carsten: Let's continue with details in breakout (this was overview)
```

- W3C Breakout results (TD size, collaborate with Special Data (SDW) WG)
- Next (security considerations, more non-REST examples (TD is agnostic), more bindings)
### 1026-1030 Report from W3C IG WoT meeting (Joerg, continued)

- WoT Building Blocks ("BB") (API and bindings, discovery, security)

      Daniel: mDNS is only link-local, would need DNS-SD for other cases

### 1032-1102 Federated Multi-Tenant Service Arch for the IoT (Herb Wildfeuer)
Draft: https://tools.ietf.org/html/draft-burgess-promise-iot-arch-00.txt <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/11-prez14.pdf

- Overview (see draft abstract)
- Things as Service Entitites, but tied to physical device (directly on smart thing, gateway with proprietary devices behind, gateway with sensors/actuators on board, transmitter?)
```
      Daniel Lux: Granularity is the thing? (ownership, control)
      Herb: Yes
```
- Multi-tenancy (promise theory)
- Scale (bottom-up appraoch is key, no centralization, but segmentation)
- Workspaces (separation of concerns for humans, more than namespaces -> containers and SDN virtual networks)

```
      Darshak: Can services run in multiple containers?
      Herb: Yes (?)
      Joerg: Workspace boundaries / partitioning are hard to define depending on the use case, e.g., might overlap in smart grid
      Herb: Depends on the grouping
      Daniel Lux: Example: In home automation you can share services of sensors (free or micro-payment)
      Herb: Yes, this concept is close to workspaces
      Carsten: Context is also a concept for separation of concern, so is bookmarks, social networks -- how do things become aware of other things?
      Herb: ??
      Dave: Adapting dynamically is important
      Daniel ???: SDN appears to be the opposite of (multi-tenancy?)
      Herb: Would like to see work on service-level architectures
      Darshak: Promise looks to be related to TD: what function and data to expect from a thing, right?
      Herb: ~yes
      Carsten: In security this is often referred to as "trust"
```

### 1120-1230 12 Ari Keränen: REST for IoT
Draft: https://tools.ietf.org/html/draft-keranen-t2trg-rest-iot-00 <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/12-ietf94_t2trg-rest-iot-00.pdf

- Goals of the document (guidance for designing IoT systems, terminology, executive summary)
- Background (usually differences in "REST as we use it" to what is documented in different sources)
- Status (20+ terms, some text, looking for contributions!)

```
      Darshak: Where ... (protocol bindings?)
      Ari: In the design patterns part
```

- Details (defined terms, roles of components in a system, application state, URIs (namespacing, semantics for query parameters), methods)

```
      Matthias: "application state" was a good example for conflicts in understanding and naming
      Jaime: I guess "Session" is not TCP or UDP session, we should try to avoid reusing terminology, right?
      Matthias: Please provide feedback on exactly such questions and how far specific term are already "occupied" in your community/peers. TODO: improve on "session" term
      Joerg: Also consider physical state that often has its own timing properties and extend the document that way.
      Alex Pelov: REST in the IoT is different from the Web, so the physical state aspect is something new that should be covered.
      Ari: REST is nice, but sometimes we need to bend it, maybe it is sometimes too much; we have to figure this out.
      Darshak: "session" vs "resource" state -- could be client and server view of a resource. [Note by Matthias: session state is more than just the view of a resource (representation)]
      Carsten: Consider notion of actions, targeted state and actual state from WoT IG.
      Dave: The classic model (Web of documents) does not fit well with sensors and actuators. Also think toward the upper level about systems and control.
      Johannes: At the W3C we also had a long discussion that exceeded the time frame. Important: How can we define differnt notions of state (application, actions, atomic way to change something on multiple components)
      Daniel Lux: What about sleepy nodes? Actions might be executed only after some time.
      Ari: Mechanisms should be in the design patterns. TODO: sleepy nodes, eventual consistency
      Darshak: Explain more about the URI namespaces. Even when to URIs map to the same resource, the secured version might be able to provide more information in its representations. What about multicast resources?
      Carsten: In the HTTP-world, switching to HTTPS is quite clear (on/off). In CoAP, there are more security levels that need to be handled somehow (coaps URI is not uniform due to the possible security mechanism). TODO: More details on coaps scheme and what it means.
      Ari: Please provide feedback on using query parameters for PUT/POST/DELETE
      Carsten: Queries define a different resource
      Ari: Is the order of query parameters important.
      Daniel ???: What should the semantic of a query be for DELETE, for instance? Usually we use HTTP definitions as common language to avoid redundancy. There should only be one way for an action to improve caching etc. TODO: discuss order of query parameters
      Carsten: Distinguish between rules required to make it work and make it efficient.
      Alex: We use queries to retrieve multiple resources as an optimization. How to do it correctly? We have a working draft that uses a special option to identify multiple resources at once.
      Ari: Collection resources are probably a good way to model this. TODO: deign pattern to optimize retrieval of multiple resources at once.
      Darshak: Best practices for caches: what and how to cache. Normalizing query order in a cache would help to improve cache hits.
      Ari: TODO: check if query order must be protected; do applications rely on specific orders to distinguish two different resources?
      Carsten: Cache is not allowed to modify URI
      Jaime: Unclear why different order should resolve to a different resource; CoRE interfaces says something about order.
      Ari: Might define an optimization rule that clients should normalize query parameters to optimize caching
      Casten: HTTP SEARCH method, FETCH method for CoAP, PATCH vs iPATCH -- we need to identify what methods we really need.
```

### 1230-1314 13 John Mattsson: https://tools.ietf.org/html/draft-mattsson-core-coap-actuators-00.txt
Slides:

- End-to-end security over middleboxes (object security, COSE)
- Attacks (on-path attacks, CoAP usually protected with DTLS or OS, block attack, delay attack, mismatch attack (token))
- Repeat option (challenge-response mechanism for CoAP)
- Security in Cyber-Physical Systems (physical aspects may enable attachs, how to tackle this? work for the RG)

```
      ???: Can you elaborate why the DTLS replay window is not effective?
      John: You can block every message, so that the expected seq.num. at the receiver is never increased. Depends on window size and number of messages sent by the client. Replay window allows a few out-of-order messages.
      Dave: Doesn't the MID enforce in-sequence delivery?
      Carsten: There is now sequencing in CoAP (MID needn't be sequenced; useful for memory optimization)
      John: Should be fixed on the CoAP-level
      Carsten: Tokens in CoAP only give same level of security as TCP gives you.
      John: What does "in use" mean for tokens? Is there a timeout? TODO: More text on tokens in lwig docuement.
      ???: Fix it in the application (?)
      John+Ari: Do not leave this to the application developer.
      John: We need to decide which properties we want and how to achieve them.
      Carsten: Applications using communication as indicator for proximity is a problem.
      Ari: Repeat option: Shouldn't being close enough to the server's timestamp be fine enough?
      Daniel Lux: Time is easily tampered with, e.g., DoS
      John: See next slide (16)
      Ari: IPSec has similar problems, there should be a solution available to adapt.
      Carsten: Probably nothing there. Most applications define their own mechanism for freshness.
      Jaime: (?) Communication pattern might tell something about the challenge-response (use exclusively for some types of actuators).

      Carsten: In the Web, usually applications implement mechanism such as challenge-response to resolve security issues. We might want to look at those.
```

### 1430-1449 14 jayaraghavendran ("not Vasu" ??? sorry)
Draft: https://tools.ietf.org/html/draft-vasu-core-ace-service-provisioning <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/14-Service-Provisioning-for-Constrained-Devices.pdf

- Motivation (RD does not provide service provisioning)
- Key idea (pre-configured users)
- Scenarios
- Resource Control

```
      Ari: Relation/delta to other work in the ACE working group?
      not Vasu: This is one approach; there are currently multiple competing approaches in ACE
      Carsten: Is it something everybody should use, a specific example, or something where others can plug in?
      not Vasu: The latter, a framework to plug in.
      Carsten: We saw similar things in data centers. We should look at the configuration servers there to get more insights.
      Carsten: You are aiming for link relations in the solution? Could became a nice small interface.
```

### 1449-1502 Security Considerations for the IoT -- something T2TRG wants to pick up? (Carsten)
Slides: [TBD]

- https://tools.ietf.org/html/draft-garcia-core-security-06 (information still valid? ...)
- https://tools.ietf.org/html/draft-he-iot-security-bootstrapping-01 (Mohit: The document provides a good initial overview of bootstrapping solutions available for IoT devices. This is useful for application developers making new services. The group should work on a document to overview such bootstrapping solutions including those not included in this document in a more structured fashion. Volunteer for editing the proposed new document.)
- http://www.ietf.org/mail-archive/web/ace/current/msg01470.html (main topic is software updates, fingerprinting, penetration testing)
- secdir review (https://www.ietf.org/mail-archive/web/secdir/current/msg06101.html)
- Look for an editor and turn it into a RG document (Mohit, "not Vasu", and Oliver Pfaff volunteered)
- Good for reference in security sections of IETF documents

### 1502-1516 Problems in and among industries for the prompt realization of IoT (Yoshiki Ishida)
Draft: https://tools.ietf.org/html/draft-baba-iot-problems <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/15-Challenges-in-and-among-industries-for-the-prompt-IoT.pdf

- Objectives (What are the challenges? ICT vs Things industry)
- Meeting (interviewed major players)
- Highlights (door security, acquired data withdrawn later due to privacy policy, configuration of IoT equipment too cumbersome, too many standards, which manufacturer is responsible in case of a system fault, openness requires new design process)
- Testbed for HEMS (Home Energy Management System) study

```
      Carsten: Document is useful as input / check list
```

### 1516-1520 ... preparing breakouts

- 11 REST breakout participants (room 304) (extra points: discuss proxy behavior also in regard to object security)
- 8 security breakout participants (room 513)

- Dinner at 1930 (Kazuyuki)

### 1520-1830 Breakouts (rooms 304 and 513)

- See end of page for REST breakout

## SUNDAY, November 1, 2015

### 0900-0930 Reports from breakouts

- Summary REST breakout
- Have PlugREST until December to make decision about joint meeting/testing in January
- Summary security breakout (https://github.com/t2trg/2015-ietf94/blob/master/t2trg-b.mkd)
- Unclear if there will be another breakout B today

```
      Kazuyuki: We should include automotive
      Carsten: Not the focus, but a use case
      Fluffy: Processes in W3C are different from IETF such as access to material/drafts, but keep trying to collaborate (?)
```

### 1000-1026 Alexander Pelov: COOL update
Draft out now: https://tools.ietf.org/html/draft-veillette-core-cool-00 <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/16-ietf94-cool-presentation-short.pdf

- Motivation (manage constrained nodes similar to classic nodes, YANG model)
- CoOL (hashes, resource arch, Fields option)

```
      Daniel Lux: What does module mean? Are 30 bits enough?
      Alex: groups in the data structure; yes
      Carsten: Numbered trees, close to SNMP, might be good for constrained devices; Problem: transition from SMI to YANG; want to follow that in constrained environmnets; YANG with XML and XPath not optimal -> CoMI -> CoOL? Useful for applications?
      Dave: Enterprise IDs to manage subrees, could become a burden to keep going back to the registry
```

### 1026-1045 Carsten Bormann: FETCH draft
Draft: https://tools.ietf.org/html/draft-bormann-core-coap-fetch-00 <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/17-fetch.pdf

- Queries can become very big, workaround: need to switch to POST, losing GET properties
- Web tends to use workaround
- HTTP SEARCH as proper fix: like GET but with body
- CoAP FETCH similar to SEARCH, cacheable (cache needs to look at request payload), payload has a content format (can be application-specific)
- Not just a link: need forms to tell clients how to construct request
- FETCH would go with PATCH to alter resource state
- Build prototypes to see if this works

```
      Alex: FETCH and PATCH might obsolete the other methods; (second point?)
      Carsten: Collections are different and one might want to PUT and DELETE at the same time. This is a special use case and justifies special method
      Robert: How would Accept work?
      Carsten: Server needs to understand Content Format of FETCH payload
      Johannes: How to map GET with query parameters to FETCH?
      Carsten: Complicated queries can for instance be www-form-urlencoded payload, there are ways of mapping
```

### 1100-1200 RG next steps (all)

- Charter
- Deliverables
   - REST cookbook (draft-keranen-t2trg-iot)
   - REST link, form types (draft-hartke-core-apps)
   - Security considerations
   - Bootstrapping survey
   - plugREST
      - Documents (reference framework, prototype formats/protocols, draft-hartke-core-lighting)
      - Software
- Milestones
   - Joint meeting in France, January 25/26th (EURECOM)




### 0930-1000 David Janes, IoTDB: Thing API (remote presentation)
### ....-....  "Bring your own resource"/"Operating Things that have multiple masters/stakeholders" [may need to reschedule]

### 1020-1200 Breakouts, reconfigured (rooms 304 and 513)

### 1300-1500 (plan based on breakout results)


## WEDNESDAY, November 4, 2015

### 1030-1130 Report to the IETF




## REST Breakout

### Agenda Items

- W3C and IRTF alignment
   - What is on the table regarding the W3C Plugfest?
   - What is relevant for the cookbook?
   - What are WoT Actions?
   - Is being paradigm-agnostic favorable? (REST, SOA, etc. bindings)
- Discuss cookbook
   - Collection resources (related to CoMI and COOL work, FETCH)
   - How to model RPC or operations (actions) in REST
   - HATEOAS (example of Lighting use case, form types) and relation to thing descriptions
   - Event handling
   - (Transparent?) translating proxies (e.g., JSON <-> CBOR); seamless IoT - Web
- PlugREST

### W3C and IRTF Alignment

#### W3C Plugfest

- Tested Thing Description (TD)
- Specification was a bit late for a meeting in Sunnydale
- Pre-testing is important: have test instances online
   - Hosting machines might be required
   - Usually the "passive" component is set up on a public server by the implementers and its address announced
   - "Active" component is run locally
   - Test specification needs to define the entry point and steps
- Main goal was an API easily understandable by humans; this worked out well (self-describing interface through TD)
- Next step: machine-understandable

- Formal testing for IPv6 helped to do autonomous testing
   - Tests specified as RFC
   - Was with a stable specification
   - See https://rawgit.com/cabo/td-coap4/master/base.html for the CoAP Plugtest
   - Let's try to agree on common mechanisms for testing for WoT and T2TRG so that it's eventually easy to run tests together

- TD has a tutorial, which was very useful for the Plugfest preparation
- Where there insights on design decisions?
   - Specific to TD and model (e.g., atomic actions, relative change)

#### What are Actions?

- Short-running: POST + action result
- Long-running: POST + new resource as handle with a status representation, is deletable to cancel
- Mechanism is generic, not application-specific. New resource contains e.g., start time, end time, parameters, etc.

- Also interesting for management

#### Events

- Attribute about frequency of change, so clients know what to expect
- Mapping to CoAP observe
- pmin, pmax in core-interfaces
- Events are also used for bindings to sync two resources

#### Is being paradigm-agnostic favorable? (REST, SOA, etc. bindings)

- Use the abstract concept and then bind to protocols (e.g., either CoAP observe or HTTP something)
- Could fail to scale since you need very specific models (e.g., targeted state, current state) and it is hard to hide details (Layered System)
- TD is still very easy and was good to implement a REST-based system
- Need to see how TD works for non-REST systems -- could become difficult
- Incentive is to understand what is in-scope and what out-of-scope, can people map TD/REST-appraoch to their non-REST system
- TD ties to REST by defining the capabilities through properties/resources and state transfer
- Core Interfaces (current version AFAIK): https://github.com/mjkoster/I-D/blob/master/CoRE%20Interfaces/draft-ietf-core-interfaces-04.pdf
- Separation between Data Model and Semantics and the application protocols (CoAP, MQTT...). For this group, focus on REST.

### Discuss cookbook

- TD vs hypermedia controls
- Does crawling a RESTful thing result in the TD?
- TD more like the entry points
- TD good to describe offered services, but model of these services must be programmed into the clinet
- HATEOAS on T2TRG document???? (are you looking for http://tools.ietf.org/html/draft-hartke-core-apps ?) Yes, let's put it as reference somewhere please.
- TD and hypermedia controls are close, but we need to figure out how to translate and identify white spots

#### Collection Resources in the Context of CoMI

Question: should we have compatible "IoT" and "web" worlds or is it okay to have app/domain specific proxies?

- Summary of CoOL (new concept: complex query encoded as CBOR-encoded "Field" option)
- We should aim for compatibility; but we could be able to translate these two in a generic way
- CBOR does not have to be translated to JSON
- CBOR is still application-agnostic (no domain knowledge)
- CoAP FETCH in combination with HTTP SEARCH is an option
- Importance of idempotency might be decision maker

### PlugREST

- Discuss with interested parties to get started: Johannes, Jaime, Klaus, Matthias, Michael.
- Take lessons learned from WoT Plugfest and ETSI Plugtests
- Take lessons from IPSO/LWM2M interop
- Finish preparation and run PlugREST within T2TRG
- Extend with WoT TD and try to integrate with WoT Plugfest
- Appears that thing description can be seen as a result of exploring HATEOAS links of system / device
- The two models are very close to each other, see how one maps to other
- Need to explore practical use cases to see how close they are
- Contiunue discussions between meetings to avoid diverging
- Interim definitely before the next IETF -- joint meeting end of January in France?


---

Breakout #2: REST

* Methods
 - what to return in responses beyond GET

 - PUT
    -
 - POST: two options: 1) action result (cf representations), 2) if resource state created/updated: 205 with link in headers 3) action result with a link

  - horizontal media types with links in IoT context would be useful.
    - often needs domain specific information

 - when getting value would like to get also links for the actions to do on that resource; what should be the media type?
 - can use relation types or media type negotation to find out what is possible; now figuring out what works better with the plugrest exercise
 - issues e.g., with PUT that's suppose to replace the whole representation
   - also issues with optional options
 - e.g. HAL helps here but what should be the media type? hal+json. In the payload data type that supports schema links
 - Need more experience from plugREST

 - the size of the payloads can be arbitrary large. Should recommend ways to keep reasonable.
 - useful to have "reverse PATCH" to get only the changed parts with e.g., observe
 - would be it safe to assume I have sub-resources for all parts of a resource?
 - need to evaluate different approaches

 - it is dangerous to assume anything from the structure of the Path
 - URI templates and forms might be a solution for this discovering what is the right path structure
 - need to learn from the server and should not be assumed by the client

 - want to be able to have either state and links or only one of them; WoT solution: add information to the path (upper level in path hierarchy has links)

 - when implementing plugREST; keep in mind the re-usable parts and make note of them

 - graceful evolution for API design; how to add parameters without breaking backward compatibility for example

 - how to follow links that are discovered. How the metadata about the links is encoded and decided.

 - having fully automated discovery of funcionality and mapping that together may be long term goal but right now we don't seem to have the tools for it
 - need to incrase learning based on the exercise
 - what are the tools we have now? CoRE apps draft, RESTful design draft.




* Design patterns



* PlugFEST/REST practicalities
 - Code from Johannes et al for w3c plugfest. Mapped against abstract model. Protocol handlers for CoAP & HTTP. Demonstrators for service side (RPi with LED) and Thing Description. More interesting might be base components. All code in github: https://github.com/thingweb/thingweb
 - Interesting classes to start from: ContentHelper (/util/encoding/ContentHelper.java) and Launcher.java
 - each subproject ends up in a .jar
 - Johannes will write a bit of README to help others get started



## WEDNESDAY, November 4th, 2015

### 1030 Welcome (Carsten)
Slides: https://www.ietf.org/proceedings/94/slides/slides-94-t2trg-0.pdf

- Summary of the focus of the RG
- Around 1/3 of the participants have been at the T2TRg meeting in Prague IETF93

- Overview of the W3C IG WoT
  - Just an example of what's going on there
  - Frst wave of IoT standards, IoT consortia now forming to build infrastrucutre and industry agreements around those

- One of the questions: Why are we having these silos (devices, gateways)
  - There are commercial reasons, but there are (may be?) also technical difficulties
  - Several major considerations
    - SCALING is one of them - SCALING up, but also SCALING down (to constrained devices)
    - MANAGEMENT and operation of things
    - Lifecycle aspects (security, also what happens at the end of life of a device, etc.)
    - Data formats, semantics, etc. - here are some IETF-specific things to be proposed, also conjoint work with W3C
  - Operating things that have multiple masters/stakeholders

- What solutions we have?
  - Looking at web-based principles, e.g. state- (REST) and event- (actions) based approaches
    - A form of duality exists between the two
  - Aspects of distribtion - there may be lots of resources, but how do you access them, distribute them, etc. (notons of "fog computing")

- Definition of "benchmark" or reference environments
  - It is difficult to talk about comparing results if we don't have these reference environments
  - Useful for plugfests AND research purposes
- Description of existing/realistic applications (practical, cross-domain, real-world)

- Relationship to IETF WGs
  - There are 8 WG that work on related issues
  - The goal is not to replicate what's going at the IETF
    - T2Trg will of course integrate the concepts developed in these WG, and potentially give feedback
    - On the long run it could be possible that the T2Trg becomes an IETF WG

- Relationship to IAB
  - Very useful past workshops
    - Security
  - Next year there will be a very useful workshop on semanthic operability (?)Semantic Interoperability

- Naming and organization of the RG
  - Thing-to-thing is a homage to "end-to-end" RG - and does not exclude device-to-cloud models
  - open-membership RG (emulate DTNRG, ICNRG)
  - Regular plugfests, open-source toole, etc.

- Meetings until now
  - First meeting happened in Dallas
    - Identified the main areas of interest: applied REST, management protocols, security
  - Second meeting in Prague @IETF93
    - First joint meeting with W3C IG WoT
  - Third meeting - Halloween meeting @IETF94
    - Joint meeting with W3C
      - (A) "REST as we know it" -> "Beyond REST"
      - (B) Security and Lifecycle aspects of constrained devices
    - Agenda split in talks + breakouts (A) and (B)

- Breakout (A)
  - Two deliverables:
    - Cookbook: "RESTful Design for IoT Systems"
              - design patterns, resource design, etc.
              - work document: draft-keranen-t2trg-rest-iot (1st version)
            - "plugRESTs: lessons learned"
              - scenario document
              - describes ways to develop hypertext-driven applications
              - work document: draft-hartke-core-{apps,lighting}
  - W3C & T2TRG work
    - W3C WoT IG has 3 task forces: Thing description, discovery, API and protocols
    - T2TRG: RESTful hypertext driven apps
    - Sharing experiences and code, github to work on common documents
    - Next joint plugfest/REST planned for January in southern France
  - Topics discusssed
    - Appllication state
    - (long running) actions with REST - how do you do this?
    - links, partioal changes for resources
      - "collections" is a term that comes up oftne
    - we think we know how to do this, but it helps to build a system like this and document it
    - Learning from scenarios and plugRESTs

- Track B - security
  - Ongoing work on challenges, requirements, landscape of means
  - Security considerations for IoT
    - starting the work from draft-garcia-core-security-06
  - Identified main constributors: Sandeep Kuar, Mohit Sethi, Jayarghavendran K, Oliver Pfaff
  - A book was cited, but it is quite big
    - Produce a document which is more succsicnt (?)
  - Cover lifecycle, ownershop, stakeholdes
  - Recent IESG comments
    - There is still misunderstanding/confusion and the "Security consideration" section in RFCs needs some help

  Question: Do you consider that official RFCs should reference a document from a RG?
  Cabo: this will be a guidelines document, ... (?)

  - Another document: security bootstrapping approaches
    - starting from draft-he-6lo-analysis-iot-sboostrapping-OO
    - identified main contributors, but more are needed. If you are willing to contribute, please step forward

- Planned next meetings
  - Jan 25++: Joint meeting with W3C (France)
  - possibly contribute to IAB workshop on semantic interop
  - possibly join Apr 12-14 W3C IG WoT
  - July: @IETF96
  - August: Worshop at research conference?

  Kevin Fall: on one of your first slide (constrained nodes, devices), maybe the ship has sailed there. However there are many other devices, such as Industrial Internet, which may not be that constrained, but that have some special requirements (real-time comms). Would this be of interest for the charter?
  Cabo: It is possible. We don't want to do another Car-to-car comm. The "Thing" is the important part here
  Kevin: What is the "thingness" here? Is the constrained-ness a significant part?
  Cabo: That's a good point.

  Andrew: Now I'm confused. What Kevin was asking - you have this definition constrained-*. Now we say - ok, it's true that some of the things are not constrained... So now we ask - then this is networking?
  Kevin: Not that I try to advice you. In 2000 we had sensor networks. And as one years go to the next, devices become less and less constrained. It should be clear that if the choice is to say "constrainnness" is the essence of "Thing", this will lead to a given path, as opposed to real-time
  Cabo: The number of transistors is not the only thing. The reachability (always on) and some other
  Andrew: It seems that the risk here is to loose focus. The value to say - you've got these things and limit to them.. (?). ...
  Cullen: Security provisioning, bootstrapping, etc. is a very specific problem, e.g. Smart Meters have the same problems (and are not constrained). It is a very broad issue covering everything that we've seen until now. I'd see something specific in the charter - this specific problem to solve.
  Lars: The charters of IRTF are more different than IETF. IRTF is like an advertisement to research community. I wouldn't like to see something that is tightly constrained. I'd like to see something that is more open, and the IRTF gives the chair the choice to restrict the discussins, but the goal is not to recharter after this.
  Andrew: I agree. We've seen RG that have a too-broad scope for people to focus. People spend too much time arguing what is the problmem.
  Lars: In the IETF the chairs use the charter to eliminate arguments which are off-scope. In IRTF, we rely on chairs to say - at this point, the group is more focused on this item.
  Andrew: again, I agree. The thing is, if anyone can say 'oh yes, that's a problem too'. So we must agree on which are the interesting problems
  Lars: correct
  Kevin Fall: The idea that this is an advertisment is on the point. If I have a researcher doing real-time controller/automation, can I advertise to him/her? Here we see "constrained" on the first line. I'd like to see "things that interact with the real-world (real-time?), and may be constrained". This way we don't redo 15 years of work.
  Cabo: ...
  Cabo: Any other ideas
  xxx: Are there any concrete plans to .. something with ICN. There are some specific problems with naming
  Cabo: Yes, there are some common things
  Jorg Ott: I agree with Lars' suggestion. The RG should be contribution-driven. If we have some controller devices that move some monster things, then OK. It should be inclusive rather than exclusive
  Ari: I think that we have the opened scope to begin with. So far everything has worked great, and I like this approcah.
  Cabo: I agree that probably we may make the reference to "physical systems" more visible
  Mathias: To give input from someone that has been active. For me it was quite clear the goal of this RG. As someone from IoT, moving to Cyberphycial systems, etc. for me it was quite clear. It is something connected to a "thing", which is constrained. Usually we look at architectures. We don't want to work on specific applications, but on architectures.
  Lars: The group is very active, let me know when you have text. I expect it to be chartered soon.
  Cabo: I'm afraid we won't have time to do this today.
