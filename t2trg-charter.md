# Thing-to-Thing Research Group (T2TRG)

The Thing-to-Thing Research Group (T2TRG) will investigate open
research issues in turning a true "Internet of Things" into reality,
an Internet where low-resource nodes ("Things", "Constrained Nodes")
can communicate among themselves and with the wider Internet, in order
to partake in permissionless innovation.  The focus of the T2TRG will
be on issues that touch opportunities for standardization in the IETF,
i.e., it will start at the adaptation layer connecting devices to IP,
and end at the application layer with architectures and APIs for
communicating and making data and management functions (including
security functions) available.

## Motivation

A first wave of IoT standards has been completed by the IETF.
Consortia are now forming to build infrastructure and industry
agreements around those.  This generates new requirements for
research, based on actual usage of the standards now available.

In parallel, W3C has set up an IG (Interest Group) on the Web of
Things (WoT); this is operating on a similar timeline as an RG does in
the IETF.  A parallel activity associated with the IETF can help
ensure the common work does not stop at the traditional boundaries of
the W3C but considers networking issues as well; however, IETF WGs are
more short-term than is required here.

## Areas of Interest

A number of areas of interest have been identified:

- Understanding and managing the motivation for single-purpose silos
   and gateways; facilitating a move towards small pieces loosely
   joined (hence "thing-to-thing"); scaling the number of applications
   in a single network
- Deployment considerations; scaling considerations; cost of
   ownership
- Management and Operation of Things
- Lifecycle aspects (including, but not limited to, security
   considerations)
- Cooperation with W3C, e.g. on data formats and semantics

More explorative areas of interest include:

- Operating Things that have multiple masters/stakeholders (including
  understanding role definitions of devices, owners, operators etc.)
- Exploring the duality of state- and event-based approaches
- Aspects of distribution (cf. "fog computing"); reliability and
  scalability considerations
- Containerization and other forms of mobile code

## Other Objectives

Besides facilitating communication between researchers in its areas of
interest, T2TRG pursues a number of additional objectives:

* Definition of "Benchmark" or Reference Environments:
    - to enable regular plugfests, and
    - as a basis for repeatable, comparable research.

* Description of practical, real world, cross domain applications of
    connected Things

* Taxonomy, technology survey and best practice documents

* Fostering collaboration with industry fora and other organizations
  on networking of things

These objectives will be achieved making use of a close involvement
between the IETF community and the T2TRG.  For the IETF, some RG
documents may simplify the generation of (or even serve as) use case
documents or other informational references.  Close contact will be
maintained with the IETF's IoT-related WGs and its IoT directorate.

## Name, organization

The name Thing-to-Thing Research Group plays on a reminescence to the
End-to-End Research Group, which accompanied the evolution of the
Internet for its first three decades.  (The name is certainly not
intended to literally exclude the communication of constrained nodes
with the wider Internet or with more than one other constrained node.)

The charter of the E2E RG mentioned that "the specific topics of
interest to the E2E RG have changed as network research has advanced,
but it is generally concerned with end-to-end services and protocols
implemented in hosts" -- a focus similar to that of the T2TRG, except
that the concern for packet forwarding and network building is closer
to a constrained node than it was to a traditional Internet host.

Also, T2TRG will not be a closed RG, but employ an open membership
policy towards all interested researchers, taking its clues from the
way that, say, the DTNRG or the ICNRG have been and are being run.

## Meetings

Meetings will often take place colocated with IETF meetings, and/or
with meetings of related organizations such as W3C IG WoT.
(Organizing Workshops at Research Conferences is also envisioned.)

Specific meetings of T2TRG will pick focus items that much of the
discussion of the meeting should revolve around.  The stated focus for
the initial meetings was on three immediate areas of interest:

- Management and Operation of networks involving constrained nodes
- Security and Lifecycle aspects in constrained nodes
- REST and Pubsub: Exploring the state-event duality

## Milestones

Initially, T2TRG will work on the following work items:

* Documents
    * Guidance for designing REST-based IoT applications ("cookbook")
    * Security considerations for the IoT
    * A Survey of Security Bootstrapping Approaches
* Activities
    * Preparing and running "plugRESTs" (with support from the
      documents above, in cooperation with W3C IG WoT; preparing work
      on reference and evaluation frameworks), eventually leading to:

           * plugRESTs: lessons learned

