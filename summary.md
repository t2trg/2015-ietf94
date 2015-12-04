# Joint W3C IG WoT/Thing-to-Thing PRG Minutes --- Summary

More detailed minutes are at:
https://github.com/t2trg/2015-ietf94/blob/master/minutes.md
(thanks to all the notetakers!)

Slides are at:
https://github.com/t2trg/2015-ietf94/tree/master/slides

## SATURDAY, October 31, 2015

### 0914-0943 10 Welcome (Carsten)
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/00-t2trg-94-welcome.pdf

- Summary of the focus of the proposed RG and W3C WoT IG introduction

Discussion:

* Are "things" always physical, or do we include virtual proxies/abstract services?
* What specifically is the "scaling down" about?

### 0943-1007 Report from W3C IG WoT meeting (Joerg)
Slides: [TBD]

- Motivation to launch W3C WoT IG; work so far

### 1007-1026 WoT Thing Description (TD) (Sebastian Käbisch)
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/10b-w3c_td_overview.pdf

- Motivation (who, what data/function, how to access)
- Metadata, Properties, Actions
- JSON-LD

### 1026-1030 Report from W3C IG WoT meeting (Joerg, continued)

- WoT Building Blocks ("BB") (API and bindings, discovery, security)

### 1032-1102 Federated Multi-Tenant Service Arch for the IoT (Herb Wildfeuer)
Draft: https://tools.ietf.org/html/draft-burgess-promise-iot-arch-00.txt <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/11-prez14.pdf

- Overview (see draft abstract)
- Things as Service Entitites
- Multi-tenancy (promise theory), Scale, Workspaces

Discussion:

* boundaries of containers, workspaces
* workspaces, context, and trust

### 1120-1230 12 Ari Keränen: REST for IoT
Draft: https://tools.ietf.org/html/draft-keranen-t2trg-rest-iot-00 <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/12-ietf94_t2trg-rest-iot-00.pdf

- Goals, Background, Status

Discussion:

* term "application state" has a well-defined meaning in REST, but is
  problematic in a wider context
* term "session" (vs. resource state)
* more focus on "physical state" needed
* REST: where do we need to bend it?
* target state vs. actual state; long-running actions; impact of
  sleeping (➔ eventual consistency)
* URIs vs. transport (and security) alternatives
* operations on multiple (and collections of) resources
* Best practices for caches
* Methods: HTTP SEARCH, CoAP Proposals for FETCH, PATCH, iPATCH

### 1230-1314 13 John Mattsson: Actuator Security
Draft: https://tools.ietf.org/html/draft-mattsson-core-coap-actuators-00.txt <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/13-IETF-94-T2TPRG-Controlling-Actuators-and-Cyberphysical-Systems.pdf

- Relevant for both CoAPS (CoAP over DTLS) and End-to-end security
  over middleboxes (object security, COSE), as well as IPsec; these
  don't address the below attacks
- Attacks: (on-path protocol attacks: block attack, delay attack;
  mismatch attack (exploiting implementation errors around tokens))
- One solution: Repeat option (challenge-response mechanism for CoAP)
- Need to think more about security in Cyber-Physical Systems, how
  physical aspects may enable attacks
- Existing application-level solutions in used in the Web, but maybe
  cannot leave all this  to the application developer.

### 1430-1449 14 Jayaraghavendran K
Draft: https://tools.ietf.org/html/draft-vasu-core-ace-service-provisioning <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/14-Service-Provisioning-for-Constrained-Devices.pdf

- Motivation (RD does not provide service provisioning)
- Key idea (pre-configured users), Scenarios, Resource Control

Discussion:

* Relation/delta to other work in the ACE working group?
  (Jay: This is one approach; there are currently multiple competing approaches in ACE)
* Role of this proposal: a framework to plug in.
* Cf. configuration servers in data centers
* Link relations in the solution?

### 1449-1502 Security Considerations for the IoT -- something T2TRG wants to pick up? (Carsten)
Drafts:

- https://tools.ietf.org/html/draft-garcia-core-security-06
- https://tools.ietf.org/html/draft-he-iot-security-bootstrapping-01
- notes in
  https://www.ietf.org/mail-archive/web/ace/current/msg01470.html and
  https://www.ietf.org/mail-archive/web/secdir/current/msg06101.html

Discussion:

* Is the information still valid?
* Good basis for further RG work
* Look for editors and turn them into RG documents
* Good for reference in security sections of IETF documents

