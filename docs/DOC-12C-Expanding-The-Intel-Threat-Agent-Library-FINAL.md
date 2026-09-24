## Expanding Intel’s Threat Agent Library to Accommodate FIMI and Other Online Harms

Table of Contents

- [Threat Agent Attributes](#threat-agent-attributes)
  - [Intent](#intent)
  - [Access](#access)
  - [Outcome](#outcome)
  - [Limits](#limits)
  - [Resource](#resource)
  - [Skill Level](#skill-level)
  - [Objective](#objective)
  - [Visibility](#visibility)
  - [Motivation](#motivation)
- [New Threat Agents](#new-threat-agents)

### 

### Threat Agent Attributes

The original research that formed the basis of the properties, relationships and vocabularies of the threat actor SDO was carried out by Tim Casey’s team at Intel. The seminal paper in 2007 introduced Intel’s threat taxonomy and Threat Agent Library<sup id="fnref-1"><a href="#fn-1">1</a></sup> of 22 threat archetypes based upon eight attributes. A follow-up paper in 2015 extended the taxonomy to include a ninth attribute: threat actor motivation<sup id="fnref-2"><a href="#fn-2">2</a></sup>.

In the spirit of Intel’s original research, this paper proposes to extend the taxonomy further with additional values for these nine attributes which can help to describe threat agents in the public information space. The original Intel Threat Agent Library was created from the following set of defining attributes: intent, access, outcome, limits, resource, skill level, objective, and visibility. Intel added motivation as a defining attribute in 2015. In extending the library to include threat agents that pose a threat to the public information environment, we have maintained the same set of attributes, but we have added new values where appropriate.

#### Intent

For cyber threats this was a binary choice between “hostile” or “non-hostile”. For threats to the public information environment, we propose three new categories of intent: “manipulative”, “abusive”, and “exploitative”<sup id="fnref-3"><a href="#fn-3">3</a></sup>. Agents with manipulative intent aim to manipulate their victims in some way; this is the domain of influence operations, FIMI, and disinformation. Agents with abusive intent aim to inflict harm upon their victims in some way: this is the domain of extreme discrimination, hate crimes, and intimidation. Agents with exploitative intent aim to exploit their victims in some way for some personal gain: this is the domain of fraudsters and sexual predators.

Given the composite nature of many threats, the five categories of intent are not mutually exclusive. For example, the archetypes “Civil Activist”, “Data Miner”, “Mobster”, “Radical Activist”, “Sensationalist”, and “Terrorist”, which were categorized in 2007 under “hostile”, could arguably now be regarded primarily as threats to the public information environment and placed into one of the corresponding newly proposed categories. For simplicity and backwards compatibility, however, we have not recategorized these archetypes.

As it turns out, some of these archetypes did not make it into the STIX 2.1 threat agent type open vocabulary. What is important to recognize is that the following values that DID make it into that vocabulary can be regarded, not just as traditional cyber threats to proprietary information environments, but also as threats to the public information environment: “activist”, “crime-syndicate”, “criminal”, “nation-state”, “sensationalist”, “terrorist”. In addition, “non-hostile” threats also exist in the public information environment, such as actors who engage in misinformation or systemic bigotry, but do not have malicious intent. In summary, defenders of the public information environment who use the extended threat agent library should consider all five categories of intent when codifying threats.

*Feedback*: Tim Casey made the very valid point that the new categories “manipulative”, “abusive”, and “exploitative” should all be regarded as subsets of “hostile”. If analysts choose to arrange the taxonomy in this way, then a distinction needs to be made between these new sub-categories and “intrusive” i.e. intruding into a proprietary information environment.

#### Access

For cyber threats this is understood to be the extent to which the threat agent has or can generate access to the company’s assets. The choice is binary: the agent either enjoys or gains full *internal* access (such as trusted insiders and spies) or retains only limited *external* access (such as competitors and activists). For the public information environment, we can think of access more in terms of the *opportunity* a specific threat agent needs to have or create to manipulate, abuse or exploit their targets according to their distinct persona.

Opportunities tend to exist where there are vulnerabilities in the target or the target’s information environment that can be exploited. For example, covert manipulators, influence for hire providers, and agents provocateurs may infiltrate their targets, such as closed or gated online communities, by exploiting human trust bias and platform anonymity features, to achieve their manipulative goals. Similarly, a doxxer may have or create the opportunity to steal inside information on their target, by exploiting a human target’s trust bias or a software or configuration vulnerability in the target’s computer system. And scammers and sexual predators may get close enough to their target to exploit them by preying on their fears, desires, or loneliness. Opportunity is one element of the threat triangle: for a threat to exist, there must be a combination of intent, capability and opportunity<sup id="fnref-4"><a href="#fn-4">4</a></sup>.

#### Outcome

Outcome is defined in the original 2007 paper as the intended or actual result of an attack. While the actual result usually equates to the attacker’s primary goal, sometimes it can be an unintended consequence, or, in the case of non-hostile agents, the result may be unintentional. Of the original five outcomes, “Tech Advantage” results from illicit improvement of a technical product or capability, usually through IP theft. It is neither a desired outcome nor unintended consequence of any of the new threat archetypes, and so this outcome is not shown in the new matrix of additional threat agents pertaining to the public information environment. The remaining four original outcomes, “Acquisition/Theft”, “Business Advantage”, “Damage”, and “Embarrassment” DO apply in varying degrees to the new archetypes, as shown in the new matrix.

We propose adding five new values for this attribute to capture the additional goals that threat agents may have when mounting attacks in the public information environment - political advantage, economic advantage, societal distrust, reputational harm, and psychological harm:

-   A *political advantage* is any lead, edge, or strategic position that would make a candidate, party, group, organization, or nation-state more likely to win elections, achieve policy goals, gain influence, or increase power in the competitive arena of governance or statecraft.
-   An *economic advantage* is any lead, edge, or strategic position that would allow an entity (person, company, nation) to generate more value, wealth, or profit than competitors.
-   *Societal distrust* is a widespread lack of faith in the honesty, reliability, and good intentions of other people, groups, and key institutions (like government, media, or science) within a society, eroding social bonds, hindering cooperation, and undermining collective action for the common good.
-   *Reputational harm* is damage to the positive public image of an individual, group, organization, brand, or government caused by negative information, false accusations, scandals, unethical actions, or mistakes.
-   *Psychological harm* is damage to a person's mental or emotional well-being, ranging from discomfort to severe trauma, which may result from extreme stress, neglect, or abuse.

#### Limits

Limits are defined in the original 2007 paper as the degrees to which threat agents feel bound by legal or ethical constraints. We assess that the four original values are sufficient for characterizing the new threat archetypes: “Code of Conduct”, “Legal”, “Extra-legal, minor”, and “Extra-legal, major”.

#### Resource

Resource is defined in the original 2007 paper as the organizational level at which a threat agent typically works, which determines the human and other assets available for use in an attack. We assess that the original six values are sufficient for characterizing the new threat archetypes: “Individual”, “Club”, “Contest”, “Team”, “Organization”, “Government”.

#### Skill Level

Skill level is defined in the original 2007 paper as the extent of expertise or training an agent possesses. We assess that the original four values are sufficient for characterizing the new threat archetypes: “None”, “Minimal”, “Operational”, “Adept”.

#### Objective

In the original 2007 paper objective is defined as the action that a cyber threat agent takes to bring about the desired outcome. We can think of this as a tactic used to achieve the agent’s primary goal. Of the original six values (“Copy”, “Deny”, “Destroy”, “Damage”, “Take”, “All of the Above/Don’t Care”), “Copy”, “Damage”, “Take”, and “All of the Above/Don’t Care” have some relevance to the new archetypes, as shown in the new matrix of additional threat agents. Other than to support hybrid attacks, however, these “actions on objective” are generally not tactics used by those who mount attacks on the public information environment. To achieve their desired outcome, we assess that such attackers are more likely to employ a combination of the following tactics to manipulate, abuse or exploit their victims - “Justify”, “Dissuade”, “Motivate”, “Undermine”, “Intimidate”, “Exploit”:

*Justify:* to provide a valid explanation or vindication for an action, decision, or belief, often one that may be questioned, by demonstrating that it is right, reasonable, or necessary.

*Dissuade:* to persuade someone not to do something or convince them to abandon a plan or belief.

*Motivate:* to inspire someone to want to do something, especially something requiring hard work or effort.

*Undermine:* to weaken or subvert someone or something’s authority, confidence, or effectiveness over time.

*Intimidate:* to intentionally frighten, threaten, or overawe someone to induce fear, force them to do something, or deter them from an action.

*Exploit:* to take advantage of someone or something for one's own benefit.

#### Visibility

Visibility is defined in the original 2007 paper as the extent to which the agent conceals or reveals their actions and identity when mounting an attack. We assess that the original four values are sufficient for characterizing the new threat archetypes: “Overt”, “Covert”, “Clandestine”, and “Don’t Care”.

#### Motivation

Motivation was added as a defining attribute to the threat agent library in 2015 because it helps to indicate the nature of the expected harmful action, creates a fuller, more relatable story to colleagues, and leads to faster implementation of more effective defenses. It was defined as meaning both the cause or reason a person commits an act, and the drive or level of emotional interest and intensity which the person acts upon. The paper distinguishes between organizational (what motivates the organization) and personal (what motivates the individual) motivations, defining (most prevalent) motivations and co-motivations (those with equal or near-equal cause to the defining motivation), and subordinate (secondary) and binding (what brings an individual into an organization) motivations.

Of the original ten elements of motivation (“Accidental”, “Coercion”, “Disgruntlement”, “Dominance”, “Ideology”, “Notoriety”, “Organizational Gain”, “Personal Financial Gain”, “Personal Satisfaction”, “Unpredictable”), we assess that three are not relevant to the new threat archetypes: “Coercion”, “Disgruntlement”, and “Unpredictable”:

-   “Coercion” applies only to those threat agents who are commonly forced to do something out of fear of incurring a loss, such as Internal Spies or Mobsters, but it is not common for any of the new threat agents to be coerced into doing what they do.
-   “Disgruntlement” applies to those who have held a past relationship with the target and perceive that they have been unfairly wronged in some way and therefore want to get their own back, such as employees or even terrorists, but it is not common for any of the new threat agents to act upon this motive. *Feedback*: Tim Casey suggested that disgruntlement can indeed apply to some of the new threat agents. We agreed but realized there are diminishing returns in further analyzing the taxonomy for motivations.
-   “Unpredictable” applies only to truly random and likely bizarre acts which seem to have no logical purpose to the victims, such as those carried out by irrational or mentally disturbed individuals. The new archetype that comes closest here is the “Conspiracy Theorist”, but it can be argued that the actions of conspiracy theorists are somewhat predictable.

Nevertheless, the remaining seven elements of motivation are deemed insufficient to describe all the causes and drivers of manipulative, abusive, and exploitative actions in the public sphere. We therefore propose adding eight new elements of motivation to help us characterize and define the new threat archetypes - “Belonging”, “Control”, “Superiority”, “Adulation”, “Outrage”, “Revenge”, “Spite”, “Hatred”:

*Belonging:* the emotional state of feeling accepted, valued, and respected by a larger group.

*Control:* the power to influence or direct people's behavior or the course of events.

*Superiority:* the state of being better, higher, greater, or more powerful than others in some way.

*Adulation:* extreme, excessive, or uncritical praise, admiration, or devotion.

*Outrage:* an intense feeling of indignation triggered by a perceived injustice or moral violation.

*Revenge:* a vindictive desire to inflict punishment or harm in retaliation for a perceived wrong.

*Spite:* a petty feeling of envy or resentment expressed through harassment or ill will.

*Hatred:* an extreme dislike, aversion, or ill will toward a person, group, or object.

We propose that these new elements of motivation be added to the Attack Motivation Vocabulary [**`attack-motivation-ov`**](https://docs.oasis-open.org/cti/stix/v2.1/os/stix-v2.1-os.html#_dmb1khqsn650).

*Feedback*: Tim Casey suggested that these newly proposed elements of motivation could all be accommodated by the existing elements, but we believe the nuance here is important and may give rise to different interventions, so we await feedback from those defending the integrity of the public information environment.

### New Threat Agents

We use the extended set of values above to propose an additional 20 threat archetypes, as shown in the matrix below. For space reasons, the original threat archetypes are not shown. The columns in the matrix are organized by the overarching (often assumed) intent of the threat actor. We have kept the original values “hostile” and “non-hostile”, and added “manipulative”, “abusive”, and “exploitative” for threats to the public information environment. In this broader context, “hostile” is synonymous with “intrusive”, meaning intruding into a proprietary information environment.

Note that the original threat agent library listed “insider-accidental” as a valid threat type along with “accidental” as a valid attack motivation. In the same spirit, we have included “misinformer” and “passive-bigot” as non-hostile threat agents pertaining to the public information environment.

Definitions for the new threat archetypes are provided in Table 2 New Threat Archetype Definitions.

<p align="center"><i>Table 1 New Threat Archetypes</i></p>

<p align="center"><img src="media/table-1-new-threat-archetypes.png" alt="Table 1 New Threat Archetypes" style="max-width: 100%;"></p>

<p align="center"><i>Table 2 New Threat Archetype Definitions</i></p>

| Threat Archetype | Description |
| --- | --- |
| **Non-Hostile** | |
| misinformer | A person who unintentionally provides false, inaccurate, or misleading information to others, causing them to be wrongly informed. A misinformer is someone who "informs wrongly," leading people astray from the truth, without an explicit intent to deceive. |
| passive-bigot | A person who holds bigoted beliefs but does not actively or aggressively act on them. Nevertheless, holding unexamined prejudices towards certain groups may influence decisions such as whom they hire or promote. Passive bigots can perpetuate systemic bigotry by being complicit in or quietly accepting an unequal status quo. |
| **Manipulative** | |
| public-propagandist | Someone who openly and deliberately spreads specific ideas, selective facts, biased information, or lies to manipulate public opinion, support a cause, damage an opponent, or further a government's agenda, often by appealing to emotion and using symbols to influence beliefs and actions for a specific goal. Includes overt manipulators, spin doctors, wolf warrior diplomats (China). |
| covert-manipulator | An individual or entity masquerading under a false identity that deliberately twists narratives, engages in selective truth-telling, or strategically alters or presents facts and data to covertly influence public perception, opinions, or decisions for a specific agenda. Includes covert influencers, undercover propagandists, disinformers. Russian intelligence agencies are renowned for engaging in dezinformatsiya (дезинформация or disinformation), aktivnye meropriyatiya (активные мероприятия or active measures), and maskirovka (маскировка or masking, disguise). |
| influence-for-hire-provider | Organization that provides information manipulation services or conducts influence operations for a fee. Sometimes called disinformation-as-a-service providers or digital campaign consultants, they may market their services as "strategic communications" or "digital reputation management". |
| internet-troll | A person, usually anonymous, who intentionally disrupts online communities by posting inflammatory, irrelevant, or malicious messages to provoke reactions, causing chaos or "drama". Trolling takes place where others can see the comments made. Trolls feed on attention and what they do ranges from clever pranks and constant harassment to violent threats. |
| public-agitator | Someone who openly and intentionally stirs up trouble, conflict, or strong reactions such as anger or moral outrage, and challenges norms, often to promote support for or opposition to a political, social, or other cause. Includes instigators, fomenters, demagogues. |
| agent-provocateur | A person hired to infiltrate a group (like a protest or union) to incite illegal actions or violence, making it easier for authorities to arrest members, essentially causing trouble from within for ulterior motives, often by encouraging rule breaking. |
| conspiracy-theorist | Someone who believes that a notable event, phenomenon or situation is the result of a secret plan made by some influential or controlling organization or group when other explanations are more probable. |
| **Abusive** | |
| active-bigot | A person who refuses to accept the members of a specific community to the point of engaging in targeted abuse of that community. Active bigotry can target those with specific identities or protected characteristics. Examples of the former are ethnonationalist extremism, xenophobia. Examples of the latter are misogyny, racism, islamophobia, antisemitism, ableism, ageism; also homophobia, transphobia and any kind of gender-based content harm. |
| hate-group | An organization or collection of individuals that, based on its official statements or principles, the statements of its leaders, or its activities, has beliefs or practices that attack or malign an entire class of people, typically for their immutable characteristics, like race, religion, ethnicity, sexual orientation, or gender identity. |
| slanderer | A person who harms the reputation of someone else or of an organization by making malicious, false, spoken statements (slander) or written statements (libel) about them, essentially a defamer, calumniator, or someone who spreads lies to prejudice others. They attack a person's or organization’s good name with untrue, damaging words, aiming to bring disgrace or discredit. Slanderers can act alone or as part of a group, such as in smear campaigns and “character assassination” efforts. |
| doxxer | A person who finds and publishes someone's private, personally identifiable information (like real name, address, workplace) online without consent, often maliciously, to harass, intimidate, or expose them. Doxxers aggregate public records, social media, and sometimes hack into accounts to gather details, then release them publicly. Motivations range from entertainment and prestige to revenge and retribution, to online feuds and vigilantism, to severe harassment and stalking, to extortion and blackmail, to commercial and political advantage. While typically carried out by individuals, doxxing has evolved to include coordinated group campaigns, “organizational doxxing” (hacking into networks to obtain Personally Identifiable Information on customers and employees), and even commercial "doxxing-as-a-service" operations. It can lead to real-world consequences like job loss, social shaming, or physical threats. |
| authoritarian | Any authority (a group or a person) that uses its power unjustly to enforce strict obedience, often without question, favoring absolute control over individual freedom, like a strict parent, manager, or political leader. Authoritarians believe in or practice systems in which power rests with leaders, not people, expecting people to follow rules rigidly. Includes totalitarians, tyrants, autocrats, persecutors, oppressors, censors. |
| cyber mob | A self-perpetuating group of people who band together online to carry out a campaign of coordinated harassment, ridicule, shaming, or threats against a specific target. Cyber mobs may engage in dogpiling, brigading, online shaming, or cancel culture against their targets. |
| cyberbully | Someone who uses digital technology (phones, internet, social media, games) to intentionally harass, threaten, embarrass, or harm those whom they perceive as vulnerable, often repeatedly, by sending mean messages, spreading rumors, posting hurtful content (photos, videos, lies), or sharing private information. |
| **Exploitative** | |
| fraudster | Someone engaging in targeted fraud or related commercial harms. Includes scammer, extortionist, catfisher. Some common schemes are investment fraud, romance scams, pig butchering, and cryptocurrency scams. Unethical businesses may hire fraudsters to defraud a rival, such as via a business email compromise, to cripple the rival’s reputation or supply chain. |
| cyberstalker | Someone who uses digital technology (internet, phones, apps) obsessively and aggressively to the point of harassment, causing a reasonable person to fear for their safety or to suffer substantial emotional distress. This may involve the use of fake accounts, hacking, doxxing, or spreading false information to control or harm the victim. Cyberstalking sometimes escalates from online actions to real-life danger. |
| groomer | Someone who engages in grooming, which is a manipulative and calculated process of building a relationship, trust, and emotional connection with a vulnerable person (typically a child or minor) in order to manipulate, exploit, and abuse them, usually for sexual purposes. |
| sextortionist | A person who commits sextortion, which is a form of blackmail where a perpetrator threatens to share a victim's private, nude, or sexually explicit images or videos unless the victim complies with their demands, which typically involve money, gift cards, or additional sexual images or favors. |

## 

---

## Notes

<sup id="fn-1">1</sup> [https://www.researchgate.net/publication/324091298_Threat_Agent_Library_Helps_Identify_Information_Security_Risks](https://www.researchgate.net/publication/324091298_Threat_Agent_Library_Helps_Identify_Information_Security_Risks) [↩](#fnref-1)

<sup id="fn-2">2</sup> [https://www.researchgate.net/publication/364960481_Understanding_Cyberthreat_Motivations_to_Improve_Defense](https://www.researchgate.net/publication/364960481_Understanding_Cyberthreat_Motivations_to_Improve_Defense) [↩](#fnref-2)

<sup id="fn-3">3</sup> Consideration was also given to a fourth category “suppressive” to cover threat agents who engage in information suppression such as authoritarians and censors, but for simplicity these agents were folded under the “abusive” category. [↩](#fnref-3)

<sup id="fn-4">4</sup> [https://www.robertmlee.org/cyber-intelligence-part-5-cyber-threat-intelligence](https://www.robertmlee.org/cyber-intelligence-part-5-cyber-threat-intelligence) [↩](#fnref-4)
