.. raw:: latex

   \pagestyle{plain}
   \thispagestyle{plain}

.. _wg-charter:

FG-TIDA WG6: WG6-ATHENA-charter (ATHENA)
=============================================================

Charter Information
-------------------

.. list-table::
   :header-rows: 0
   :widths: 30 70

   * - **Charter version**
     - v0.1

   * - **Date**
     - 2026-11-24

   * - **Status**
     - Draft


1. Group Information
--------------------

..
   MANDATORY

   AUTHOR GUIDANCE:

   Include names and affiliations only in this section.

   Provide the exact repository and issue-tracker link.

   Do not include biographies, honorary titles, or persons who have not
   agreed to serve.

.. list-table::
   :header-rows: 1
   :widths: 38 62

   * - Field
     - Content

   * - Working group name and acronym
     - WG6-ATHENA-charter (ATHENA)

   * - FG-TIDA theme(s) covered
     - [Theme] [Theme] Network-Native Governance and Trust Enforcement for Agentic AI #10
     - [Theme] ATHENA: Telco-Grade Identity and Delegation Architecture for Agentic AI #34

   * - Chair(s) / co-chairs
     - Gianpaolo Scalone, Vodafone

   * - Editor(s) of the main deliverables
     - Gianpaolo Scalone, Vodafone

   * - Mailing list
     - <Mailing list>

   * - Repository and issue tracker
     - https://github.com/fg-tida-wg6/WG6-ATHENA-charter

   * - Charter status and version
     - Draft, V0.1


2. Background and Problem Statement
-----------------------------------

..
   MANDATORY

   AUTHOR GUIDANCE:

   Write two to four short paragraphs, or a concise numbered list.

   State:

   - what the problem is;
   - who has the problem: people, organizations, AI agents, systems, etc.;
   - why existing work does not adequately solve it;
   - any essential terms needed to understand the rest of the charter.

   Define only essential terms here.

   Do not include:

   - a history of the topic;
   - a literature review;
   - a proposed solution;
   - claims about a particular vendor or product;
   - undefined buzzwords.

An AI agent acting on behalf of an individual or organization may delegate part of a task to another agent. A service receiving a request from that second agent needs to answer three questions. Who is the agent acting for? Who gave it permission to perform this action? Is that permission still valid? The individual or organization from whom the authority originates is the principal.

ATHENA starts from telco-grade identity. Operators already provision and manage SIM/eSIM credentials at scale, authenticate subscriptions and rely on each other’s authentication through roaming. Consider an agent anchored to a SIM/eSIM-backed subscription that delegates a task to a cloud-based sub-agent. The operator can attest to the subscription. The service receiving the sub-agent’s request still needs to establish the link back to the principal and verify that each delegation stayed within the authority granted by its parent.

Workload identity, verifiable credentials and authorization mechanisms provide building blocks. The gap becomes clear when permissions change. A principal may allow an agent to compare prices and make purchases, then withdraw only the permission to buy. The subscription is still active, the agent’s credential is still valid and the sub-agent can still compare prices. When the sub-agent submits an order, how does the merchant know that the permission to buy has been withdrawn?

This is where network APIs could play a role. Which identity and subscription status can an operator attest through an API? Where the operator also manages the delegation, can it confirm that a specific permission is still valid? Where another party manages it, what evidence does the service need from that party? The challenge is to make that information available across operators and services, at the time of the request, without disclosing the principal’s identity unnecessarily.



3. Goals
--------

..
   MANDATORY

   AUTHOR GUIDANCE:

   State what the Working Group will produce and why.

   Keep this section to approximately three to six sentences or bullets.

   Make clear whether the WG will:

   - describe: use cases, terminology, gap analysis;
   - specify: formats, interfaces, protocols;
   - recommend: guidelines, principles or best practices.

   The WG should build on relevant existing standards and specifications
   where possible.

   Do not use open-ended language such as "and any other related topics".

   Do not claim authority reserved for ITU-T Study Groups, such as approving
   ITU-T Recommendations.

* The Working Group will describe a telco-grade reference architecture, using SIM/eSIM-backed subscriptions as a starting point, for binding an agent to an accountable individual or organization. It will identify which elements can also be used by other accountable identity providers.

* It will define requirements for verifying a delegation chain from the principal through an agent to its sub-agents, so a service can establish who granted authority and whether each delegation stayed within the limits of its parent.

* It will identify what a service needs to know when an agent identity, credential or delegation is suspended, expires or is revoked, and what evidence is needed to resume operation after compromise.

* It will assess how network APIs could expose current subscription, identity and delegation status to authorized services, including which party can attest that a specific permission is still valid and how little information about the principal needs to be disclosed.