### 1502-1516 Problems in and among industries for the prompt realization of IoT (Yoshiki Ishida)
Draft: https://tools.ietf.org/html/draft-baba-iot-problems <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/15-Challenges-in-and-among-industries-for-the-prompt-IoT.pdf

* Study about challenges in ICT vs Things industry; interviewed major
  players
* Presented a few highlights (see slides)

Discussion:

* Document useful as input / check list

### 1516-1520 ... splitting into breakouts

- 11 REST breakout participants (room 304)
- 8 Security breakout participants (room 513)

- Dinner at 1930 (Kazuyuki)

### 1520-1830 Breakouts (rooms 304 and 513)

* See end of https://github.com/t2trg/2015-ietf94/blob/master/minutes.md for REST breakout
* See https://github.com/t2trg/2015-ietf94/blob/master/t2trg-b.mkd for Security breakout

## SUNDAY, November 1, 2015

### 0900-0930 Reports from breakouts

Summaries were given from REST and Security breakouts.

Discussion:

* Include automotive? Maybe not the focus, but a use case
* Some discussion about W3C/IRTF collaboration in the presence of
  differences in process and openness; strong desire to continue to
  collaborate

### 1000-1026 Alexander Pelov: COOL update
Draft out now: https://tools.ietf.org/html/draft-veillette-core-cool-00 <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/16-ietf94-cool-presentation-short.pdf

- Motivation: manage constrained nodes similar to classic nodes, YANG model
- CoOL approach:  from hashes to managed idenfifiers, resource architecture, Fields option

Discussion centered around the various IETF approaches to management
(SNMP, NETCONF, YANG, ...).

### 1026-1045 Carsten Bormann: FETCH draft
Draft: https://tools.ietf.org/html/draft-bormann-core-coap-fetch-00 <br/>
Slides: https://github.com/t2trg/2015-ietf94/raw/master/slides/17-fetch.pdf

- GET vs. POST in HTTP Web: switch to POST when query gets big
- HTTP SEARCH as proper fix: like GET but with body
- CoAP FETCH similar to SEARCH, cacheable (cache key includes request payload)
- Request payload has a content format (can be application-specific)
- Cannot construct request from just a link: need forms to tell clients how
- FETCH would go with PATCH to alter resource state
- Build prototypes to see if this works

Discussion:

* Do FETCH and (i)PATCH obsolete the other methods? (Not really.)
* How does client know what Content Formats server knows? (cf. form relations)
* defined mapping between GET and FETCH? (e.g., using www-form-urlencoded)

### 1100-1200 RG next steps (all)

- Charter
- Deliverables
   - REST cookbook (draft-keranen-t2trg-iot)
   - REST link, form types (draft-hartke-core-apps)
   - Security considerations (from draft-garcia-core-security)
   - Bootstrapping survey (from draft-he-iot-security-bootstrapping)
   - plugREST
      - Documents (reference framework, prototype formats/protocols, draft-hartke-core-lighting)
      - Software
- Milestones
   - Joint meeting in France, January 25/26th (EURECOM)

### 1300-1500 (breakout discussions, continued)


## WEDNESDAY, November 4, 2015

### 1030-1130 Report to the IETF

1030 Welcome (Carsten); Slides: https://www.ietf.org/proceedings/94/slides/slides-94-t2trg-0.pdf

- Summary of the focus of the RG
- Around 1/3 of the participants have been at the T2TRg meeting in Prague IETF93

- Overview of the W3C IG WoT
  - Just an example of what's going on there
  - First wave of IoT standards, IoT consortia now forming to build
    infrastrucutre and industry agreements around those

- One of the questions: Why are we having these silos (devices, gateways)
  - There are commercial reasons, but there are (may be?) also technical difficulties
  - Several major considerations
    - SCALING is one of them - SCALING up, but also SCALING down (to constrained devices)
    - MANAGEMENT and operation of things
    - Lifecycle aspects (security, also what happens at the end of life of a device, etc.)
    - Data formats, semantics, etc. - here are some IETF-specific
      things to be proposed, also conjoint work with W3C
  - Operating things that have multiple masters/stakeholders

