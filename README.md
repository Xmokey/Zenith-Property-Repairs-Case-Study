# Zenith Property Repairs

## Managed Property-Services Marketplace & Delivery Platform

**Role:** Product Owner — Technical Delivery  
**Product:** Managed marketplace for property repairs, renovations and development  
**Users:** Property Owners / Investors · Contractors · Zenith Admin  
**Development:** 1 Backend Engineer · 2 Frontend Engineers  
**Status:** End-stage QA / Pre-production

![Zenith Property Repairs](assets/website-hero.png)

---

## Overview

Zenith Property Repairs is a managed marketplace designed to give property owners a **client-supervised, done-for-you repair experience** without exposing them to the risks and operational burden of sourcing and managing contractors.

At the same time, Zenith gives vetted contractors **qualified, inspected and commercially structured work** without the lead-acquisition and marketing burden of finding and selling to clients.

Zenith is not designed as a conventional contractor directory or open marketplace. It operates as the **operational control and quality-enforcement layer** between property owners and contractors, governing the process from initial request through inspection, contractor assignment, quotation, contracting, project delivery and payment.

> **Inspect before you quote. Vet before you assign. Pay in milestones, not upfront.**

![Zenith operating model](assets/zenith-operating-model.png)

The core workflow is:

**Inspection → Estimate → Quote → Contract → Project**

---

## The Problem

Property repair is fragmented across **diagnosis, contractor quality, scope, pricing, delivery, compliance and payment**. Each part can introduce a separate failure, but the consequences compound across the job: poor diagnosis can create scope problems; weak contractor qualification can create quality risk; uncontrolled scope can create pricing disputes; and weak delivery controls can lead to delays, payment disputes and operational fallout.

The underlying problem was not simply finding someone to fix a property. It was the absence of a **structured system for controlling the work from assessment through delivery and payment**.

For contractors, the problem is different. They need structured work, clear assignments, defined scopes, predictable delivery and payment processes, without carrying the full burden of lead acquisition, marketing and selling every job.

Zenith addresses both sides by absorbing the coordination, qualification, assessment, commercial and delivery-control burden between them.

**Property owners get access to qualified, vetted contractors through a structured service-delivery process.**

**Contractors receive qualified, inspected and commercially structured work through a governed operating environment.**

Zenith sits between both sides as the **operational control and quality-enforcement layer**.

---

## Product Model

The platform is organized around three primary actors:

### Property Owner / Client

Submits a repair or renovation request, provides property information, accepts terms, pays applicable inspection fees and project payments, reviews quotations, approves contracts and evaluates project milestones.

### Contractor

Registers and completes onboarding, satisfies qualification and compliance requirements, accepts assignments, performs inspections, submits estimates, executes approved work and submits milestone evidence.

### Zenith Admin

Provides the operational control layer: reviews and classifies requests, assigns qualified contractors, reviews inspections and estimates, negotiates and structures the commercial proposal, generates client quotations, manages contracts, verifies milestones and handles disputes.

The resulting model is:

**Property Owner ↔ Zenith Admin ↔ Contractor**

rather than a direct owner-to-contractor marketplace.

---

## From Business Problem to Product System

The product required the business problem to be translated into an operating model that engineering could implement.

The work involved moving through:

**Problems → Solutions → Actions → Rules → Interconnected Workflows**

The resulting model connected the activities of property owners, contractors and Zenith Admin across the full service lifecycle.

![Zenith service lifecycle](assets/service-lifecycle.png)

This required defining more than individual screens:

- user responsibilities
- workflow stages
- handoffs
- decision rules
- eligibility conditions
- state changes
- exceptions
- pricing authority
- payment conditions
- dispute handling
- compliance controls
- system behaviour

The objective was to make the business process explicit enough to operate consistently and precise enough for engineering to implement.

---

## AI-Assisted Inspection Triage

One of the significant product decisions was to avoid treating every repair request as requiring the same inspection process.

A property owner may describe a problem in ordinary language, but Zenith needs to determine the appropriate level of assessment before work can progress.

The product therefore uses a three-tier inspection model:

### Tier 1 — Express Digital

Desktop/photo-based assessment with the inspection fee waived.

### Tier 2 — Remote Video

Scheduled live video walkthrough with a reduced inspection fee.

### Tier 3 — Full Physical

Physical inspection with a standard fee and applicable geographic distance band.

![AI-assisted inspection triage](assets/inspection-and-ai-traige.png)

The classification logic evaluates factors including:

- safety conditions
- repair category
- category-specific inspection requirements
- confidence
- scope certainty
- solution specificity
- scope-creep signals
- escalation requirements

Safety rules can override normal confidence scoring. Certain structural, gas, damp/mould and flooding conditions require physical inspection, while categories such as plumbing and electrical impose minimum inspection levels.

The classification output is structured for downstream workflow use, including the assigned tier, confidence, category, safety flag, specialist flag, scope certainty, classification reason and escalation state.

This turns an initially ambiguous property request into a controlled operational decision.

---

## Qualified and Vetted Contractor Marketplace

Zenith does not operate as an open marketplace where clients simply choose a contractor.

Contractors enter a governed network and must complete the required onboarding and qualification process before becoming eligible for assignments.

![Contractor onboarding](assets/contractor-onboarding.png)

The platform establishes controls around contractor qualification, documentation, licensing, insurance, agreements and payout readiness.

This creates a deliberate separation between:

**Contractor eligibility**

and

**Client assignment.**

The objective is not simply to create contractor supply. It is to create **qualified, usable supply** that Zenith can confidently assign to property work.

![Contractor assignment](assets/assignment.png)

> **Vet before you assign.**

---

## From Inspection to Contract

The primary commercial workflow is:

**Request → Terms → Inspection → Estimate → Zenith Negotiation → Quote → Contract → Project**

![Service request](assets/service-request.png)

The inspection establishes the information needed to understand the property problem and develop the scope.

The contractor provides the technical estimate.

Zenith Admin reviews the estimate and engages with the contractor on the work and commercial terms before establishing the client-facing quotation.

Contractors therefore estimate the work, while Zenith maintains control of the client-facing commercial relationship.

![Quotation](assets/quote.png)

> **Contractors estimate. Zenith negotiates and quotes.**

Once the quotation is accepted, the platform moves the engagement into contract and project execution.

This creates a controlled path from assessment to an agreed commercial engagement.

---

## Project Delivery and Payment

Payment is integrated into the project-delivery workflow rather than treated as a standalone transaction.

The project includes an **initial contractor deployment payment** to enable mobilisation to the site.

Subsequent payments are tied to defined project milestones and the verification of completed work.

![Controlled delivery and payment](assets/delivery-and-payment.png)

The workflow includes:

**Milestone → Evidence → Admin Verification → Client Evaluation → Payment**

Contractors submit evidence of milestone completion. Zenith reviews the evidence before the milestone proceeds through the client evaluation and payment process.

Where evidence is insufficient, the milestone can be returned for correction. Where the client disputes the work, the dispute is handled through the defined workflow before payment proceeds.

> **Payments follow controlled project progress.**

The model therefore balances the practical requirement to fund contractor mobilisation with the need to avoid releasing the full project value before delivery has been verified.

---

## Scope Changes and Operational Exceptions

Property work does not always follow the original inspection.

Hidden conditions can emerge after work begins, creating the need for additional work, changed pricing or schedule adjustments.

Zenith therefore treats change orders as explicit workflow events rather than informal conversations between clients and contractors.

The broader operating model also accounts for:

- contractor assignment
- work-order acceptance
- mobilisation
- rescheduling
- insufficient milestone evidence
- client disputes
- payment issues
- warranty claims
- scope disputes
- contractor conduct
- compliance issues
- platform issues

The support system provides separate client and contractor pathways while giving Admin responsibility for triage, investigation, escalation, resolution and closure.

---

## Product & Technical Delivery

My work covered the design of the Zenith product workflow from business requirements through implementable product behaviour.

I defined and structured:

- product workflows
- user actions
- business rules
- state changes
- validation requirements
- exception paths
- payment conditions
- integration requirements
- operational controls
- system responsibilities

The product was developed by a focused team of **one backend engineer and two frontend engineers**.

I worked directly with the engineering team to translate the product model into implementation requirements and resolve ambiguity during development.

As dedicated UI/UX design capacity became unavailable, I also translated product workflows and requirements into detailed frontend design specifications and guided frontend implementation to maintain consistency across the product.

This was not simply a matter of specifying screens. The frontend had to represent the underlying workflow states, permissions, decisions and operational responsibilities correctly.

---

## QA and Product Validation

Zenith progressed through end-stage QA with validation covering the major product workflows and decision systems.

The AI classification model was stress-tested against ambiguous and adversarial scenarios, including judgment-based property conditions.

Distance-band logic and inspection pricing were also validated, while inconsistencies and unresolved data issues were identified rather than silently accepted.

Workflow review also exposed areas requiring refinement around:

- work-order acceptance
- reassignment
- mobilisation
- evidence sufficiency
- milestone notices
- client evaluation
- dispute handling

These refinements strengthened the product model before final validation.

The approach was to validate not only whether individual features worked, but whether the **connected system behaved according to the intended business rules**.

---

## What This Project Demonstrates

### Managed Marketplace Design

Designing a marketplace where the platform actively governs the relationship between property owners and contractors rather than simply facilitating discovery.

### Operational & Quality Control

Embedding qualification, assignment, inspection, negotiation, verification and payment controls into the product workflow.

### AI Product Design

Turning unstructured property problems into structured inspection decisions using classification, confidence, safety and escalation rules.

### Workflow & Systems Thinking

Connecting property owners, contractors and Admin through explicit states, handoffs, rules and operational controls.

### Commercial Product Thinking

Separating contractor estimation from platform-controlled negotiation and quoting, while connecting project delivery to milestone-based payments.

### Technical Product Management

Translating complex operational requirements into workflows, validation rules, system behaviour and implementation requirements for a small engineering team.

### Delivery Adaptability

Maintaining product and frontend implementation consistency when dedicated UI/UX capacity was unavailable by providing detailed design and implementation specifications to frontend engineering.

---

## Current Status

**Stage:** End-stage QA / Pre-production  
**Product model:** Managed property-services marketplace  
**Primary actors:** Property Owner / Client · Contractor · Zenith Admin  
**Development:** 1 Backend Engineer · 2 Frontend Engineers  
**Core workflow:** Inspection → Estimate → Quote → Contract → Project  

**Primary product evidence:** AI decisioning, contractor qualification, marketplace governance, operational workflows, commercial controls, project delivery and payment architecture.

---

*Case study documentation focuses on product decisions, workflows and delivery evidence rather than confidential implementation details.*