* It will map these requirements against XSTR.ATHENA and relevant identity and authorization specifications, identify gaps, and recommend architectural principles for verification across operators and non-telco services.


4. Scope and Non-Goals
----------------------

In Scope
~~~~~~~~

..
   MANDATORY

   AUTHOR GUIDANCE:

   Identify clearly what work belongs to this Working Group.

* Telco-grade identity anchoring. How an operator can use a SIM/eSIM-backed subscription to bind an agent to an accountable individual or organization, what evidence supports that binding, and how other accountable identity providers can establish an equivalent binding.

* Delegation across trust domains. What a service needs to verify who delegated authority to whom, whether each agent was entitled to delegate, and whether the requested action falls within every upstream grant. This includes a SIM/eSIM-backed agent delegating to a cloud-based sub-agent with no subscription of its own.

* Identity and delegation lifecycle. How provisioning, suspension, expiry, revocation and recovery after compromise affect the evidence a service can rely on. This includes cases where the subscription remains active but a delegation has been withdrawn, and where an agent resumes operation with a replacement credential.

* Network APIs and minimum disclosure. What an authorized service needs to learn at the time of a request, which party can attest it, and how current the evidence must be. ATHENA will examine when an operator can confirm subscription or identity status, when it can also confirm a delegated permission, and when the service needs evidence from another authority.



Out of Scope / Non-Goals
~~~~~~~~~~~~~~~~~~~~~~~~

..
   MANDATORY

   AUTHOR GUIDANCE:

   Explicitly identify what the WG will NOT do.

   This section is important for preventing scope creep.

   Where a neighbouring topic belongs to another FG-TIDA WG, an SG17
   Question, or another organization, identify that relationship.

   Avoid defining the same deliverable under more than one WG.

* The Working Group will not work on Task authorization and enforcement. The proposed APMA group addresses how task privileges are granted, adjusted and revoked. Theme #10 addresses network enforcement. ATHENA’s contribution to both is the evidence of identity, delegation and current status that those decisions depend on.

* The Working Group will not work on Protocol and API specifications. ATHENA will identify information requirements and assess existing interfaces. Defining new network API endpoints, credential formats, SIM/eSIM profiles or authentication protocols is outside its scope.

* The Working Group will not work on Legal and application-specific policy. Legal responsibility for an agent’s actions belongs with Theme #14. Guardian authority and child-specific safeguards belong with Theme #25. Both can provide use cases for testing the architecture

* The Working Group will not work on Remote attestation. ATHENA may use attestation results as evidence for issuing or maintaining an agent identity. Attestation mechanisms and evidence formats belong with Theme #22.

* Task-level authorization and privilege management are outside ATHENA’s scope and are addressed by the proposed APMA Working Group. ATHENA will identify the evidence a service needs to verify who delegated authority, what limits apply and whether the delegation is still valid.



5. Programme of Work and Deliverables
-------------------------------------

..
   MANDATORY

   AUTHOR GUIDANCE:

   Identify concrete documents the WG intends to produce.

   Every deliverable should have:

   - a clear title;
   - a short description;
   - relevant input documents, where applicable.

   Existing contributions or draft documents should be identified as inputs,
   not automatically treated as adopted WG text.

   Avoid open-ended deliverables such as "ongoing analysis".

.. list-table::
   :header-rows: 1
   :widths: 6 29 45 20

   * - #
     - Deliverable
     - Short description
     - Input documents

   * - 1
     - Telco-Grade Identity and Delegation for Agentic AI (Technical Report)
     - The report will outline a reference architecture using SIM/eSIM-backed
       subscriptions as a starting point. One worked example will follow an
       agent delegating a task to a cloud-based sub-agent. It will identify
       what a service needs to verify when the principal withdraws one
       permission while the subscription remains active, which party can
       attest to each fact, and where a network API could provide current
       status with minimal disclosure.
     - ITU-T XSTR.ATHENA and FG-TIDA Theme #34, including the discussion
       of delegation and revocation.


6. Milestones
-------------

..
   MANDATORY

   AUTHOR GUIDANCE:

   Define dated, checkable milestones aligned with the FG-TIDA meeting
   calendar.

   Typical milestones include:

   - first draft available;
   - WG agreement;
   - submission to the FG-TIDA plenary.

   Keep dates realistic.

   Milestones may be updated without rechartering when the scope itself has
   not changed.

   Do not set dates beyond the lifetime of the Focus Group.

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Target date
     - Milestone

   * - January 2027 before FG-TIDA meeting
     - First draft of deliverable 1 available in the repository. The Working Group will make the first draft of the ATHENA Technical
       Report available in the repository for discussion. It will include an initial architecture outline and one worked delegation example.

   * - January 2027  FG-TIDA meeting
     - Deliverable 1 agreed by the Working Group.

   * - <Meeting / YYYY-MM>
     - <Deliverable 1> submitted to the FG-TIDA plenary.