- What solutions we have?
  - Looking at web-based principles, e.g. state- (REST) and event- (actions) based approaches
    - A form of duality exists between the two
  - Aspects of distribution - there may be lots of resources, but how
    do you access them, distribute them, etc. (notons of "fog
    computing")

- Definition of "benchmark" or reference environments
  - It is difficult to talk about comparing results if we don't have
    these reference environments
  - Useful for plugfests AND research purposes
- Description of existing/realistic applications (practical, cross-domain, real-world)

- Relationship to IETF WGs
  - There are 8 WG that work on related issues
  - The goal is not to replicate what's going at the IETF
    - T2Trg will of course integrate the concepts developed in these
      WG, and potentially give feedback
    - On the long run it could be possible that the T2Trg becomes an IETF WG

- Relationship to IAB
  - Very useful past workshops
    - Smart Objects, Security
  - Next year there will be a very useful workshop on Semantic Interoperability

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
    - There is still misunderstanding/confusion and the "Security
      consideration" section in RFCs needs some help

  Question: Do you consider that official RFCs should reference a
  document from a RG? <br/>
  Cabo: this will be a guidelines document; security considerations
  typically are not normative and can benefit from referencing it

  - Another document: security bootstrapping approaches
    - starting from draft-he-6lo-analysis-iot-sboostrapping-OO
    - identified main contributors, but more are needed. If you are willing to contribute, please step forward

- Planned next meetings
  - Jan 25++: Joint meeting with W3C (France)
  - possibly contribute to IAB workshop on semantic interop
  - possibly join Apr 12-14 W3C IG WoT
  - July: @IETF96
  - August: Worshop at research conference?

#### Discussion

  Kevin Fall: on one of your first slide (constrained nodes, devices),
  maybe the ship has sailed there. However there are many other
  devices, such as Industrial Internet, which may not be that
  constrained, but that have some special requirements (real-time
  comms). Would this be of interest for the charter?

  Cabo: It is possible. We don't want to do another Car-to-car
  comm. The "Thing" is the important part here

  Kevin: What is the "thingness" here? Is the constrained-ness a significant part?

  Cabo: That's a good point.

  Andrew: Now I'm confused. What Kevin was asking - you have this
  definition constrained-*. Now we say - ok, it's true that some of
  the things are not constrained... So now we ask - then this is
  networking?

  Kevin: Not that I try to advice you. In 2000 we had sensor
  networks. And as one years go to the next, devices become less and
  less constrained. It should be clear that if the choice is to say
  "constrainedness" is the essence of "Thing", this will lead to a
  given path, as opposed to real-time

  Cabo: The number of transistors is not the only thing. The
  reachability (always on) and some other

  Andrew: It seems that the risk here is to lose focus. The value to
  say - you've got these things and limit to them.. (?). ...

  Cullen: Security provisioning, bootstrapping, etc. is a very
  specific problem, e.g. Smart Meters have the same problems (and are
  not constrained). It is a very broad issue covering everything that
  we've seen until now. I'd see something specific in the charter -
  this specific problem to solve.

  Lars: The charters of IRTF are more different than IETF. IRTF is
  like an advertisement to research community. I wouldn't like to see
  something that is tightly constrained. I'd like to see something
  that is more open, and the IRTF gives the chair the choice to
  restrict the discussins, but the goal is not to recharter after
  this.

  Andrew: I agree. We've seen RG that have a too-broad scope for
  people to focus. People spend too much time arguing what is the
  problem.

  Lars: In the IETF the chairs use the charter to eliminate arguments
  which are off-scope. In IRTF, we rely on chairs to say - at this
  point, the group is more focused on this item.

  Andrew: again, I agree. The thing is, if anyone can say 'oh yes,
  that's a problem too'. So we must agree on which are the interesting
  problems

  Lars: correct

  Kevin Fall: The idea that this is an advertisment is on the
  point. If I have a researcher doing real-time controller/automation,
  can I advertise to him/her? Here we see "constrained" on the first
  line. I'd like to see "things that interact with the real-world
  (real-time?), and may be constrained". This way we don't redo 15
  years of work.

  Cabo: ...

  Cabo: Any other ideas

  (?): Are there any concrete plans to .. something with ICN. There
  are some specific problems with naming

  Cabo: Yes, there are some common things

  Jorg Ott: I agree with Lars' suggestion. The RG should be
  contribution-driven. If we have some controller devices that move
  some monster things, then OK. It should be inclusive rather than
  exclusive

  Ari: I think that we have the opened scope to begin with. So far
  everything has worked great, and I like this approcah.

  Cabo: I agree that probably we may make the reference to "physical systems" more visible

  Mathias: To give input from someone that has been active. For me it
  was quite clear the goal of this RG. As someone from IoT, moving to
  Cyberphycial systems, etc. for me it was quite clear. It is
  something connected to a "thing", which is constrained. Usually we
  look at architectures. We don't want to work on specific
  applications, but on architectures.

  Lars: The group is very active, let me know when you have text. I
  expect it to be chartered soon.
