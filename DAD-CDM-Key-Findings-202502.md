
# DAD-CDM Key Findings
## February 2025

## Summary of progress

In 2024, the Steering Committee met 18 times to discuss the development of extensions to the OASIS STIX standard to support modeling of Foreign Information Manipulation and Interference (FIMI) operations.

The Steering Committee agreed that both taxonomies and definitions needed to be examined and revised, while the core and structure of STIX should not be changed. For example, a new object should not be created unless modifying existing objects' properties would not allow adequate description of the model of threats to the public information environment, including hybrid threats involving cyber attacks. For the purposes of this document "existing" or "current" means anything that already exists in STIX 2.1 or is planned for STIX 2.2, specifically the [Incident Extension Suite](https://github.com/oasis-open/cti-stix2/tree/master/examples/stix2.2/incident).

So far, the Steering Committee has examined the following categories of STIX objects: Incidents and related objects, Actors, Channels and Relationships, Narratives, and Cyber Observables. Below is an overview of the committee's work.

## Overview of Current and New STIX Object Definitions for FIMI

The table below summarizes the new or current STIX objects related to FIMI that we propose to keep and/or develop, the associated definitions we propose, and remarks to contextualize our proposals.

| STIX Object (New/Current) | Definition (New/Current) | Remarks |
|--------------------------|--------------------------|---------|
| Incident (current) | An adverse occurrence confirmed by initial investigation of one or more related adverse events whose actual or potential impact has been deemed significant enough to merit further investigation and/or response | In the broadest sense, an Incident is an occurrence of anything deemed adverse and worthy of investigation and response. The proposed definition captures the way the term is used in the [Incident Extension Suite](https://github.com/oasis-open/cti-stix2/tree/master/examples/stix2.2/incident), which is based on the language of "Incident Response" from the cyber world in which an "Incident" is declared according to an "Incident Response Plan". It is preceded by one or more "security events" (aka events which could threaten information security) and it "should have sufficient properties to represent the current state of the incident or investigation while serving as an anchor point to record both related activities and the impact to an organization". The definition is proposed for use in both proprietary (cyber) and public (FIMI, online harm etc) information environments, and users can customize the definition to suit their own use case. |
| Case (new) | An issue or request from a customer or constituent requiring the investigation, coordination, and resolution of an incident. | There is currently no "Case" object in STIX but there is in OpenCTI. It is not clear that we need this object as there is overlap with the Incident object, which may suffice. The term is used in "case management", "customer service management", or "ticketing systems" to refer to the handling of an issue or request from a customer that may involve assignment, diagnosis, escalation, and resolution. Cases can involve any issue or request covered by a service provider contract. Here the issue or request is to handle an Incident for the customer. As the customer reaches out for help with an Incident, a support agent will create a new Case. The Case assists the agent in coordinating all activities, communications, and third parties involved in resolving the Incident. The Case remains open until a resolution has been presented to and accepted by the customer. |
| Event (current) | A happening that has had or may have a harmful effect on (cyber)security or on the public information environment, or a significant happening in the real world that can provide the context for a threat | In the [Incident Extension Suite](https://github.com/oasis-open/cti-stix2/tree/master/examples/stix2.2/incident) an event is equivalent to a "security event" i.e. an intrusion or security policy violation that may have a negative effect on the confidentiality, integrity or availability of the organization's proprietary information environment. Similarly, an Event can occur that might have a harmful effect on the public information environment e.g. an occurrence of clickbait, online harm etc. But in the context of threats to the public information environment an Event is more typically a happening of significance in the real-world such as a national election, a sports event etc. which can be exploited by Threat Actors to spread propaganda or mount cyber attacks. |
| Campaign (current) | A planned series of adversarial activities carried out over a period of time against a specific set of targets to achieve a discrete long-term objective | Defenders make an intelligence assertion based on the evidence in hand that what they are seeing is the result of a concerted Campaign with a presumed objective and target set. As objectives and/or targets change over time it becomes possible to delineate one Campaign from another. Campaigns may be characterized by a common set of adversarial behaviors and/or resources but what sets them apart are their presumed objective and target set. |
| Intrusion Set (current) | An entire attack package of adversarial activities, behaviors and resources with common properties, which is designed to facilitate unauthorized access to computer systems, which is believed to be orchestrated by a single organization, and which may be used over a very long period of time in multiple campaigns to achieve multiple objectives | Where a Campaign is a set of attacks over a period of time against a specific set of targets to achieve some objective, an Intrusion Set is the entire attack package and may be used over a very long period of time in multiple Campaigns to achieve potentially multiple purposes. New activity can be attributed to an Intrusion Set even if the Threat Actors behind the attack are not known. While sometimes an Intrusion Set is not active, or changes focus, it is usually difficult to know if it has truly disappeared or ended. For semantic clarity, under consideration is the introduction of a new STIX Domain Object (SDO), "Manipulation Set", whose name would better capture a set of behaviors and resources designed to facilitate manipulation of the public information environment rather than unauthorized access to computer systems, such as cloning websites, narratives that resonate with a target audience, and amplification bots. Unattributed hybrid threats might then be described using both an Intrusion Set and a Manipulation Set. Ideally we would just have one SDO to describe any set of threat actor elements, but naming is a challenge. |
| Threat Actor (current) | Actual individuals, groups, or organizations believed to be operating with malicious intent. | Threat Actors leverage their resources, and possibly the resources of a Manipulation Set and/or an Intrusion Set, to conduct attacks and run Campaigns against targets. Threat Actors can be characterized by their motives, capabilities, goals, sophistication level, past activities, resources they have access to, and their role in their organization. |
| Channel (new) | A specific, immutable conduit for carrying messages or other content from one place to another | A way to reach people with messages (phone, email, chat) or other content (TV, radio, or internet based). Channels can be semi-permanent ways that Media Outlets reach their audience e.g. RTL Television in Germany can reach its audience through www.rtl.de, 396 MHz radio, or @rtl_news on YouTube. Or channels can be more ephemeral ways that Campaigns can reach a target audience such as a temporary WhatsApp group, or a specific Twitter profile. A channel need not be electronic, such as, word-of-mouth. A Channel is a vector that is logically distinct from the physical means (e.g. fiber-optic cable) or the technical platform (e.g. Telegram) upon which it relies. A channel is useful for tracking information. |
| Media Outlet (new) | An editorial entity that provides news and information to the public through various channels | An editorial entity such as RTL Television should be considered as a Media Outlet that can promote its content through multiple Channels. Media Outlets are identified using a unique Universal Media Identifier (UMId). A higher level organizational entity such as RTL Group should be considered a Legal Entity, identified using a Legal Entity Identifier (LEI). |
| Cyber Observable (current) | An object that has been or can be observed directly rather than inferred and which can constitute evidence of a threat | Granular objects found on network devices and endpoints such as files or processes can be used to understand what actually happened within a proprietary information environment. Similarly granular objects found on the internet such as the content of social media posts or in physical space such as the content on billboards can be used to understand what actually happened within the public information environment. Observables document the facts about what happened. They do not capture the who, when or why but they can be used as evidence for these higher-level intelligence assertions. |
| Task (current) | A usually assigned piece of work performed by or for a defender, typically but not exclusively in response to an incident | The Task SDO was created in the Incident Extension Suite primarily as a way of recording the actions undertaken by the incident response team to resolve an Incident. However, Tasks can also be performed prior to an Incident such as an investigation of one or more security events or of one or more suspicious or anomalous activities. In the case of the public information environment a common task is an open source investigation (of a suspected channel or a reported terms of service violation etc.), or the hunt for a known threat (a threat hunt). |
| Impact (current) | The result or potential result of an event or incident upon an affected entity | The Impact SDO was created in the Incident Extension Suite primarily as a way of assessing the potential or actual consequence of an Incident. However, Impact can also be assessed prior to an Incident, when adverse events occur or potential threats are otherwise identified. Affected entities can include victims, categorized by identity class such as individual, group, system, organization, or community; assets owned by the victim, categorized by infrastructure or observables; or information related to the victim, categorized by narratives or media-content. |
| Sighting (current) | The belief that a specific threat has been seen, how often, within which timeframe, by whom, and (optionally) the specific raw data that informed the belief | A Sighting is an intelligence assertion that a threat entity such as a threat actor, a campaign, a manipulation set, a narrative, an attack pattern, an indicator, has been seen, along with how often it was seen, who saw it, within which timeframe it was seen, and possibly the raw data on the specific observations made that led the analyst to make the assertion that they saw this specific threat entity. A Sighting is a special STIX Relationship Object (SRO) that relates the identity of the sighter to what is believed to have been sighted. |
| Narrative (new) | The description of a sequence of real or imagined events in the world, organized in a storytelling format and often involving stereotypical roles such as hero or villain | The description may be explicit, in that the events are directly described, or may be a reference, in which events that are assumed known to the audience are called to mind. The events in the sequence may be real, imagined, or of unknown status. The sequence itself may exhibit temporal, causal, or complication-resolution structure. Finally, the event participants may be cast, implicitly or explicitly, in stereotypical roles such as hero, villain, among others. |

## Incident: Problem Statement

Currently, the STIX specification does not adequately address:

1. The process by which researchers of the public information environment detect and analyze threats, which is investigation-driven rather than event-driven. This means there is no way to detect observables and then make intelligence assertions based on these observables about higher-level threat entities such as threat actors or campaigns or narratives within the context of an investigation or threat hunt. We can only make those correlations within the context of a security event, but the counter-FIMI field lacks the extensive telemetry enjoyed by the cyber world for detecting threats and generating events (firewalls, intrusion detection systems, antivirus systems etc).

2. Similarly, the STIX specification does not adequately address the process by which the counter-FIMI community investigates incidents, assesses their potential impact and harm, and decides on mitigations. While cyber incidents are typically investigated by the victim organization or their service provider, the situation is less clear for incidents in the public information environment, which may require several organizations working in concert. And what is captured largely by a combination of the CIA triad (confidentiality, integrity, availability), financial metrics, and consideration of recoverability in the cyber world requires significantly more nuance in the counter-FIMI field, including issues of authenticity, veracity, and equanimity; harms ranging from financial to psychological to physical; and consideration of whether incidents can even be mitigated at all.

3. Finally, the STIX specification does not adequately address the importance of real-world events for providing the context for many attacks by threat actors in the public information space. In the cyber world the term "event" is confined to security events generated by cyber telemetry and processed by the Security Operations Center. In the public information environment real world events often provide an opportunity for threat actors to exploit.

## Summary of Proposed Changes

This extension will introduce the following high-level changes:

- **New Object Types:** An extension object for the Impact SDO specific to the public information environment with properties for impact type, harm type, mitigateability; and metrics for reach, engagement and harm. Sub-objects of the Impact SDO for reach, engagement, and harm metrics.

- **Extended Properties:** Additional properties for the Incident SDO to specify the coordinating entity and supporting entities involved in investigating and resolving an Incident in the public information environment. An additional property for the Event SDO to provide the context for the event (cyber, public information environment, or real world). An additional property for the Task SDO to list the Sightings made when carrying out the task (when the task is an investigation). An expansion of the scope of the property within the Sighting SRO that reports where the Sighting was made, to include technology Platforms such as Facebook etc.

- **New Relationships:** New relationships, for a Threat Actor, a Manipulation Set, an Incident, a Channel, or a Narrative targeting an Event; for an Incident using a Channel or Narrative; and for an Incident being attributed to a Manipulation Set. New reverse relationships to capture who declares an Incident and who publishes a Report about the Incident.

- **New and Extended Taxonomies:** A new enumeration for event context and considerable additions to the event type open vocabulary. New open vocabularies for impact type and online harms type for the new extension object of the Impact SDO. And a new enumeration for mitigateability for the new Impact extension.

These changes align with the STIX specification's core principles while addressing the identified gaps.

## Expected Benefits

Adopting this extension is expected to provide the following benefits:

- **Whole-of-Society Approach:** Enable multi-stakeholder collaboration to counter online threats
- **Prioritizing Threats:** Standardize the process of assessing potential impact and harm and prioritizing threats
- **Event Planning:** Improve threat assessments for real world event planning

## Example Scenario

To illustrate the value of this extension:

**Scenario: Modeling the UK Southport Riots**

This example demonstrates the use of the event sequencing capability built into the Incident Extension Suite. The sequence starts on July 4th with the UK election (event context is "real-world") which was preceded by hundreds of observations of an Islamophic narrative (codified as a Sighting object embedded within an event with context of "public-information-environment") being spread in the public information environment via an AI-generated video (codified as a media-content object).

The sequence continued with a mass stabbing on July 29th in Southport (event context is "real-world") in which three children were killed, which was quickly followed by numerous sightings in social media of a false narrative regarding the suspect's identity, nationality, religion and immigration status (codified as a Sighting object embedded within an event with context of "public-information-environment").

The sequence ended the first week in August during which far-right anti-immigration riots occurred throughout England and Northern Ireland (event context is "real-world"). The riots triggered the creation of an incident that required an investigation into the role of hateful rhetoric, disinformation, and misinformation, and a national response by the government. The example demonstrates how the impact on society escalated as events in the real world and in the public information environment interacted over time (codified using the state change sub-object type).

## Actor: Problem Statement

STIX 2.1 provides currently several STIX objects related to actors:

- a threat actor which can be either an individual, a group or an organization
- an identity object which can also be either an individual, a group or an organization.
- a location object for a region, a country or geography coordinates.

After studying these objects, we concluded that these are not currently suited to capturing details of FIMI threats, lacking granularity and failing to meet analysts' needs to describe information operations. Our proposals aim to reflect in a more accurate way both the actors we can come across in FIMI, including journalists, diplomats and media, and their corresponding relationships, and roles.

## Summary of Proposed Changes

Our proposed changes aim to detail in a more accurate way the variety of actors involved in FIMI, including their relationships and roles.

In order to keep the STIX language simple and facilitate potential changes, we agreed to expand the open vocabularies and properties associated with the Threat Actor SDO instead of proposing new STIX domain objects.

This extension will introduce the following high-level changes:

We propose 13 new threat actor types in addition to the 12 already [existing](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_eaton5rga6k9) types (10.22 Threat actor type). Under consideration as an alternative for some of the new threat actor types is to use or extend the open vocabularies for threat actor role and identity class.

Following the same rationale of simplicity and facilitating the use of STIX, we identified two new relationships "contract with" and "is sponsored by" which could apply systematically to each threat actor type. These relationships' properties could be expanded to specify more precisely the nature of the relationship between each threat actor. For example:

- "is sponsored by" could be applied in different situations: financing a journalist's travel, supporting an agent with a new computer or new facilities, giving training.
- "contract with" could be applied in these situations: buying a software from a company, outsourcing media content to a content farm.

Under consideration as an alternative to these new relationships is the use of the threat actor role open vocabulary. These new relationships or use of the threat actor role open vocabulary could be completed according to the community's feedback and the evolution of information operations.

These new additions are listed below.

| Type | Definition | Relationships |
|------|------------|--------------|
| Company | a for-profit organization, to which a threat actor can outsource its influence operation. | Contract with<br>is sponsored by |
| Diplomat | a government representative, representing a country (political meaning), likely spreading narratives to a national and international audience. | Contract with<br>is sponsored by |
| Entrepreneur | a private economic actor conducting information operations for a threat actor. | Contract with<br>Is sponsored by |
| Expert | an actor self-designated or designated by others as an expert likely spreading narratives and content with credibility. | Is sponsored by<br>Contract with |
| Government Unit Cell | The unit within a government, to which the information operation is delegated. | Contract with<br>Is sponsored by |
| Individual | a person who is part of an influence operation, but isn't an official or informal vector | Is sponsored by<br>Contract with |
| Influencer | an actor self-designated or designated by others as an influencer, likely spreading narratives and content with credibility. | Contract with<br>Is sponsored by |
| Journalist | an actor self-designated or designated by others as a journalist, likely spreading narratives and content with credibility. | Is sponsored by<br>Contract with |
| Media | a media outlet, whether a TV, radio or press outlet, whose legitimacy and identity can be leveraged during an information operation. | Is sponsored by<br>Contract with |
| Offline service provider | individuals, groups or organizations providing offline services. Examples include: organizing a demonstration, painting graffitis. | Is sponsored by<br>Contract with |
| Online service provider | online infrastructure providers likely to be leveraged to conduct a campaign. | Contract with<br>Is sponsored by |
| Public Official | an elected or appointed official, linked to a country (political meaning), likely spreading narratives to a broad national and international audience. | Is sponsored by<br>Contract with |
| Researcher | an actor self-designated or designated by others as a researcher, likely spreading narratives and content with credibility. | Is sponsored by<br>Contract with |

We aim to propose a refined version of the relationships with the list of their properties in a future report.

## Expected Benefits

Adopting new threat actor types enables STIX users to describe information operations more accurately without being overwhelmed by too many STIX objects and enables them to propose new types in the future which can be easily implemented. This can be a good solution taking into account FIMI's quick evolving nature.

## Example Scenario

To illustrate the value of these additions and changes:

Based on the investigations conducted by [Mandiant](https://www.mandiant.com/resources/blog/haixun-silent-titan-global-influence) and the [CitizenLab](https://citizenlab.ca/2023/09/unraveling-chinas-global-media-influence-the-haixun-press-operation/) on a network of inauthentic websites posing as local news outlets, a digital marketing firm called "Haixun" has contracted with for-hire freelancers via the platform Fiverr to promote information manipulation campaign content.

In the light of this example, these new threat actors types and relationships will enable analysts to describe more precisely information manipulation campaigns, increasingly outsourced to third parties.

## Channels and Relationships: Problem Statement

Currently, the STIX specification does not adequately address the many varieties of ways of describing information "channels". This limitation creates challenges such as inconsistent descriptors of how information flows, in particular a variability in the granularity of the flow leading to variability in the amount of information captured for analysis and description. This can lead to comparing operations at very different scales, or comparing full operations against sub-parts of an operation against, or just plainly, comparing inconsistent things.

In the current regime adopted by Filigran in OpenCTI a TV news station can be captured as a channel and also an individual social media account. Both of these acquire and disperse information but in very different ways. These have very different reaches, information flow control mechanisms, and ways through which information can pass through them. In particular, the flow information through these channels is mutable (it can be interrupted or redirected), and it may not be possible to trace the flow of information from the source to the destination without interruption. Note that this difficulty is a limit of the knowability of the information flow descriptors and not one of accessibility to the information flow descriptors (which is always an issue). Each of these, in the context of a FIMI investigation can be more usefully described as chained pathways of channels that can more accurately and fully describe the exchanges of information.

Another problem that currently exists in the public information environment is confusion over the source of content. Many media brands and channel names sound similar, sometimes by coincidence, but often on purpose when malicious actors try to create confusion on which they can capitalize. These actors mislead audiences and advertisers as well as the algorithmic-driven recommender systems of search or social media platforms that direct our attention and advertisers' dollars.

The following improvements can help thorough investigations be better captured and greatly advance information sharing on threats and their mitigation.

## Summary of Proposed Changes

This extension will introduce the following high-level changes:

- A Channel object, defined as – An immutable conduit for information that constrains its flow from point A to point B. This could be "word of mouth" or a telegram channel or a facebook page, or a legal action (e.g. FOIA request), etc, and it will allow for the full gambit of activity that can be described as flow of information.

- This object will carry properties that allow one to specify the channel (such as, name, alias, description, and URL), as well as additional properties that allow one to describe information flow manipulators. These include things like the channel owner, and typical uses, but also descriptions of its publishing capabilities as well as its targeting capabilities.

- This object will be able to have specific relationships to its owner, its targets, and the specific bit of information that it was used to disseminate. Furthermore, the channel object can relate to partners of the channel to highlight easier access to and increased probability of information, as well as direct links to other channels that are connected in some way (hosted, promoted, back-linked, etc.). This object will also capture relationships between channels and individuals that capture how individuals can interact with channels. In this way, the channel relationship set will completely specify the actors and information that they connect.

- A new STIX Domain Object called "Media Outlet" which aligns with [proposals](https://www.gmr-registry.org/) being put forward by the Global Media Registry in Germany. This new SDO would model large media brands which reach their customers through multiple channels. Examples: (1) the Media Outlet "Sputnik" can reach audiences in different geographies via the Channels [sputnikglobe.com](https://sputnikglobe.com), [sputnikarabic.ae](https://sputnikarabic.ae), [sputniknews.com.tr](https://sputniknews.com.tr), [spnfa.ir](https://spnfa.ir), [sputnik.af](https://sputnik.af), [sputniknews.lat](https://sputniknews.lat), and [sputniknewsbrasil.com.br](https://sputniknewsbrasil.com.br) (2) the Media Outlet "RTL Television" can reach its audience via its web channel [www.rtl.de](https://www.rtl.de), a radio channel D306 at 396MHz, a YouTube channel [@rtl_news](https://youtube.com/@rtl_news) etc.

These changes align with the STIX specification's core principles while addressing the identified gaps.

## Expected Benefits

Adopting this change is expected to provide the following benefits:

- A clear and consistent standard by which operations can be compared with regards to how information flows through them.
- A framework that can treat information flow as fully inspectable, allowing for the full description of flow (depending on accessibility) from source to target.
- Improved cross-comparison between and analysis of operations against a clear and consistent standard.
- Unambiguous identification of the source of content from trusted media brands, increasing consumer protection and improving brand safety.

## Narratives: Problem Statement

Currently, the STIX specification does not adequately address how to describe observed narratives. One of the main purposes of FIMI operations is to promulgate narratives to target populations, as narratives are one of the main mechanisms of influence and manipulation online. Specific populations are vulnerable to particular narratives or narrative tropes, and thus threat actors tailor narratives to take advantage of these vulnerabilities. To understand the narratives in play, and effectively protect against or counter them, we must be able to describe them.

For the purposes of describing FIMI operations, we will provisionally define narrative as a description of a sequence of events in the world. The description may be explicit, in that the events are directly described, or may be a reference, in which events that are assumed known to the audience are called to mind. The events in the sequence may be real, imagined, or of unknown status. The sequence itself may exhibit temporal, causal, or complication-resolution structure. Finally, the event participants may be cast, implicitly or explicitly, in stereotypical roles such as hero, villain, among others.

STIX itself does not address narratives directly. The STIX FIMI Model—a proposed extension to STIX 2.1 for describing FIMI—contains a Narrative object, but the representation of the narrative itself is just a free text string, and the extension only contains a "subnarrative-of" relationship between Narrative objects, and a variety of "uses" relationships between other STIX objects (Threat-Actor, Intrusion-Set, Campaign, etc.).

The OpenCTI FIMI approach is a good start, but limited in several ways. First, it does not allow more detail about the narrative to be provided in structured form, if such detail is available. Second, it does not correctly capture the complexity of the relationships between narratives, or the ways in which narratives may be used in FIMI. Third, it does not provide any guidance to STIX practitioners in how to uniformly identify narratives and notate them.

## Summary of Proposed Changes

We provisionally are considering three changes to implement a STIX extension that would allow effective, uniform, and reliable description of observed narratives.

1. A new Narrative SDO object, modeled initially on the OpenCTI FIMI extension object of the same name, that provides appropriate attributes for describing observed FIMI narratives. The object will have:
   a. A small set of required attributes, possibly only "name" and "short-description"
   b. Multiple clusters of attributes and embedded relationships which provide different approaches for describing the observed narrative, depending on the information available. In particular, the representations should be robust to the practitioner lacking specialized knowledge that allows them to fully understand the narrative in context.

2. New relationship types, specific to the Narrative SDO, that allow narrative objects to be related appropriately

3. A coding handbook that describes, in terms accessible to most STIX practitioners, the conventions and procedures that should be followed to ensure uniform and reliable coding of observed narratives.

## Expected Benefits

Designing a Narrative extension that provides the described functionality will allow practitioners to capture valuable information that can be used to (1) track the spread of harmful narratives in the media, (2) infer the identity, motivations, and goals of threat actors, and (3) counter or mitigate the harmful effects of narratives. In particular, it will allow one to (a) reliably and uniformly identify FIMI narratives, (b) reliably and uniformly identify the relationships between those narratives and their uses, and (c) reliably and uniformly map narrative vulnerabilities in target populations.

## Cyber Observables: Problem Statement

STIX 2.1 provides few STIX objects which could adequately describe all the content-related online observables. We identified the object "files" which could be used to describe text, image, video, and audio content. However, this object doesn't address the requirement to describe the "container" of this content, the medium through which the content appears online: a post, a tweet, an article etc. Concretely, this suggestion aims for instance to separate the tweet itself from the type of media shared within the tweet (image, video, etc.). We concluded that we need to find an adequate system to represent this duality. We are currently exploring three options:

- Use the properties of channels objects to include components such as ID of the tweet, name of the platform to describe the container and connect these properties through a relation to the file object which would describe the content itself.
- Develop the current OpenCTI STIX extension of media content which would include both the container and the content of the cyber observable.
- Introduce a new STIX Domain Object "Posting" as the container with a sub-object for content and a handful of sub-type extensions to handle the different properties of social media posts, blog posts, news articles etc. A [similar approach](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_3j3ly1uw5ll8) is used currently in STIX to model files of different types (PDF, archive etc.).

We intend to test these three options, ensuring simplicity of use while keeping granularity and preciseness in the description of all the cyber observables that can be surfaced online.
