# MVCR-v0.7
## Minimum Viable Consent Receipt - Core Consent Receipt Profile Specification

The 0.7 version of the MVCR specification focuses on the requirements for the MVCR specification. Future versions of this specification will add additional sections to facilitate the technical implementation of an MVCR. As a result, this version of the specification has been reduced by removing material from previous edits, which will be added in according the stage and agreed roadmap of the MVCR in the CISWG.

# Executive Summary

The Consent & Information Sharing Working Group (CISWG) is distilling a common set of consent requirements for information sharing that are salient across jurisdictions and compliant with Fair Information Practice privacy instruments and standards.(see references)  These common requirements constitute the minimum viable consent receipt, specifying the minimum required policy links, consent fields and data formats to meet the minimum legal, transparency and trust obligations for information sharing.

The core Consent Receipt (CR) specification refers to the legal notices required for compliant consent to be valid when collecting personal information. This is currently managed by organizations separately with bespoke policies that are closed to systematic use by an individual. The Consent Receipt addresses this problem.

# Problem Statement
There is no common consent record format.

Information sharing is a complex issue for organizations that require consent for the collection of personal information.  Legal obligations require privacy policies that reflect how personal information may be collected, used, disclosed, retained and disposed of or deleted.

Each organization has their own best practices, policy structures and policy formats. This results in a closed (or 'siloed') type of transparency, that violates the  Openness (transparency and notice) privacy principles, is very costly to manage for all stakeholders and very difficult to regulate effectively. This is compounded by each organization posting their policies in different locations, while frequently changing not only the content but also the URI of the policies.

The result is the current static and binary notice and consent infrastructure that is regulated, yet neither usable nor suitable for its intended purposes. An individual is asked to perform beyond what is reasonable in the current context.  Each individual is expected to understand what information is being collected about them, how it will be used and for what purposes, with which types of entities their information will be shared and to understand and manage the consequences long past the first point of consent. All of this is without a record or the ability to manage consent independently out of context. Meanwhile, in context, people are expected to read all policies, keep track of all active consents, so as to be informed when making new consent agreements.

# The Solution
Increase the capacity for people to manage and understand consent.

Information sharing is dramatically increasing, as a result, the capacity for people to manage information sharing also needs to increase. A specification for a  core viable consent (or authorisation) will address specific jurisdictional requirements and provide a useful framework for developing compliance with ISO 29100 and other trust standards and frameworks.

Individuals' capacity to manage privacy is increased if they are able to aggregate and manage consent after it is provisioned.  Digital consent records, which in this specification is called a consent receipt, enable people to manage information sharing relationships. Organizations can use these receipts to reduce friction and streamline the consent experience.

The core receipt specification addresses general, or regulatory, consent requirements. Consent receipts additionally become more useful as a channel for trust services, trust networks, identity federations, trust marks, privacy icons, standards, assurances, certifications and self asserted community and industry reputations.

# Scope
The Minimum Viable Consent Receipt (MVCR) specification will provide the generic consent record profile for  consent requirements and is intended to be used as a legal and open notice with Kantara CISWG use cases.

This v0.7 of the MVCR further defines the requirements for a Minimum Viable Consent Receipt (MVCR). In this version, the scope is limited to covering when a user takes an explicit action to consent to sharing information, noting that personal data will be collected in a consent transaction. This consent can occur before, during or immediately after their personal information is collected.

The receipt format is required to be human and machine readable.

# Stakeholders

There are three general stakeholder audiences for the MVCR which are referenced through this specification:

1. People:
People receive the consent receipt and may use this to independently track consent and manage terms of sharing personal information.

2. Organizations:
Organizations provide consent receipts when they obtain or assume consent to collect personal information.

3. Regulators - (privacy and data protection enforcement)
Regulators include but aren't limited to the FTC in the USA, the Canadian Federal and Provincial Privacy Commissioners, the EU Data Protection Regulators. Regulators provide public processes for administration and enforcement of regulation in regards to notice and consent requirements

