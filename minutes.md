# Joint W3C IG WoT/Thing-to-Thing PRG Minutes

## SATURDAY, October 31, 2015

### 0914-0943 10 Welcome (Carsten)
Slides: https://github.com/t2trg/2015-ietf94/blob/master/slides/00-t2trg-94-welcome.pdf

- Summary of the focus of the RG
- W3C WoT IG introduction

      Dave Raggett: Are things always physical?
      Carsten: IoT is about connecting physical devices to the Internet ("Internet with Things")
      Dave: WoT is also about abstract services
      Carsten: "Web Things" may refer to virtual proxies

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

      Daniel ???: TD JSON available on each device? Is there a standard way to get it from any object?
      Sebastian: Yes, but discovery still work in progress (e.g., latest version of TD).
      Carsten: Let's continue with details in breakout (this was overview)

### 1026-1030 Report from W3C IG WoT meeting (Joerg, continued)

- WoT Building Blocks ("BB") (API and bindings, discovery, security)

      Daniel: mDNS is only link-local, would need DNS-SD for other cases

### 1032-10__ Federated Multi-Tenant Service Arch for the IoT (Herb Wildfeuer)
Draft: https://tools.ietf.org/html/draft-burgess-promise-iot-arch-00.txt <br/>
Slides: [TBD]

- Overview (see draft abstract)
- Things as Service Entitites, but tied to physical device (directly on smart thing, gateway with proprietary devices behind, gateway with sensors/actuators on board, transmitter?)

### 1000-1045 12 Ari Keränen: https://tools.ietf.org/html/draft-keranen-t2trg-rest-iot-00
### 1100-1130 13 John Mattsson: https://tools.ietf.org/html/draft-mattsson-core-coap-actuators-00.txt
### 1130-1200 14 jayaraghavendran K: https://tools.ietf.org/html/draft-vasu-core-ace-service-provisioning
### 1300-1315 Carsten Bormann: Security Considerations for the IoT -- something T2TRG wants to pick up? (https://tools.ietf.org/html/draft-garcia-core-security-06.txt)
### 1315-1330+ (space for an additional discussion point such as on W3C outcome)
### 1330-1400 Yoshiki Ishida: https://tools.ietf.org/html/draft-baba-iot-problems
### 1400-1420 ... preparing breakouts

### 1420-1800 Breakouts (rooms 304 and 513)

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

