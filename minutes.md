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
Slides: [TBD]

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

### 1026-1030 Report from W3C IG WoT meeting (Joerg, continued)

- WoT Building Blocks ("BB") (API and bindings, discovery, security)

      Daniel: mDNS is only link-local, would need DNS-SD for other cases

### 1032-1102 Federated Multi-Tenant Service Arch for the IoT (Herb Wildfeuer)
Draft: https://tools.ietf.org/html/draft-burgess-promise-iot-arch-00.txt <br/>
Slides: [TBD]

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

### 1120-1230 12 Ari Keränen: https://tools.ietf.org/html/draft-keranen-t2trg-rest-iot-00
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
      Jamie: Is "session" the TCP session?
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
      Jamie: Unclear why different order should resolve to a different resource; CoRE interfaces says something about order.
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
      Jamie: (?) Communication pattern might tell something about the challenge-response
      
      Carsten: In the Web, usually applications implement mechanism such as challenge-response to resolve security issues. We might want to look at those.
```

### 1345-1415 14 jayaraghavendran K: https://tools.ietf.org/html/draft-vasu-core-ace-service-provisioning
### 1415-1430 Carsten Bormann: Security Considerations for the IoT -- something T2TRG wants to pick up? (https://tools.ietf.org/html/draft-garcia-core-security-06.txt)
### 1430-1500 Yoshiki Ishida: https://tools.ietf.org/html/draft-baba-iot-problems
### 1500-1520 ... preparing breakouts

### 1520-1830 Breakouts (rooms 304 and 513)

## SUNDAY, November 1, 2015

### 0900-0930 Reports from breakouts
### 0930-1000 David Janes, IoTDB: Thing API (remote presentation)
### 1000-1020 Alexander Pelov: COOL update, Carsten Bormann: FETCH draft
### ....-....  "Bring your own resource"/"Operating Things that have multiple masters/stakeholders" [may need to reschedule]

### 1020-1200 Breakouts, reconfigured (rooms 304 and 513)

### 1300-1500 (plan based on breakout results)
### 1500-1600 RG next steps (all)

## WEDNESDAY, November 4, 2015

### 1030-1130 Report to the IETF