In summary, this MVCR receipt specification addresses the requirements of these three stakeholder groups with the aim to provide a self-regulatory market trust tool that organizations will implement, people can use, and regulators can enforce.

## Intellectual Property Rights
This document is being developed by Kantara Initiative's Consent and Information Sharing Working Group; see <https://kantarainitiative.org/groups/ciswg/>. Participation is free and open, and all work contributed to the effort falls into the Reciprocal Royalty Free with Opt-Out to Reasonable And Non discriminatory (RAND) IPR policy <https://kantarainitiative.org/confluence/x/mQByAg>.

Kantara Initiative is a non-profit membership organization that connects businesses, consumers, governments, and citizens through innovations and programs that support more natively trust worthy on-line experiences. The mission of KI is to foster identity community harmonization, interoperability, innovation, and broad adoption through the development criteria for operational trust frameworks and deployment/usage best practices for privacy-respecting, secure access to trusted online services.

## Generic Requirements
"MUST" indicates a required component, the word “SHOULD” indicates a recommendation and does not impose an obligation. The word "CAN" means that this is a common option.

1. The receipt MUST have a property to authenticate the origin.
2. The receipt MUST have an integrity protection property.
3. The audience SHOULD be restricted and transparent.
4. The receipt SHOULD be able to be transmitted over various transport protocols.
5. The payload MUST have a human readable section, and SHOULD have a machine readable section.
6. The payload MUST include the following properties:
  a) Issuer
  b) Date
  c) Time
  d) direct contact information to data controller
  e) Contain a static Link to privacy policy
  f) Purpose (s)
  g) YES or NO Flags
    * 3rd party data sharing
    * Sensitive Personal Data Collection
    * Operational Context
7. The payload SHOULD include the following properties:
  a) A description of the types of personally identifiable information to which the consent applies.
8. The payload SHOULD include the following information:
  a) the personal identifier used in the consent receipt
  b) some or all of the personally identifiable information to which the consent applies
8. The receipt MUST be systematically usable and automatically discoverable
9. Receipts MUST contain the minimum information to enable request for more information, if required
10. Receipts MUST contain the minimum information to enable requests for more information, if required

### Consent Notice Fields and Descriptions (TBF v.07)

