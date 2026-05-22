---
coding: utf-8

title: "Privacy Considerations for the Discovery of Agents, Workloads, and Named Entities (DAWN)"
abbrev: "DAWN Privacy"
docname: draft-iannone-dawn-privacy-considerations-00
category: info
stream: IETF
area: Internet
#workgroup: DAWN Working Group
keyword: Internet-Draft
v: 3

ipr: trust200902
date: {DATE}
stand_alone: yes
pi: [toc, sortrefs, symrefs, docmapping]

author:
-
    ins: L. Iannone
    name: Luigi Iannone
    #role: editor
    org: Huawei Technologies France S.A.S.U.
    abbrev: Huawei
    street: 18, Quai du Point du Jour
    city: Boulogne-Billancourt
    country: France
    code: '92100'
    email: luigi.iannone@huawei.com
-
    ins: A. Fressancourt
    name: Antoine Fressancourt
    #role: editor
    org: Huawei Technologies France S.A.S.U.
    abbrev: Huawei
    street: 18, Quai du Point du Jour
    city: Boulogne-Billancourt
    country: France
    code: '92100'
    email: antoine.fressancourt@huawei.com

normative:
    
#   IEEE1619-2007: DOI.10.1109/IEEESTD.2008.4493450

#   MODES: DOI.10.6028/NIST.SP.800-38A

informative:
  PIR95: DOI.10.1109/SFCS.1995.492461

#  SHENOY21: DOI.10.1109/HPSR52026.2021.9481818

#  BLESS22: DOI.10.23919/IFIPNetworking55013.2022.9829816

#  RIDOUX05: DOI.10.1007/11422778_41

#  ERIKSSON04: DOI.10.1109/INFCOM.2004.1356997

--- abstract

This document describes the privacy issues associated with the Discovery of Agents, Workloads, and Named Entities (DAWN). 
It provides general observations about typical current privacy practices in similar domains like, DNS, HTTP, and in general privacy in information retrieval.
   
--- middle

# Introduction {#Sec:intro}

{{!I-D.akhavain-moussa-dawn-problem-statement}} defines the problem space how AI-related entities discover and interact with one another across distributed ecosystems. In particular, it focuses on defining the requirements for a standardized discovery substrate that allows entities to find one another based on attributes like skills, capabilities, policies,communication methods, and collaborate dynamically.

In such a context, privacy is one of the hardest problems in entities discovery because the act of discovery itself can leak sensitive information. When an entity searches for another entity, model, dataset, or compute resource, the query may reveal sensitive intent. For instance, a medical AI agent querying oncology datasets may reveal information about user health, or a company agent searching for GPU clusters before a product launch may reveal business strategy. This may lead to privacy risks like surveillance of organizational behavior, users/enterprise profiling correlation attacks.

This document focuses on the privacy risks associated to the action of entities discovery, i.e., how to protect the privacy of the entity performing the discovery so there is no information leakage. It provides an threat analysis following the guidelines in {{!RFC6973}}.

Published entity properties attributes, such as capabilities, endpoints, availability, geographic location, etc., may be also sensitive information. Entities' published information should be controlled by their operators; privacy considerations about published information will discussed in future revision of this document.

Private communication among entities should be part of the communication protocol itself, hence considered out of the scope of this document.   

# Requirements Notation {#Sec:req}

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 {{!RFC2119}} {{!RFC8174}} when, and only when, they appear in all capitals, as shown here.


# Definitions of Terms {#Sec:term}

This document assumes familiarity with the terminology defined in {{!I-D.farrel-dawn-terminology}}:

- Attributes
- Discoverable Object
- Discovery
- Discovery Mechanism
- Entity
- Minimum Discoverable Information


# Applicability Scope