7. Coordination, Dependencies and Liaisons
------------------------------------------

..
   MANDATORY

   AUTHOR GUIDANCE:

   Identify only organizations or groups with a real dependency.

   Include, where relevant:

   - other FG-TIDA Working Groups;
   - ITU-T SG17 Questions;
   - other ITU-T groups;
   - external standards-development organizations;
   - industry or research communities.

   State briefly what the coordination concerns.

   Do not imply that a formal liaison or agreement exists unless one has
   actually been established.

.. list-table::
   :header-rows: 1
   :widths: 35 65

   * - Group / Organization
     - Coordination or dependency

  * - ITU-T SG17 Q1/17
     - The Working Group will use XSTR.ATHENA as an input to the reference
       architecture and identify any additional requirements that arise when
       a SIM/eSIM-backed agent delegates to a sub-agent in another trust domain.

   * - Proposed FG-TIDA Working Group on Authorization and Privilege
       Management for AI Agents (APMA, proposal #64)
     - The Working Group will seek feedback on the worked example in which
       a principal withdraws one permission while the subscription remains
       active. ATHENA will describe the evidence a service can verify.
       The point for review with APMA is how that evidence informs the
       service's authorization decision.


8. Terminology
--------------

..
   OPTIONAL

   AUTHOR GUIDANCE:

   Include this section only where WG-specific terminology is needed.

   Prefer a reference to FG-TIDA terminology work.

   Limit this section to approximately three to five terms.

   Do not create a complete glossary here.

The Working Group will use the common FG-TIDA terminology where applicable. 
Should the Working Group define new terminology, this shall be communicated to the FG-TIDA terminology & use cases WG that maintains the common terminology repository. 

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Term
     - Meaning

   * - <Term>
     - <Definition>

9. Use Cases
--------------

..
   OPTIONAL

   AUTHOR GUIDANCE:

   Include this section only where WG-specific use cases is needed.

   Prefer a reference to FG-TIDA use cases work.

   Limit this section to approximately three use cases.

   Do not create a complete set of use cases here.

The Working Group will define use cases relevant to this problem domain. 
This shall be communicated to the FG-TIDA terminology & use cases WG that maintains the common use cases repository. 

10. Working Methods
------------------

..
   OPTIONAL

   AUTHOR GUIDANCE:

   Include only working practices that differ from the general FG-TIDA
   working methods.

   Examples include:

   - how GitHub issues are used;
   - how draft documents are adopted;
   - special interim calls.

   Do not repeat ITU-T or FG-TIDA general procedural rules.

<Describe any WG-specific working methods, or delete this section if none.>


11. Security and Privacy Considerations
---------------------------------------

..
   OPTIONAL - RECOMMENDED

   AUTHOR GUIDANCE:

   Provide a short paragraph identifying the security and privacy
   concerns that the WG's deliverables must consider.

   Examples may include:

   - impersonation;
   - unauthorized delegation;
   - linkability;
   - surveillance;
   - misuse of identity information;
   - loss of human control;
   - accountability for agent actions.

   Avoid generic disclaimers.

The report will examine how a service can detect an agent acting on a
permission that its parent never granted or that the principal has since
withdrawn, even while the SIM/eSIM-backed subscription remains active.
Where a network API provides status information, the report will consider
who may query it, how fresh the evidence must be, and whether the service
can verify the permission without learning the subscriber's identity or
receiving an identifier that links the subscriber's activity across services.

12. Success Criteria and Conclusion
-----------------------------------

..
   OPTIONAL

   AUTHOR GUIDANCE:

   State how the WG will know its chartered work is complete.

   Examples include:

   - all deliverables submitted to the FG-TIDA plenary;
   - findings transferred to the relevant SG17 Question;
   - no remaining chartered deliverables.

   Do not describe future approval by SG17 as guaranteed.

The Working Group will have completed its chartered work when it submits
the ATHENA Technical Report to the FG-TIDA plenary. The report will include
the reference architecture and one worked example showing what a service
needs to verify when a principal withdraws a delegated permission while
the SIM/eSIM-backed subscription remains active.



13. Revision History
--------------------

..
   MANDATORY

   AUTHOR GUIDANCE:

   Update this table whenever the scope or charter text changes.

   Changes to milestones alone may be managed separately where appropriate.

.. list-table::
   :header-rows: 1
   :widths: 18 22 60

   * - Version
     - Date
     - Change

  * - 0.1
     - 2026-11-19
     - First draft of the proposed ATHENA Working Group charter.