| #  | Fields                                                               | Description                                                                                                                                                                                                                                                                                            | Logic                                                                                                                                                                                                                                                                | JWT Claim                                                                                        | MVCR                       |
|----|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|----------------------------|
| 1  | Receipt Identifier                                                   |                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                      | jti / string                                                                                     | Y                          |
| 2  | Jurisdiction of organisation                                         | this is the location of processing                                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                      | jurisdiction / string (country code?)                                                            | Y                          |
| 3  | Issuer                                                               | URL of the party that generated and signed this consent receipt                                                                                                                                                                                                                                        | self created, third party and service provided created                                                                                                                                                                                                               | iss / string [URL]                                                                               | Y                          |
| 4  | Identification: of natural person using any pseudonymous identifiers | Subject provided identifier, usually email addressClaim, defined/namespaced by the issuer -                                                                                                                                                                                                            | This is the identity provided by the data subject to identify the consent to a persona and create a profile.                                                                                                                                                         | sub / String                                                                                     | Y                          |
| 5  | Service Title                                                        | this is global context for consent: e.g. amazon, amazon express                                                                                                                                                                                                                                        | Identify the scope of the use of consent, scope of purpose and to a service context.                                                                                                                                                                                 | “svc”: String (array[String]?)                                                                   | Y                          |
| 6  | Short Notice Field                                                   | Link to the short notice enables usability and layered policy. to provide enhanced transparency about data collection and information sharing practices                                                                                                                                                | This is a short summary that supports the service title and makes transparent the use.                                                                                                                                                                               | “notice” / String                                                                                | Y                          |
| 7  | Date Time Stamp                                                      | date and time at the point consent is provided                                                                                                                                                                                                                                                         | moment explicit consent is provided the consent transaction is date and time stamped                                                                                                                                                                                 | iat / timestamp                                                                                  | Y                          |
| 8  | Privacy Policy Link                                                  | the internet and immediately accessible privacy policy of the service referred to by the receipt (mydomain.com/privacy)                                                                                                                                                                                | - if link is not valid receipt is not valid- domain provides an admin registration contact that provides company jurisdiction- IP Address provides GEOlocation-                                                                                                      | “policy_uri” / URI (String)                                                                      | Y                          |
| 9  | Identity of Data Controller                                          | The identity and company of the data controller and any partynominated to be data controller on behalf of org                                                                                                                                                                                          |                                                                                                                                                                                                                                                                      | “data_controller” / object                                                                       | Y                          |
| 10 | Contact information of Data Controller                               | Address of Data Controller + at least one other method of contact                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                      | ^-- subsumed in the above                                                                        | Y                          |
| 11 | Consent Transaction Data: collected from the consent session-        | Examples include: Device Identifier, UID, IP Address, Browser Fingerprint, DNT signal client header, .Mobile device id                                                                                                                                                                                 | (not sure how this will be attached to the receipt)                                                                                                                                                                                                                  | consent_payload / object                                                                         | N                          |
| 12 | Purpose (s) Specification - short purpose description,               | this is a short description of the purposelist of normative values in a global registry (services need to map specific actions to things in the registry -- should we require services to document these mappings?)                                                                                    | -                                                                                                                                                                                                                                                                    | purpose / array [string]-> scope?                                                                | Y                          |
| 13 | Categories of PII Collected                                          | Categories Being; name, address, email, finacial,                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                      |                                                                                                  | Y                          |
| 14 | PII Collected                                                        | Personal information collected in relation to, or adjacent of purposes specified                                                                                                                                                                                                                       | (not sure in what format or how this will be attached to the receipt)                                                                                                                                                                                                | pii_collected / object                                                                           | N                          |
| 15 | Sensitive Information                                                | What is determined to be personal information can be from a big list of all defined personal information categories from all jurisdictions. ( this indicates that it is possible depending on where parties are that this is sensitive)                                                                | if no, then no information is needed, if yes, then more information or assurances are required to show compliance with legal obligations, these can be provided in a number of ways, i.e. third trust marks, protocols, standards, assurances and so on.             | “sensitive” / array[strings] -> strings are pointers (URIs?) to details of sensitive information | Y (needs just a yes or no) |
| 16 | 3rd party sharing of personal information                            | This refers to the sharing of personal information collected about the individual, with another external party by the service provider, bound under the privacy policy and terms.                                                                                                                      | a chain of obligations, in law this is the categories of data shared, (room for more)                                                                                                                                                                                | “sharing” / array[string]-> strings are pointers?                                                | Y (needs just a yes or no) |
| 17 | OC of data collection                                                | Operational Context refers to the conditions that ensure the consent is fair, reasonable and proportional. , e.g. if it is on a website, then there are requirements like; are mandatory fields indicated, is there a separate consent for privacy policy and terms of service?set of registry values? | This is a self asserted Yes or No that is not mandatory but would be required to demonstrate compliance with legal obligations that are found in various contexts. This provides the contextual framework for context elements in a number of different environments | “context” / array[string]-> Strings are pointers?                                                | Y (needs just a yes or no) |
| 18 | Resource Server Identifier                                           | URI that identifies the target service of this consent                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                      | “aud” / URI                                                                                      | N                          |
| 19 | Scopes                                                               | What you’re allowed to do on the service (these can be tied to legal / business / technical layers)                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                      | “scope” / space separated list of strings                                                        | N                          |