{{!RFC6973}} clearly states that privacy should be included into protocols from the design phase, not afterwards. This is especially true in open and  cross-domain ecosystems. As such any discovery protocol designed in the context of DAWN should natively include mechanisms to provide privacy protection. However, the use of such mechanisms may be relaxed in specific contexts, like for instance closed ecosystems. A closed ecosystem is an environment where discovery, communication, identity, orchestration,
and capability advertisement are restricted to a single vendor, platform, enterprise, or tightly controlled federation. Example of such ecosystems, may be internal coding assistants, HR workflow agents, finance analysis agents, procurement bots, security automation agents. In such tightly controlled and closed environments privacy requirements might be less strict and privacy protection can be relaxed. Yet, it is important to understand that privacy protection should be maintained by these closed environments when interfacing with other entities outside the local domain.

# Privacy Threat Analysis

{{!RFC6973}} provides guidelines about privacy in Internet protocols. It also introduces privacy related terminology and it provides a structured framework for analyzing privacy threats in Internet protocols. Many of the privacy issues emerging in entities discovery, map directly onto the privacy concepts identified in {{!RFC6973}}. As such the following subsections go through the the privacy threats identified in {{!RFC6973}} and describe how they relate to DAWN. The subsections assume that the reader is familiar with {{!RFC6973}}. 

## Combined Security-Privacy Threats 

### Surveillance

Surveillance consists in observing communications or interactions over time.
In a discovery infrastructure a malicious observer can see which agents query which capabilities, organizational interests, workload patterns,
operational behavior. Discovery substrates become surveillance points unless privacy protections are built in.

### Stored Data Compromise

Stored protocol data becomes a privacy risk if not adequately protected.
Discovery systems may store query logs, interaction histories, and other type of metadata, that may reveal usage patterns, workflows, enterprise operations. Hence, stores data should be minimized  and protected.

### Intrusion

TBD

### Misattribution

TBD

## Privacy-Specific Threats

### Correlation

Linking multiple interactions like repeated discovery queries, agent identifiers, capability searches, may lead to identify users or entities behavior.  

### Identification

Protocols may expose identity unnecessarily. In the context of DAWN, discovery may expose organization names, infrastructure ownership,
operator identity. Even capability metadata may uniquely fingerprint an entity. Discovery should avoid identity exposure beyond operational necessity.

### Secondary Use

TBD

### Disclosure

TBD

### Exclusion

TBD

# Similarities with Domain Name System (DNS) privacy protection

Discussion about DNS privacy and similarities with DAWN from a privacy perspective.

TBD

# Privacy vs Auditability

TBD

# {{!RFC6973}} Guidelines Compliance

{{!RFC6973}} provides guidance in the form of a questionnaire about a protocol being designed.

[Replies to RFC6973 questionnaire to be added.]

# Threats Mitigation

{{!RFC6973}} defines three categories of relevant mitigations, namely (1) data minimization, (2) user participation, and (3) security. They apply also in the context of DAWN.

## Technological building blocks

Some privacy-enhancing technologies can be used at an advantage in improving the privacy of entities discovery. 
Among those technologies, Private Information Retrieval can be used at a benefit in the development of privacy-preserving discovery protocols.   

Private Information Retrieval (or PIR) {{PIR95}} is a technology initially developed in the database realm.
It is used by users to retrieve information stored in a server while hiding the exact retrieved information from the server hosting it. 
As PIR schemes have gained efficiency and become usable at scale in a distributed setting, their use in DAWN to prevent registrars or entities hosting capacities of interest to retrieve information about requesters' interests and activities.
In investigating those developments, specific care need to be taken about the ability of academic PIR schemes to cope with the scale at which DAWN needs to operate.

[Future revision to have DAWN-specific mitigation categories]

# IANA Considerations {#SEC:iana}

This document does not require any IANA action.

# Security Considerations {#SEC:security}

TBD.

<!-- # Acknowledgements {#Acknowledgements}
{: numbered="false"}
This document received many comments and help from community people. 
<!- -XXX did provide technical comments for this document.- -  >
The authors would like to thank all of them.-->

--- back
