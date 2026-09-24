# Threat Actor & Intrusion Set

Table of Contents

- [Introduction](#_Toc232626897)
- [Acknowledgements](#_Toc232626898)
- [Threat Actor](#threat-actor)
  - [Properties](#properties)
  - [Vocabularies](#_Toc232626901)
  - [Relationships](#relationships)
  - [Example 1: Overt State Influence](#example-1-overt-state-influence)
  - [Example 2: Harassment](#example-2-harassment)
  - [Example 3: Scam](#example-3-scam)
  - [Example 4: Misinformation](#example-4-misinformation)
- [Intrusion Set](#intrusion-set)
  - [Properties](#properties-1)
  - [Vocabularies](#vocabularies-1)
  - [Relationships](#relationships-1)
  - [Example 5: Gender-Based Violence](#example-5-gender-based-violence)
- [Integrated Hypothetical Example](#integrated-hypothetical-example)
  - [STIX Bundle](#stix-bundle)
  - [Knowledge Graph](#knowledge-graph)
- [Integrated Real-World Example](#integrated-real-world-example)
  - [STIX Bundle](#stix-bundle-1)
  - [Knowledge Graph](#knowledge-graph-1)
- [Vocabularies](#vocabularies-2)
  - [Threat Actor Type Vocabulary](#threat-actor-type-vocabulary)
  - [Threat Actor Role Vocabulary](#threat-actor-role-vocabulary)
  - [Attack Motivation Vocabulary](#attack-motivation-vocabulary)
- [Enumerations](#enumerations)
  - [Context Enumeration](#context-enumeration)

## Introduction

This document proposes extensions to STIX 2.1 to handle the threat actor and intrusion set STIX Domain Objects (SDOs) relevant to Foreign Information Manipulation and Interference (FIMI) and other types of online harm, such as hate speech, digital fraud, or information suppression. These extensions refer to properties, relationships, enumerations, and open vocabularies. The proposal adheres to the guidance laid out in section 7.3 of the STIX 2.1 specification<sup id="fnref-1"><a href="#fn-1">1</a></sup>. The following Large Language Models have been used to refine this proposal: Google Gemini 3 Flash, Perplexity Pro (which at the time of writing uses Perplexity Sonar, OpenAI GPT‑5.4, Claude Sonnet 4.6, Claude Opus 4.8, or Gemini 3.1 Pro, depending upon query), and Claude Opus 4.8.

The current Threat Actor, Intrusion Set, and Identity SDOs and their relationships are depicted in the following figure.   
<p align="center"><img src="media/c077982c2b36ce869083ef5125b39bf9.png" style="max-width: 100%;"></p>

Threat Actors are individuals, groups, or organizations believed to be operating with malicious intent. Threat actors are mental constructs in the minds of defenders. The real actor(s) behind a threat actor are modeled using the Identity SDO.

An Intrusion Set is a grouped set of campaigns, adversarial behaviors and resources with common properties that is believed to be orchestrated by a single organization. An Intrusion Set can be thought of as the fingerprint of a Threat Actor whose real identity may be known or unknown.

Recent publications by FIMI defenders refer to one type of “intrusion set” in the public information environment as an “information manipulation set.<sup id="fnref-2"><a href="#fn-2">2</a></sup>” This is defined “as a set of adversarial behaviors, tools, and tactics likely linked to the same threat actor. These sets bridge the gap between individual incidents and full campaign attribution, enabling analysis at three levels: tactical (incident-level data), operational (narratives and infrastructure), and strategic (linking to threat actors and intent).” Where intelligence exists and resources permit, we recommend that FIMI defenders move beyond tactical level reporting to model FIMI threats at the operational level using the Intrusion Set SDO, or at the strategic level using the Threat Actor SDO. As explained by the Doppelgänger Working Group, this approach will help the community move beyond less effective short-term responses towards stronger technical attribution, more systemic risk mitigation and more effective long-term threat disruption<sup id="fnref-3"><a href="#fn-3">3</a></sup>.

## Acknowledgements

The DAD-CDM Technical Steering Committee would like to express its sincere gratitude to the EU External Action Service (EEAS), CheckFirst, Davide Gianni, Jeff Mates (US DoD Cyber Crime Center – DC3), Tim Casey (formerly Intel), and Adam M. (DISARM Foundation) for their guidance and feedback throughout the course of this research. Their expertise and insight greatly contributed to the development of this work to ensure that our findings align with the current practices of the STIX and FIMI communities.

This document includes only the proposed *extensions* to STIX 2.1. To get the complete picture, readers are advised to read this document in conjunction with the STIX 2.1 specification<sup><a href="#fn-1">1</a></sup>. This document also assumes the existence of the Event, Task, and Impact SDOs which have been proposed by the Cyber Threat Intelligence Technical Committee of OASIS (the “CTI-TC”) for inclusion in STIX 2.2<sup id="fnref-4"><a href="#fn-4">4</a></sup>.

New relationships being proposed include those already added by Filigran to OpenCTI<sup id="fnref-5"><a href="#fn-5">5</a></sup>. They assume not only the existence of the Event, Task, and Impact SDOs, but also the Channel, Narrative, and Persona SDOs and the Media Content SCO. These latter objects have been proposed by Filigran as DAD-CDM extensions<sup id="fnref-6"><a href="#fn-6">6</a></sup>. They will be the subject of separate DAD-CDM proposals.

## Threat Actor

The original STIX 2.1 [**`threat-actor-type-ov`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_tqbl8z36yoir) drew inspiration from Intel’s Threat Agent Library<sup id="fnref-7"><a href="#fn-7">7</a></sup>, selecting the threat agents which were of most relevance to the cyber community, with the goal of creating a simple and concise taxonomy. The DAD-CDM Technical Steering Committee (TSC) has taken the same approach. We expanded the Threat Agent Library into a comprehensive set of threat agents across four classes of hostile intent: intrusion (theft, sabotage – the cyber case), manipulation (disinformation, FIMI), abuse (hate speech, information suppression), and exploitation (fraud, sextortion). From this set of threat agents (for details see the supporting document *Expanding Intel’s Threat Agent Library to Accommodate FIMI and Other Online Harms*) we have selected the agents and motivations which are most relevant to and most easily understood by those defending the integrity of the public information environment, and we have simplified the descriptions of those for an international audience.

Preference was given to recognizable entities which could be clearly identified by their repeated actions of a particular malicious type. Ad hoc or one-off malicious actions which do not rise to the level of an identifying characteristic remain as techniques modeled using the Attack Pattern SDO. The TSC preferred to avoid labels with emotionally loaded terms (“public propagandist” was replaced by “overt manipulator”), labels which are difficult to evidence (“misinformer”), and labels which are politically controversial (“passive bigot”).

### Properties

No new or amended properties are recommended.

### Vocabularies

-   We recommend the following new entries to Threat Actor Type Vocabulary [**`threat-actor-type-ov`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_tqbl8z36yoir): Overt Manipulator, Covert Manipulator, Influence for Hire Provider, Cyber Mob, Cyber Bully, Fraudster, Cyber Stalker, Extortionist. See Threat Actor Type Vocabulary for details.
-   We recommend the following new entries to Attack Motivation Vocabulary [**`attack-motivation-ov`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_dmb1khqsn650): “Belonging”, “Control”, “Superiority”, “Adulation”, “Outrage”, “Revenge”, “Spite”, “Hatred”. See Attack Motivation Vocabulary for details.

### Relationships

The following additional relationships are recommended.

| Source | Type | Target | Description |
| --- | --- | --- | --- |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`sponsors`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw), [**`campaign`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_pcpvfz4ik6d6) | The threat actor sponsors the specified threat actor or campaign. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`employs`* | [**`identity`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_wh296fiwpklp) | The threat actor employs the specified individual. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`compromises`* | [**`identity`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_wh296fiwpklp) | The threat actor compromises the specified individual, organization, or group. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`presents-as`* | **`persona`** | The threat actor presents as the specified persona. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`cooperates-with`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | The threat actor cooperates with the specified threat actor. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`part-of`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | The threat actor is part of the specified threat actor. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`participates-in`* | [**`campaign`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_pcpvfz4ik6d6) | The threat actor participates in the specified campaign. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`targets`* | [**`event`**](https://oasis-open.github.io/cti-stix-common-objects/Incident_Extension_Suite.html#event) | The threat actor targets the specified event. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`owns, uses`* | **`channel`** | The threat actor owns or uses the specified channel. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`creates, spreads, uses, amplifies`* | **`narrative`** | The threat actor creates, spreads, uses, or amplifies the specified narrative. |
| [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | *`creates, publishes, amplifies, engages-with`* | [**`media content`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_pcpvfz4ik6d6) | The threat actor creates, publishes, amplifies, or engages with the specified media content. |

The following additional reverse relationships are proposed.

| Source | Type | Target | Description |
| --- | --- | --- | --- |
| [**`identity`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_wh296fiwpklp) | *`employed-by, compromised-by, contracts-with`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | The specified individual, organization, or group is employed by, compromised by or enters into a contract with the threat actor. |
| [**`campaign`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_pcpvfz4ik6d6) | *`sponsored-by`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | The specified campaign is sponsored by the threat actor. |
| [**`incident`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_sczfhw64pjxt) | *`attributed-to`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | The specified incident is attributed to the threat actor. |
| **`media content`** | *`created-by, published-by, amplified-by`* | [**`threat actor`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_k017w16zutw) | The specified media content is created by, published by, or amplified by the threat actor. |

### Example 1: Overt State Influence

The following example represents a state-linked threat actor who engages in overt influence in plain sight.

```json
{
  "type": "threat-actor",
  "spec_version": "2.1",
  "id": "threat-actor--22222222-1111-4111-8111-222222222222",
  "created_by_ref": "identity--bbbbbbbb-cccc-4ddd-8eee-ffffffffffff",
  "created": "2025-12-30T14:05:00.000Z",
  "modified": "2025-12-30T14:05:00.000Z",
  "name": "State Media Propaganda Unit",
  "description": "A state-controlled media arm that openly pushes biased narratives and selective truths to support government objectives.",
  "threat_actor_types": [
    "overt-manipulator"
  ],
  "aliases": [
    "Patriotic Voice Network"
  ],
  "roles": [
    "communicator",
    "content-publisher"
  ],
  "goals": [
    "Shape international perception of state policies",
    "Discredit foreign critics and opposition figures"
  ],
  "sophistication": "advanced",
  "resource_level": "organization",
  "primary_motivation": "ideology",
  "secondary_motivations": [
    "organizational-gain",
    "control"
  ]
}
```

### Example 2: Harassment

The following example represents a loose online collective that targets journalists and activists with racist and misogynistic abuse.

```json
{
  "type": "threat-actor",
  "spec_version": "2.1",
  "id": "threat-actor--33333333-1111-4111-8111-333333333333",
  "created_by_ref": "identity--cccccccc-dddd-4eee-8fff-000000000000",
  "created": "2025-12-30T14:10:00.000Z",
  "modified": "2025-12-30T14:10:00.000Z",
  "name": "Coordinated Hate Harassment Crew",
  "description": "A loose online collective that targets journalists and activists with racist and misogynistic abuse.",
  "threat_actor_types": [
    "cyber-mob"
  ],
  "aliases": [
    "CleanUpTheFeed",
    "RealTruthGuardians"
  ],
  "roles": [
    "content-publisher",
    "content-amplifier"
  ],
  "goals": [
    "Silence targeted journalists through harassment",
    "Intimidate activists and drive them offline"
  ],
  "sophistication": "operational",
  "resource_level": "team",
  "primary_motivation": "dominance",
  "secondary_motivations": [
    "control",
    "hatred",
    "belonging"
  ]
}
```

### Example 3: Scam

The following example represents a criminal network that grooms victims via dating platforms and then conducts large-scale investment and sextortion scams.

```json
{
  "type": "threat-actor",
  "spec_version": "2.1",
  "id": "threat-actor--44444444-1111-4111-8111-444444444444",
  "created_by_ref": "identity--dddddddd-eeee-4fff-8aaa-111111111111",
  "created": "2025-12-30T14:15:00.000Z",
  "modified": "2025-12-30T14:15:00.000Z",
  "name": "Romance Investment Scam Syndicate",
  "description": "A criminal network that grooms victims via dating platforms and then conducts large-scale investment and sextortion scams.",
  "threat_actor_types": [
    "fraudster",
    "crime-syndicate",
    "sextortionist"
  ],
  "aliases": [
    "GoldenHearts Capital Group",
    "PerfectMatch Advisors"
  ],
  "roles": [
    "messenger",
    "content-creator"
  ],
  "goals": [
    "Obtain victims’ trust for financial exploitation",
    "Extort additional payments using intimate material"
  ],
  "sophistication": "advanced",
  "resource_level": "organization",
  "primary_motivation": "personal-financial-gain",
  "secondary_motivations": [
    "organizational-gain"
  ]
}
```

### Example 4: Misinformation

The following example shows someone spreading harmful content without recognizing they are supporting an operation.

```json
{
  "type": "threat-actor",
  "spec_version": "2.1",
  "id": "threat-actor--11111111-1111-4111-8111-111111111111",
  "created_by_ref": "identity--aaaaaaaa-bbbb-4ccc-8ddd-eeeeeeeeeeee",
  "created": "2025-12-30T14:00:00.000Z",
  "modified": "2025-12-30T14:00:00.000Z",
  "name": "Well-Meaning Misinformer",
  "description": "An individual who repeatedly shares misleading health information without malicious intent.",
  "threat_actor_types": [
    "insider-accidental"
  ],
  "aliases": [
    "HelpfulNeighbor42"
  ],
  "roles": [
    "content-amplifier"
  ],
  "goals": [
    "Warn friends and family about perceived risks",
    "Promote home remedies and alternative treatments"
  ],
  "sophistication": "minimal",
  "resource_level": "individual",
  "primary_motivation": "belonging",
  "secondary_motivations": [
    "personal-satisfaction"
  ]
}
```

## Intrusion Set

An Intrusion Set is a grouped set of campaigns, adversarial behaviors and resources with common properties that is believed to be orchestrated by a single organization. The name of this SDO assumes that the organization orchestrating the Intrusion Set is conducting a cyberattack i.e. an unauthorized *intrusion* into a proprietary information environment. When the organization instead is conducting an information operation involving manipulation, abuse or exploitation of information or communication, or of the consumers of information or communication in the public information environment, a new SDO with a more suitable name might be considered, such as “Information Manipulation Set”<sup id="fnref-8"><a href="#fn-8">8</a></sup>.

However, naming one or more new SDOs according to presumed intent would introduce additional subjectivity and complexity. Instead, we propose repurposing the Intrusion Set SDO for the public information environment by adding a new optional property that specifies the context(s) within which the Intrusion Set is (are) observed to be operating:

-   When the Intrusion Set is observed operating within a proprietary information environment, the context is “cyber”. This is the default value.
-   When it is observed operating within the public information environment, the context is “social”, designating the environment in which society openly exchanges information and ideas and engages in debate.
-   When it is observed operating within the physical environment, the context is “physical”, indicating the realm of the tangible, of tactile things and beings.
-   Combinations are possible: an Intrusion Set found interfering with an Industrial Control System would be designated [“cyber”, “physical”]; an Intrusion Set found conducting a hack-and-leak operation would be designated [“cyber”, “social”]<sup id="fnref-9"><a href="#fn-9">9</a></sup>.

When an Intrusion Set operates within a “social” context, the resources within it can include channels, narratives, media content, and personas, represented respectively by the Channel SDO, the Narrative SDO, the Media Content SCO, and the Persona SDO.

### Properties

The following additional properties are recommended.

| Property Name | Type | Description |
| --- | --- | --- |
| **context** (optional) | **`list of type`** [**`enum`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_v9k64f8djur1) | The context within which the intrusion set is observed to be operating.  This property SHOULD be set if the object is observed operating outside a proprietary information environment. The values of this property MUST come from the [**`context-enum`**](#_heading=h.fw23ut33ivmj) enumeration. If no value is provided, then the context should be considered to default to “cyber”. |

### Vocabularies

-   We recommend the creation of a new enumeration [**`context-enum`**](#_heading=h.fw23ut33ivmj) with values “cyber” (default), “social”, and “physical”. See Context Enumeration for details.
-   We recommend the following new entries to Attack Motivation Vocabulary [**`attack-motivation-ov`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_dmb1khqsn650): “Belonging”, “Control”, “Superiority”, “Adulation”, “Outrage”, “Revenge”, “Spite”, “Hatred”. See Attack Motivation Vocabulary for details.

### Relationships

The following additional relationships are proposed.

| Source | Type | Target | Description |
| --- | --- | --- | --- |
| [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | *`impersonates`* | [**`identity`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_wh296fiwpklp) | The intrusion set impersonates the specified individual, organization, or group. |
| [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | *`presents-as`* | **`persona`** | The intrusion set presents as the specified persona. |
| [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | *`targets`* | [**`event`**](https://oasis-open.github.io/cti-stix-common-objects/Incident_Extension_Suite.html#event) | The intrusion set targets the specified event. |
| [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | *`owns, uses`* | **`channel`** | The intrusion set owns or uses the specified channel. |
| [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | *`creates, spreads, uses, amplifies`* | **`narrative`** | The intrusion set creates, spreads, uses, or amplifies the specified narrative. |
| [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | *`creates, publishes, amplifies, engages-with`* | **`media content`** | The intrusion set creates, publishes, amplifies, or engages with the specified media content. |

The following additional reverse relationships are proposed.

| Source | Type | Target | Description |
| --- | --- | --- | --- |
| [**`incident`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_sczfhw64pjxt) | *`attributed-to`* | [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | The specified incident is attributed to the intrusion set. |
| **`media content`** | *`created-by, published-by, amplified-by`* | [**`intrusion set`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_5ol9xlbbnrdn) | The specified media content is created by, published by, or amplified by the intrusion set. |

### Example 5: Gender-Based Violence

```json
{
  "type": "intrusion-set",
  "spec_version": "2.1",
  "id": "intrusion-set--77777777-8888-5333-9444-222222222222",
  "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
  "created": "2025-12-30T14:31:00.000Z",
  "modified": "2025-12-30T14:31:00.000Z",
  "name": "Gender-Based-Violence-Abuse-Set-62",
  "description": "Set of TTPs and resources targeting LGBTQ+ communities in the Balkans with hateful rhetoric and violent acts.",
  "first_seen": "2025-08-01T00:00:00.000Z",
  "last_seen": "2025-11-30T23:59:59.000Z",
  "goals": [
    "Spread fear within the LGBTQ community",
    "Establish male dominance in society",
    "Cause physical harm to targeted individuals"
  ],
  "resource_level": "organization",
  "primary_motivation": "dominance",
  "secondary_motivations": [
    "hatred"
  ],
  "context": [
    "social",
    "physical"
  ]
}
```

## Integrated Hypothetical Example

The following hypothetical example illustrates the use of some of the new properties, relationships, and vocabularies. It models an operation which combines disinformation, hate speech, and impersonation fraud to target a local election and its supporters. The STIX bundle is followed by a knowledge graph built with the STIX Visualizer<sup id="fnref-10"><a href="#fn-10">10</a></sup>.

### STIX Bundle

```json
{
  "type": "bundle",
  "id": "bundle--00000000-0000-4000-8000-000000000000",
  "objects": [
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:30:00.000Z",
      "modified": "2025-12-30T14:30:00.000Z",
      "name": "DAD-CDM Example CTI Producer",
      "description": "Synthetic CTI producer identity used as created_by_ref for this bundle.",
      "identity_class": "organization",
      "sectors": [
        "technology",
        "non-profit"
      ]
    },
    {
      "type": "campaign",
      "spec_version": "2.1",
      "id": "campaign--11111111-2222-3333-4444-555555555555",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:31:00.000Z",
      "modified": "2025-12-30T14:31:00.000Z",
      "name": "Operation Divided Town",
      "description": "Coordinated online operation combining disinformation, hate harassment, and fraud targeting a local election and its supporters.",
      "first_seen": "2025-08-01T00:00:00.000Z",
      "last_seen": "2025-11-30T23:59:59.000Z",
      "objective": "Undermine trust in local election processes and exploit community divisions for financial gain."
    },
    {
      "type": "intrusion-set",
      "spec_version": "2.1",
      "id": "intrusion-set--99999999-1111-4222-8333-999999999999",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:31:00.000Z",
      "modified": "2025-12-30T14:31:00.000Z",
      "name": "The Great Divider",
      "description": "Repeated use of disinformation, hate harassment, and fraud to create division in targeted communities.",
      "first_seen": "2025-08-01T00:00:00.000Z",
      "last_seen": "2025-11-30T23:59:59.000Z",
      "goals": [
        "Decrease trust in election results nationwide",
        "Intimidate activists and journalists",
        "Exploit vulnerable supporters for financial gain"
      ],
      "resource_level": "organization",
      "primary_motivation": "ideology",
      "secondary_motivations": [
        "organizational-gain"
      ],
      "context": [
        "cyber",
        "social"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--bbbb1111-2222-4333-8444-bbbbbbbbbbbb",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:32:00.000Z",
      "modified": "2025-12-30T14:32:00.000Z",
      "name": "Civic Health Alliance",
      "description": "Non-profit organization targeted by Operation Divided Town.",
      "identity_class": "organization",
      "sectors": [
        "healthcare",
        "non-profit"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--cccc1111-2222-4333-8444-cccccccccccc",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:32:30.000Z",
      "modified": "2025-12-30T14:32:30.000Z",
      "name": "Local Election Commission",
      "description": "Local election authority targeted by narratives about fraud and illegitimacy.",
      "identity_class": "organization",
      "sectors": [
        "government-local"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--dddd1111-2222-4333-8444-dddddddddddd",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:33:00.000Z",
      "modified": "2025-12-30T14:33:00.000Z",
      "name": "Town News",
      "description": "Local independent news organization",
      "identity_class": "organization",
      "roles": [
        "media-outlet"
      ],
      "sectors": [
        "communications"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--eeee1111-2222-4333-8444-eeeeeeeeeeee",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:33:30.000Z",
      "modified": "2025-12-30T14:33:30.000Z",
      "name": "PatriotInvestor",
      "description": "Patriotic investment coach encouraging investment in American enterprises",
      "identity_class": "individual",
      "aliases": [
        "Heartland Wealth Adviser"
      ],
      "roles": [
        "expert"
      ],
      "sectors": [
        "financial-services"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--77771111-2222-4333-8444-777777777777",
      "created": "2025-12-31T16:10:00.000Z",
      "modified": "2025-12-31T16:10:00.000Z",
      "name": "Famous Handsome Actor",
      "description": "Well-known male actor and eligible bachelor",
      "identity_class": "individual",
      "sectors": [
        "entertainment"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--ffff1111-2222-4333-8444-ffffffffffff",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:34:00.000Z",
      "modified": "2025-12-30T14:34:00.000Z",
      "name": "Town Bank",
      "description": "Local bank whose brand is impersonated by the fraudster syndicate.",
      "identity_class": "organization",
      "roles": [
        "offline-service-provider"
      ],
      "sectors": [
        "financial-services"
      ]
    },
    {
      "type": "threat-actor",
      "spec_version": "2.1",
      "id": "threat-actor--11111111-1111-4111-8111-111111111111",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:35:00.000Z",
      "modified": "2025-12-30T14:35:00.000Z",
      "name": "Well-Meaning Misinformer",
      "description": "Individual who repeatedly shares misleading election rumors without malicious intent.",
      "threat_actor_types": [
        "insider-accidental"
      ],
      "aliases": [
        "ConcernedCitizen89"
      ],
      "roles": [
        "content-amplifier"
      ],
      "goals": [
        "Warn neighbors about perceived election irregularities",
        "Promote alternative vote-counting narratives"
      ],
      "sophistication": "minimal",
      "resource_level": "individual",
      "primary_motivation": "belonging",
      "secondary_motivations": [
        "personal-satisfaction"
      ]
    },
    {
      "type": "threat-actor",
      "spec_version": "2.1",
      "id": "threat-actor--22222222-1111-4111-8111-222222222222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:36:00.000Z",
      "modified": "2025-12-30T14:36:00.000Z",
      "name": "State-Aligned Influence Cell",
      "description": "Covert manipulation team that seeds divisive narratives through cut-out brands.",
      "threat_actor_types": [
        "covert-manipulator",
        "influence-for-hire-provider"
      ],
      "aliases": [
        "SilverLinden Consulting"
      ],
      "roles": [
        "content-creator",
        "content-publisher",
        "content-amplifier"
      ],
      "goals": [
        "Undermine trust in the Local Election Commission",
        "Increase societal distrust and polarization"
      ],
      "sophistication": "advanced",
      "resource_level": "organization",
      "primary_motivation": "organizational-gain",
      "secondary_motivations": [
        "ideology",
        "control"
      ]
    },
    {
      "type": "threat-actor",
      "spec_version": "2.1",
      "id": "threat-actor--33333333-1111-4111-8111-333333333333",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:37:00.000Z",
      "modified": "2025-12-30T14:37:00.000Z",
      "name": "Hate Harassment Crew",
      "description": "Loose online collective targeting activists and election workers with racist and misogynistic abuse.",
      "threat_actor_types": [
        "cyber-mob"
      ],
      "aliases": [
        "RealVoicesOfTown"
      ],
      "roles": [
        "content-amplifier"
      ],
      "goals": [
        "Drive Civic Health Alliance staff offline through harassment",
        "Intimidate Local Election Commission employees"
      ],
      "sophistication": "operational",
      "resource_level": "team",
      "primary_motivation": "personal-satisfaction",
      "secondary_motivations": [
        "personal-gain",
        "hatred"
      ]
    },
    {
      "type": "threat-actor",
      "spec_version": "2.1",
      "id": "threat-actor--44444444-1111-4111-8111-444444444444",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:38:00.000Z",
      "modified": "2025-12-30T14:38:00.000Z",
      "name": "Patriot Investment Syndicate",
      "description": "Criminal group that grooms victims via fake patriotic dating and investment schemes.",
      "threat_actor_types": [
        "fraudster",
        "crime-syndicate",
        "sextortionist"
      ],
      "aliases": [
        "Heartland Wealth Circle"
      ],
      "roles": [
        "messenger",
        "content-creator"
      ],
      "goals": [
        "Extract savings from local supporters via fraudulent investments",
        "Blackmail victims using intimate content collected during grooming"
      ],
      "sophistication": "advanced",
      "resource_level": "organization",
      "primary_motivation": "personal-gain",
      "secondary_motivations": [
        "organizational-gain"
      ]
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--aaaa2222-3333-4444-8555-aaaaaaaa2222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:39:00.000Z",
      "modified": "2025-12-30T14:39:00.000Z",
      "relationship_type": "participates-in",
      "description": "The misinformer plays an unwitting supporting role in Operation Divided Town.",
      "source_ref": "threat-actor--11111111-1111-4111-8111-111111111111",
      "target_ref": "campaign--11111111-2222-3333-4444-555555555555"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--33333333-4444-5555-9666-zzzzzzzz3333",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:39:30.000Z",
      "modified": "2025-12-30T14:39:30.000Z",
      "relationship_type": "attributed-to",
      "description": "The Operation Divided Town campaign is attributed to The Great Divider intrusion set.",
      "source_ref": "campaign--11111111-2222-3333-4444-555555555555",
      "target_ref": "intrusion-set--99999999-1111-4222-8333-999999999999"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--bbbb2222-3333-4444-8555-bbbbbbbb2222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:39:30.000Z",
      "modified": "2025-12-30T14:39:30.000Z",
      "relationship_type": "attributed-to",
      "description": "The state-aligned influence cell orchestrates The Great Divider intrusion set.",
      "source_ref": "intrusion-set--99999999-1111-4222-8333-999999999999",
      "target_ref": "threat-actor--22222222-1111-4111-8111-222222222222"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--cccc2222-3333-4444-8555-cccccccc2222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:40:00.000Z",
      "modified": "2025-12-30T14:40:00.000Z",
      "relationship_type": "participates-in",
      "description": "The hate harassment crew participates in Operation Divided Town by targeting activists and officials.",
      "source_ref": "threat-actor--33333333-1111-4111-8111-333333333333",
      "target_ref": "campaign--11111111-2222-3333-4444-555555555555"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--dddd2222-3333-4444-8555-dddddddd2222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:40:30.000Z",
      "modified": "2025-12-30T14:40:30.000Z",
      "relationship_type": "participates-in",
      "description": "The fraud syndicate participates in Operation Divided Town by exploiting victims drawn in through campaign narratives.",
      "source_ref": "threat-actor--44444444-1111-4111-8111-444444444444",
      "target_ref": "campaign--11111111-2222-3333-4444-555555555555"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--eeee2222-3333-4444-8555-eeeeeeee2222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:41:00.000Z",
      "modified": "2025-12-30T14:41:00.000Z",
      "relationship_type": "impersonates",
      "description": "The intrusion set The Great Divider masquerades as the Town News organization.",
      "source_ref": "intrusion-set--99999999-1111-4222-8333-999999999999",
      "target_ref": "identity--dddd1111-2222-4333-8444-dddddddddddd"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--ffff2222-3333-4444-8555-ffffffff2222",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:41:30.000Z",
      "modified": "2025-12-30T14:41:30.000Z",
      "relationship_type": "impersonates",
      "description": "The fraud syndicate impersonates PatriotInvestor.",
      "source_ref": "threat-actor--44444444-1111-4111-8111-444444444444",
      "target_ref": "identity--eeee1111-2222-4333-8444-eeeeeeeeeeee"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--88882222-3333-4444-8555-888888888888",
      "created": "2025-12-31T16:12:00.000Z",
      "modified": "2025-12-31T16:12:00.000Z",
      "relationship_type": "impersonates",
      "description": "The Patriot Investment Syndicate impersonates the Famous Handsome Actor.",
      "source_ref": "threat-actor--44444444-1111-4111-8111-444444444444",
      "target_ref": "identity--77771111-2222-4333-8444-777777777777"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--11112222-3333-4444-8555-121212121212",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:42:00.000Z",
      "modified": "2025-12-30T14:42:00.000Z",
      "relationship_type": "targets",
      "description": "Operation Divided Town targets the Civic Health Alliance.",
      "source_ref": "campaign--11111111-2222-3333-4444-555555555555",
      "target_ref": "identity--bbbb1111-2222-4333-8444-bbbbbbbbbbbb"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--99992222-3333-4444-8555-999999999999",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T15:00:00.000Z",
      "modified": "2025-12-30T15:00:00.000Z",
      "relationship_type": "impersonates",
      "description": "The Patriot Investment Syndicate impersonates Town Bank in phishing and scam communications.",
      "source_ref": "threat-actor--44444444-1111-4111-8111-444444444444",
      "target_ref": "identity--ffff1111-2222-4333-8444-ffffffffffff"
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--22222222-3333-4444-8555-232323232323",
      "created_by_ref": "identity--aaaa1111-2222-4333-8444-aaaaaaaaaaaa",
      "created": "2025-12-30T14:42:30.000Z",
      "modified": "2025-12-30T14:42:30.000Z",
      "relationship_type": "targets",
      "description": "Operation Divided Town targets the Local Election Commission.",
      "source_ref": "campaign--11111111-2222-3333-4444-555555555555",
      "target_ref": "identity--cccc1111-2222-4333-8444-cccccccccccc"
    }
  ]
}
```

### Knowledge Graph

<p align="center"><img src="media/af5d52123ab75afa8ff4b314f4f6142d.png" style="max-width: 100%;"></p>

<p align="center"><i>Figure 1 Example Operation Divided Town</i></p>

<p align="center"><img src="media/c23c50a41b98a3375457d7d0dbe01a88.png" style="max-width: 100%;"></p>

## Integrated Real-World Example

The following real-world example illustrates the use of some of the new properties, relationships, and vocabularies. It models a cyber-enabled influence operation called Ghostwriter consisting of two intrusion sets: one responsible for credentials harvesting, the other which publishes inauthentic news articles on hacked websites and amplifies the articles using fabricated and hacked social media accounts<sup id="fnref-11"><a href="#fn-11">11</a></sup>. The STIX bundle is followed by a knowledge graph built with the STIX Visualizer<sup id="fnref-12"><a href="#fn-12">12</a></sup>.

### STIX Bundle

```json
{
  "type": "bundle",
  "id": "bundle--2ddbdc7b-fe4d-5546-9a23-3a658b13e3c2",
  "objects": [
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "name": "DAD-CDM Example CTI Producer",
      "description": "Synthetic CTI producer identity used as created_by_ref for this illustrative bundle. All objects below are SYNTHETIC examples built to demonstrate the proposed Intrusion Set `context` property and are not an authoritative attribution.",
      "identity_class": "organization",
      "sectors": [
        "technology",
        "non-profit"
      ]
    },
    {
      "type": "location",
      "spec_version": "2.1",
      "id": "location--a113f58a-905e-57f2-b43e-e2428f277d39",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Belarus",
      "country": "BY",
      "region": "eastern-europe",
      "description": "Assessed operating location of the cyber-espionage activity (Minsk)."
    },
    {
      "type": "location",
      "spec_version": "2.1",
      "id": "location--c528c619-d9d4-5089-95f5-c7183655be68",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Lithuania",
      "country": "LT",
      "region": "eastern-europe"
    },
    {
      "type": "location",
      "spec_version": "2.1",
      "id": "location--23444787-7aca-5e63-ad12-daf5bd6ea8d1",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Latvia",
      "country": "LV",
      "region": "eastern-europe"
    },
    {
      "type": "location",
      "spec_version": "2.1",
      "id": "location--aa6107f1-2273-5656-9b74-fc993247ba02",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Poland",
      "country": "PL",
      "region": "eastern-europe"
    },
    {
      "type": "location",
      "spec_version": "2.1",
      "id": "location--debb62f3-d176-560f-95a5-8e8eafea341d",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Ukraine",
      "country": "UA",
      "region": "eastern-europe"
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--5c7c88c8-8650-5577-96e9-7f662ad86a9d",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "NATO",
      "description": "Defensive alliance whose presence in Eastern Europe is targeted by hostile narratives.",
      "identity_class": "organization",
      "sectors": [
        "government-national"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--8f26b9e3-09fc-5436-89af-fd61ec34e1d2",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Eastern European Government Officials",
      "description": "Group of officials whose email and social media accounts are targeted for compromise and subsequent abuse to disseminate fabricated content.",
      "identity_class": "group",
      "sectors": [
        "government-national"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--17c90016-06ff-581f-8834-1919834e0978",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Regional News Portal (legitimate)",
      "description": "Legitimate regional news outlet whose website and brand are impersonated/spoofed to lend false credibility to fabricated articles.",
      "identity_class": "organization",
      "roles": [
        "media-outlet"
      ],
      "sectors": [
        "communications"
      ]
    },
    {
      "type": "identity",
      "spec_version": "2.1",
      "id": "identity--4e9616f5-dabf-5aa8-bc87-3f6820304f10",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Trusted Webmail / Social Brand (legitimate)",
      "description": "Legitimate email/social platform brand spoofed in credential-theft (phishing) domains.",
      "identity_class": "organization",
      "sectors": [
        "technology"
      ]
    },
    {
      "type": "threat-actor",
      "spec_version": "2.1",
      "id": "threat-actor--4f48bf24-a600-515f-9826-483465245d28",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Belarus State-Linked Actor",
      "description": "State-linked actor assessed in public reporting to direct or support the activity tracked as GhostWriter / UNC1151. Modeled here as the real-world actor to which the two intrusion sets are attributed. (SYNTHETIC illustrative object.)",
      "threat_actor_types": [
        "nation-state",
        "covert-manipulator"
      ],
      "aliases": [
        "Minsk-aligned operator"
      ],
      "roles": [
        "director"
      ],
      "goals": [
        "Undermine trust in NATO in Eastern Europe",
        "Suppress and discredit political opposition",
        "Destabilize domestic politics of neighboring states"
      ],
      "sophistication": "advanced",
      "resource_level": "government",
      "primary_motivation": "ideology",
      "secondary_motivations": [
        "control",
        "dominance"
      ]
    },
    {
      "type": "intrusion-set",
      "spec_version": "2.1",
      "id": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "UNC1151 (cyber-espionage component)",
      "description": "The cyber-espionage fingerprint: credential-theft domains spoofing trusted email/social brands, spear-phishing, and compromise of email, social media, and website/CMS accounts. Operates within a proprietary information environment, hence context=[\"cyber\"] (also the default). Cooperates with the GhostWriter influence set, to which it supplies access and stolen material. SYNTHETIC example.",
      "aliases": [
        "UNC1151",
        "PUSHCHA"
      ],
      "first_seen": "2017-01-01T00:00:00.000Z",
      "last_seen": "2022-03-31T23:59:59.000Z",
      "goals": [
        "Harvest credentials of targeted officials and outlets",
        "Provide access and stolen material to the influence effort"
      ],
      "resource_level": "government",
      "primary_motivation": "ideology",
      "secondary_motivations": [
        "organizational-gain"
      ],
      "context": [
        "cyber"
      ]
    },
    {
      "type": "intrusion-set",
      "spec_version": "2.1",
      "id": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "GhostWriter (influence component / IMS)",
      "description": "The influence / Information Manipulation Set fingerprint: fabrication of news articles, spoofing of legitimate news websites, operation of inauthentic personas, and dissemination of anti-NATO and COVID-19 narratives. Operates within the public information environment, hence context=[\"social\"]. On its own this set would be regarded as an Information Manipulation Set. Cooperates with UNC1151, which supplies it with compromised access and leaked material. SYNTHETIC example.",
      "aliases": [
        "GhostWriter"
      ],
      "first_seen": "2016-01-01T00:00:00.000Z",
      "last_seen": "2022-03-31T23:59:59.000Z",
      "goals": [
        "Promote narratives critical of NATO's presence in Eastern Europe",
        "Discredit political opposition and sow domestic discord"
      ],
      "resource_level": "government",
      "primary_motivation": "ideology",
      "secondary_motivations": [
        "control"
      ],
      "context": [
        "social"
      ]
    },
    {
      "type": "campaign",
      "spec_version": "2.1",
      "id": "campaign--9e3b644e-cff9-544d-9292-9bd4f09c148f",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Anti-NATO Narrative Wave (illustrative)",
      "description": "Illustrative campaign of fabricated articles and leaked material promoting anti-NATO narratives across Lithuania, Latvia and Poland. SYNTHETIC example.",
      "aliases": [
        "NATO troops / COVID-19 narrative set"
      ],
      "first_seen": "2020-06-01T00:00:00.000Z",
      "last_seen": "2021-12-31T23:59:59.000Z",
      "objective": "Undermine confidence in NATO's military presence in Eastern Europe."
    },
    {
      "type": "attack-pattern",
      "spec_version": "2.1",
      "id": "attack-pattern--a4a4cb11-bf69-5e2d-bc46-7a88ab7b483d",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Phishing for Credentials",
      "description": "Spear-phishing and spoofed login domains to harvest victim credentials.",
      "external_references": [
        {
          "source_name": "mitre-attack",
          "external_id": "T1566",
          "url": "https://attack.mitre.org/techniques/T1566/"
        }
      ]
    },
    {
      "type": "attack-pattern",
      "spec_version": "2.1",
      "id": "attack-pattern--cb89dea0-5e00-57e7-b21a-b360c67b565f",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Compromise Accounts",
      "description": "Compromise of email and social media accounts for access and dissemination.",
      "external_references": [
        {
          "source_name": "mitre-attack",
          "external_id": "T1586",
          "url": "https://attack.mitre.org/techniques/T1586/"
        }
      ]
    },
    {
      "type": "attack-pattern",
      "spec_version": "2.1",
      "id": "attack-pattern--3162d188-c0f5-5f2a-8451-bbfb7851d178",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Develop Inauthentic News Articles",
      "description": "Create false or misleading news articles aligned to campaign goals or narratives.",
      "external_references": [
        {
          "source_name": "DISARM",
          "external_id": "T0085.003",
          "url": "https://github.com/DISARMFoundation/DISARMframeworks-17/blob/main/generated_pages/techniques/T0085.003.md"
        }
      ]
    },
    {
      "type": "attack-pattern",
      "spec_version": "2.1",
      "id": "attack-pattern--2130de41-8375-5e93-8b3d-7509b92702ab",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Impersonated Persona",
      "description": "Threat actors may impersonate existing individuals or institutions to conceal their network identity, add legitimacy to content, or harm the impersonated target’s reputation. This Technique covers situations where an actor presents themselves as another existing individual or institution.",
      "external_references": [
        {
          "source_name": "DISARM",
          "external_id": "T0143.003",
          "url": "https://github.com/DISARMFoundation/DISARMframeworks-17/blob/main/generated_pages/techniques/T0143.003.md"
        }
      ]
    },
    {
      "type": "attack-pattern",
      "spec_version": "2.1",
      "id": "attack-pattern--2d459671-1a0b-5095-ab81-61af7a738fe7",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "name": "Fabricated Persona",
      "description": "An individual or institution pretending to have a persona without any legitimate claim to that persona is presenting a fabricated persona, such as a person who presents themselves as a member of a country’s military without having worked in any capacity with the military (T0143.002: Fabricated Persona, T0097.105: Military Personnel).",
      "external_references": [
        {
          "source_name": "DISARM",
          "external_id": "T0143.002",
          "url": "https://github.com/DISARMFoundation/DISARMframeworks-17/blob/main/generated_pages/techniques/T0143.002.md"
        }
      ]
    },
    {
      "type": "attack-pattern",
      "spec_version": "2.1",
      "id": "attack-pattern--5f81e69a-b33c-5213-8fc7-a819478b3608",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "name": "Journalist Persona",
      "description": "A fabricated persona presenting as a reporter or journalist delivering news, conducting interviews, or running investigations, used to give an influence operation the appearance of legitimacy. Here the inauthentic personas operated by the influence set are invented journalist personas (fabrication), not impersonation of a specific real journalist.",
      "external_references": [
        {
          "source_name": "DISARM",
          "external_id": "T0097.102",
          "url": "https://github.com/DISARMFoundation/DISARMframeworks-17/blob/main/generated_pages/techniques/T0097.102.md"
        }
      ]
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--3463565c-efa3-5941-b07f-79361e30ae3d",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "related-to",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "description": "The UNC1151 cyber-espionage set cooperates with the GhostWriter influence set, supplying it with compromised access and leaked material (cyber-enabled influence)."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--8342c575-22ad-532f-bbbd-60cb5dd28ee2",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "attributed-to",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "threat-actor--4f48bf24-a600-515f-9826-483465245d28",
      "description": "The UNC1151 cyber-espionage set is attributed to the Belarus state-linked actor."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--b7ec0f61-c9e9-5148-9df6-1ca60ee65969",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "attributed-to",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "threat-actor--4f48bf24-a600-515f-9826-483465245d28",
      "description": "The GhostWriter influence set is attributed to the Belarus state-linked actor."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--863ccef5-72ac-5f65-8b01-b30c4b9b6b35",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "attributed-to",
      "source_ref": "campaign--9e3b644e-cff9-544d-9292-9bd4f09c148f",
      "target_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "description": "The anti-NATO narrative campaign is attributed to the GhostWriter influence set."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--793f2fe7-c3ff-5df3-9363-06a9edca8eb5",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "uses",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "attack-pattern--a4a4cb11-bf69-5e2d-bc46-7a88ab7b483d",
      "description": "UNC1151 uses credential phishing."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--6944e0d9-8a86-52cc-a38b-5537ccd8df9d",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "uses",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "attack-pattern--cb89dea0-5e00-57e7-b21a-b360c67b565f",
      "description": "UNC1151 compromises email and social media accounts."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--b1db61cc-c74d-5138-b41a-96f8b5723aec",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "uses",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "attack-pattern--3162d188-c0f5-5f2a-8451-bbfb7851d178",
      "description": "GhostWriter fabricates news content."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--bada8305-740e-56e4-ae7e-7bd39dbb807e",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "uses",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "attack-pattern--2130de41-8375-5e93-8b3d-7509b92702ab",
      "description": "GhostWriter spoofs legitimate news sites."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--22ea90c0-7446-511b-a45c-43c06e028b6a",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "uses",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "attack-pattern--2d459671-1a0b-5095-ab81-61af7a738fe7",
      "description": "GhostWriter operates fabricated personas."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--ef975304-942a-5cf0-8584-e3c5b53245ff",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "relationship_type": "uses",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "attack-pattern--5f81e69a-b33c-5213-8fc7-a819478b3608",
      "description": "The influence set fabricates and operates journalist personas to lend false legitimacy to its content."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--3c58e77f-e565-5697-abd3-b08c422fa8a2",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "originates-from",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "location--a113f58a-905e-57f2-b43e-e2428f277d39",
      "description": "The cyber-espionage component is assessed to originate from Belarus (Minsk)."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--78200e9d-afd6-52a7-89ba-cfc8df177649",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "targets",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "identity--5c7c88c8-8650-5577-96e9-7f662ad86a9d",
      "description": "The influence set targets perceptions of NATO."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--948906ce-2545-53ef-8b82-962a2bc30365",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "targets",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "location--c528c619-d9d4-5089-95f5-c7183655be68",
      "description": "The influence set targets audiences in Lithuania."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--d8a4d273-ca20-5e38-b055-e885fe4d9fbe",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "targets",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "location--23444787-7aca-5e63-ad12-daf5bd6ea8d1",
      "description": "The influence set targets audiences in Latvia."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--4565ce02-50a2-5cdc-bc35-c53a2044e2b9",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "targets",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "location--aa6107f1-2273-5656-9b74-fc993247ba02",
      "description": "The influence set targets audiences in Poland."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--f4f11fed-e59e-51d0-9543-aab0ef76890a",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "targets",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "location--debb62f3-d176-560f-95a5-8e8eafea341d",
      "description": "The influence set targets audiences in Ukraine."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--35729891-7d22-5240-9dab-8be58f2f55af",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "targets",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "identity--8f26b9e3-09fc-5436-89af-fd61ec34e1d2",
      "description": "The cyber set targets officials' accounts for compromise."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--c6ae9ee3-8ab3-54fe-a864-224878c1a30e",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "impersonates",
      "source_ref": "intrusion-set--8f5eced7-e2a6-5958-a407-7413a05f600c",
      "target_ref": "identity--17c90016-06ff-581f-8834-1919834e0978",
      "description": "[proposed] The influence set impersonates a legitimate regional news outlet."
    },
    {
      "type": "relationship",
      "spec_version": "2.1",
      "id": "relationship--fc900325-8365-5674-b489-dbd6f224a234",
      "created": "2026-06-15T12:00:00.000Z",
      "modified": "2026-06-15T12:00:00.000Z",
      "created_by_ref": "identity--a362e97f-4e2c-525a-b16a-ebcd139e8368",
      "relationship_type": "impersonates",
      "source_ref": "intrusion-set--85c804b2-fa95-59c1-a9fc-201bacdaf040",
      "target_ref": "identity--4e9616f5-dabf-5aa8-bc87-3f6820304f10",
      "description": "[proposed] The cyber set impersonates a trusted email/social brand in credential-theft domains."
    }
  ]
}
```

### Knowledge Graph

<p align="center"><img src="media/46469b522ad99c16618b31cf075a28c3.png" style="max-width: 100%;"></p>

<p align="center"><i>Figure 2 Example Ghostwriter</i></p>

<p align="center"><img src="media/b7c27ea30825ee00ca025690a1f195b4.png" style="max-width: 100%;"></p>

## Vocabularies

### Threat Actor Type Vocabulary

The following additional threat actor types are proposed for threats to the public information environment. These are excerpted from the full analysis available in the supporting document *Expanding Intel’s Threat Agent Library to Accommodate FIMI and Other Online Harms.*

**Type Name:** threat-actor-type-ov

| Vocabulary Value | Description |
| --- | --- |
| **Manipulative** | |
| overt-manipulator | An individual or organization who openly uses persuasive content or pressure to steer others’ beliefs or behavior in their preferred direction. |
| covert-manipulator | An individual or organization which secretly shapes others’ perceptions or decisions through deception, hidden agendas, or disguised sources. |
| influence-for-hire-provider | An individual or organization that sells manipulation services - such as coordinated messaging, astroturfing, or fake engagement - on behalf of paying clients. |
| **Abusive** | |
| hate-group | An organized collective that persistently targets people based on protected characteristics with hostile, dehumanizing, or exclusionary messages and actions. |
| cyber-mob | A loosely coordinated crowd of online actors who collectively participate in sustained harassment, pile-ons, or shaming against a person or group. |
| cyber-bully | Someone who repeatedly targets specific individuals online with hostile or degrading behavior intended to cause psychological or social harm. |
| **Exploitative** | |
| fraudster | Someone who systematically deceives others in digital environments to obtain money, assets, data, or advantages they are not entitled to. |
| cyber-stalker | Someone who persistently monitors, contacts, or intrudes on a target’s digital and often physical life in ways that undermine their privacy, safety, or autonomy. |
| extortionist | Someone who uses threats - such as exposure, damage, or disruption - to coerce victims into providing money, information, or other concessions. |

### Threat Actor Role Vocabulary

The following additional threat actor roles are proposed for designating specific roles that threat actors can play in an information operation, influence or hate campaign.

**Type Name:** threat-actor-role-ov

| Vocabulary Value | Description |
| --- | --- |
| public-communicator | The threat actor who is responsible for openly communicating a threat actor’s or campaign’s narratives. Includes diplomats, spokespersons, speakers, delegates, representatives. |
| private-messenger | The threat actor who handles private communication (texting, email, speech) with potential and actual supporters and targets. |
| content-creator | The threat actor who creates content to support a campaign narrative. |
| content-publisher | The threat actor who publishes content generated by the content creator, perhaps on the web or via a social media post. |
| content-amplifier | The threat actor who amplifies content posted by the content publisher, perhaps by sharing it, republishing it, reposting it, or engaging with it in some way. |

### Attack Motivation Vocabulary

The following additional attack motivations are proposed to describe the reasons and drivers behind threats to the public information environment. These are excerpted from the full analysis available in the supporting document *Expanding Intel’s Threat Agent Library to Accommodate FIMI and Other Online Harms.*

**Type Name:** attack-motivation-ov

| Vocabulary Value | Description |
| --- | --- |
| belonging | The emotional state of feeling accepted, valued, and respected by a larger group. |
| control | The power to influence or direct people's behavior or the course of events. |
| superiority | The state of being better, higher, greater, or more powerful than others in some way. |
| adulation | Extreme, excessive, or uncritical praise, admiration, or devotion. |
| outrage | An intense feeling of indignation triggered by a perceived injustice or moral violation. |
| revenge | A vindictive desire to inflict punishment or harm in retaliation for a perceived wrong. |
| spite | A petty feeling of envy or resentment expressed through harassment or ill will. |
| hatred | An extreme dislike, aversion, or ill will toward a person, group, or object. |

## Enumerations

### Context Enumeration

The following taxonomy is proposed for designating the possible values for context. The context is the environment within which the object is observed.

**Type Name:** context-enum

The context vocabulary is used in the following SDOs:

-   Event
-   Intrusion Set

| Vocabulary Value | Description |
| --- | --- |
| cyber | The object is observed within a proprietary information environment and may indicate a threat to cybersecurity e.g. ransomware, data-exfiltration, denial-of-service.   This is the default value if the property context is not set. |
| social | The object is observed within the public information environment and may indicate a threat to the public information environment e.g. disinformation, hate-speech, click-bait. |
| physical | The object is observed within the physical environment and may indicate a threat in the real world e.g. an intrusion set intruding into a proprietary physical space, or it may be a real-world object that provides the context for an information operation e.g. a real-world event such as a hurricane, an international-summit, a terrorist-attack. |

## 

---

## Notes

<sup id="fn-1">1</sup> [https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_32j232tfvtly](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_32j232tfvtly) [↩](#fnref-1)

<sup id="fn-2">2</sup> [https://www.disinfo.eu/building-a-common-operational-picture-of-fimi/](https://www.disinfo.eu/building-a-common-operational-picture-of-fimi/) [↩](#fnref-2)

<sup id="fn-3">3</sup> [https://www.disinfo.eu/wp-content/uploads/2026/01/20260115_building-a-common-operational-picture-of-FIMI_01.pdf](https://www.disinfo.eu/wp-content/uploads/2026/01/20260115_building-a-common-operational-picture-of-FIMI_01.pdf) [↩](#fnref-3)

<sup id="fn-4">4</sup> [https://oasis-open.github.io/cti-stix-common-objects/Incident_Extension_Suite.html](https://oasis-open.github.io/cti-stix-common-objects/Incident_Extension_Suite.html) [↩](#fnref-4)

<sup id="fn-5">5</sup> We are grateful to Jean-Philippe Salles for providing us with Filigran’s internal documentation on all the SROs within OpenCTI. [↩](#fnref-5)

<sup id="fn-6">6</sup> [https://github.com/DAD-CDM/Contributions/pull/5](https://github.com/DAD-CDM/Contributions/pull/5) [↩](#fnref-6)

<sup id="fn-7">7</sup> [https://static1.squarespace.com/static/5a111571d0e628a8679b6b6c/t/5c379b84b8a045a55b983f3a/1547148165167/Intel+-+Threat+Agent+Library+Helps+Identify+Information+Security+Risks.pdf](https://static1.squarespace.com/static/5a111571d0e628a8679b6b6c/t/5c379b84b8a045a55b983f3a/1547148165167/Intel+-+Threat+Agent+Library+Helps+Identify+Information+Security+Risks.pdf) [↩](#fnref-7)

<sup id="fn-8">8</sup> VIGINUM defines an Information Manipulation Set as “a collection of adversarial behaviors, tools, and Tactics, Techniques, and Procedures (TTPs) presumed to be linked to the same Threat Actor or group of Threat Actors, which may be unknown. One or more IMSs can be technically attributed to a threat actor, and one or more campaigns can be attributed to an IMS. An IMS should not be confused with a Threat Actor, which may consist of a State, organization or individual. Finally, an IMS can be used to conduct information campaigns, which can be broken down into several information operations (or incidents)”. VIGINUM defines strict criteria for an IMS based on clandestinity and coordination. See [https://www.sgdsn.gouv.fr/files/files/Publications/20260122_NP_TLP-CLEAR_SGDSN_VIGINUM_IMS_0.pdf](https://www.sgdsn.gouv.fr/files/files/Publications/20260122_NP_TLP-CLEAR_SGDSN_VIGINUM_IMS_0.pdf). [↩](#fnref-8)

<sup id="fn-9">9</sup> An alternative approach we considered was to define a new property “intent” for the Intrusion Set SDO, having an associated enumeration with values such as “intrusion”, “manipulation”, “abuse”, or “exploitation”, but establishing intent often remains elusive. Moreover, documenting the environment in which behaviors and resources are observed is more objective and will lead to more consistent coding by analysts. [↩](#fnref-9)

<sup id="fn-10">10</sup> [https://oasis-open.github.io/cti-stix-visualization](https://oasis-open.github.io/cti-stix-visualization) [↩](#fnref-10)

<sup id="fn-11">11</sup> See, for example, [https://www.hybridcoe.fi/wp-content/uploads/2022/11/20221129_Hybrid_CoE_Research_Report_7_Disarm_WEB.pdf](https://www.hybridcoe.fi/wp-content/uploads/2022/11/20221129_Hybrid_CoE_Research_Report_7_Disarm_WEB.pdf) [↩](#fnref-11)

<sup id="fn-12">12</sup> [https://oasis-open.github.io/cti-stix-visualization](https://oasis-open.github.io/cti-stix-visualization) [↩](#fnref-12)