## Json Model (TBF v0.7)
- define the data model 
- core object of what represents a consent receipts 
- translate that into json  mode 
- map action upon the object into an api
restful where possible. 


 
- and to create a generator of receipt based on this model using the policy and information put into a form.   
We then
- play with this a little - see if it is going to be harder than I think it is to show a common set of requirements for a minimal viable versions. 
- present this in an demonstrable form so everyone interested in driving this forward can collaborate
- Collect all the comments and discussion points then update the model to produce a v.1. 
- Add UMA fields to the CR Core as soon as the core format is stable (or earlier) 

# References and Further Reading
The MVCR is written with terms and reference in context of:
* ISO/IEC 29100	Information technology – Security techniques – Privacy framework
* ISO/IEC 29115	Information technology – Security techniques – Entity Authentication Assurance

Supporting reference to ISTPA: Analysis of privacy principles:
* ISTPA, (2007) Analysis of Privacy Principals, pg. 64, [Online] http://www.istpa.org/ [Accessed Nov, 4 2010]
* Minister of Economy Office, Japan (2014) Guideline for the online notice and consent from consumers, http://www.meti.go.jp/press/2014/10/20141017002/20141017002a.pdf.  [Includes examples of a consent receipt in guidelines proposed in the context of ISO 29100]

Note: as an international framework the MVCR aims to include all the requirements for Sensitive Personal Information, this because, people change jurisdictions, and people provide fake jurisdiction. In this regard the consent receord framework aims to harmonise these requirements so they are consistent across jurisidictions.  This is a guiding principle for the appendix and in particular Sensitive Personal Information classificaitons. (note this will need to be more specific for v0.8)

# Appendix A: Data Controller Contact Types (TDF v0.8)

Address, phone number and email, twitter, live online support,
- This should include proportional contact capabilitlites that are proportionate to the contexts

# Appendix B: Track Identifiers and Attributes for People

UID, IP Address, Email Address, Browser Finger Print,

# Appendix C: Purpose Specification (TBD V0.8)

Purpose specification apprach is to create a list here that will act as a cataouge of purpose short notices. In the processes described we will require an option for use cases and data controllers  to be able to add additional purposes.

The purpose here may need to add Operational Context for type of deveices (See NTIA Best Practices for Short Notices for Mobile etc. )

# Appendix D: 3rd Party Sharing

# Appendix E: Sensitive Personal Information

# Appendix  F:  Operational Contexts

As a part of creating a receipt for a Person, Data Subject (DS) there are often legal requirements based on the operational content(OC).

 The Operational Contexts obligations are listed when the Use Case for implementation is created, these are found in legal requirements, best practices, and are a bucket for context specific identifiers which enable operation policy.

This functions as a flag: YES or NO in the MVCR

Each use case or implementation requires an OC check list.

i.e. If YES, the Yes is defined by a self-assertion that the receipt and company side consent management practices follow the legal requirements for fair and reasonable consent harvesting.

Operational Context - Defined by either jurisdictionally specific requirements and or use case specific requirements.

## Examples of Operation Contexts

#Informing PI principals about the consequences, if any, of withholding their consent in whole or in part; and
informing on the ways to withdraw consent

# whether replies to the questions are obligatory or voluntary, as well as the possible consequences of failure to reply,
# the existence of the right of access to and the right to rectify the data  concerning him

## Audit Notes
NOTE: Burying the privacy related notice obscurely in the other matters and having user accept it is a common privacy attack.

Consent is action based is it an independent permission (i.e. only one policy  with same scopes of purpose)

 ## Meaningful Policy Changes Requiring a New Consent Receipt
 - Change in overview of the service
 - change the PII Controller
 - change PII items being collected
 - change the purpose of use to something outside the scope
 - change 3rd party- unless DS consented to scope of 3rd parties and this is within scope
 - consent required if extend retention period or extend disposal date
 - change matters related to disclosure, suspension of use, correction, deletion, suspension of provision or revoking of consent
 - change the contact information for inquiry
