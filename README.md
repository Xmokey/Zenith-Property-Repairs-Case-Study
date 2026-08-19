# Zenith Property Repairs

## Managed Property-Services Marketplace & Delivery Platform

**Role:** Product / Technical Delivery  
**Product:** Managed marketplace for property repairs, renovations and development  
**Users:** Property Owners / Investors · Contractors · Zenith Admin  
**Development:** 1 Backend Engineer · 2 Frontend Engineers  
**Status:** End-stage QA / Pre-production

---

## Overview

Zenith Property Repairs is a managed marketplace connecting property owners, investors and other property stakeholders with qualified contractors for repairs, renovations and property development.

It is not designed as a conventional contractor directory or open marketplace. Clients do not simply browse contractors and engage them directly. Zenith provides the operational control and quality-enforcement layer between property owners and contractors, governing the process from initial request through inspection, contractor assignment, quotation, contracting, project delivery and payment.

The operating principles are:

> **Inspect before you quote. Vet before you assign. Tie payments to project milestones.**

The core workflow is:

**Inspection → Estimate → Quote → Contract → Project**

---

## The Problem

Property repair is messy because diagnosis, contractor quality, pricing, scope, delivery, compliance and payment can all introduce risk.

For property owners, there can be uncertainty around:

- whether the contractor is qualified to perform the work
- whether the problem has been properly assessed
- what the work should cost
- what is actually included in the scope
- whether work is progressing as expected
- whether completed work has been properly verified
- when payments should be released

Poorly controlled processes can lead to delays, disputes, scope changes, cost overruns, compliance issues and broader operational fallout.

Contractors face a different set of problems. They need structured assignments, clear scopes, defined workflows, predictable milestone processes and a reliable path from completed work to payment.

Zenith was designed to address both sides.

**Property owners get access to qualified, vetted contractors through a structured service-delivery process.**

**Contractors receive structured work through a governed operating environment.**

Zenith sits between both sides as the **operational control and quality-enforcement layer**.

---

## Product Model

The platform is organized around three primary actors:

### Property Owner / Client

Submits a repair or renovation request, provides property information, accepts terms, pays applicable inspection fees, reviews quotations, approves contracts, evaluates milestones and makes required project payments.

### Contractor

Registers and completes onboarding, satisfies qualification and compliance requirements, accepts assignments, performs inspections, submits estimates, executes approved work and submits milestone evidence.

### Zenith Admin

Provides the operational control layer: reviews and classifies requests, assigns qualified contractors, reviews inspections and estimates, generates quotations, manages contracts, verifies milestones and handles disputes.

The resulting model is:

**Property Owner ↔ Zenith Admin ↔ Contractor**

rather than a direct owner-to-contractor marketplace.

---

## From Business Problem to Product System

The product required the business problem to be translated into an operating model that engineering could implement.

The work involved moving through:

**Problems → Solutions → Actions → Rules → Interconnected Workflows**

The resulting model connected the activities of property owners, contractors and Zenith Admin across the full service lifecycle.

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

The platform establishes controls around contractor qualification, documentation, licensing, insurance, agreements and payout readiness.

This creates a deliberate separation between:

**Contractor eligibility**

and

**Client assignment.**

The objective is not simply to create contractor supply. It is to create **qualified, usable supply** that Zenith can confidently assign to property work.

The operating principle is:

> **Vet before you assign.**

---

## From Inspection to Contract

The primary commercial workflow is:

**Request → Terms → Inspection → Estimate → Zenith Quote → Contract → Project**

The inspection establishes the information needed to understand the property problem and develop the scope.

The contractor provides the technical estimate.

Zenith Admin reviews the estimate, applies the appropriate platform markup, defines milestones and generates the client quotation.

Contractors therefore estimate the work, while Zenith maintains control of the client-facing commercial relationship.

> **Contractors estimate. Zenith quotes.**

Once the quotation is accepted, the platform moves the engagement into contract and project execution.

This creates a controlled path from an initially uncertain property problem to an agreed commercial engagement.

---

## Project Delivery and Payment

Payment is integrated into the project-delivery workflow rather than treated as a standalone transaction.

The project includes an **initial contractor deployment payment** to enable mobilisation to the site.

Subsequent payments are tied to defined project milestones and the verification of completed work.

The workflow includes:

**Milestone → Evidence → Admin Verification → Client Evaluation → Payment**

Contractors submit evidence of milestone completion. Zenith reviews the evidence before the milestone proceeds through the client evaluation and payment process.

Where evidence is insufficient, the milestone can be returned for correction. Where the client disputes the work, the dispute is handled through the defined workflow before payment proceeds.

This creates the principle:

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

Embedding qualification, assignment, inspection, verification and payment controls into the product workflow.

### AI Product Design

Turning unstructured property problems into structured inspection decisions using classification, confidence, safety and escalation rules.

### Workflow & Systems Thinking

Connecting property owners, contractors and Admin through explicit states, handoffs, rules and operational controls.

### Commercial Product Thinking

Separating contractor estimation from platform-controlled quoting and connecting project delivery to milestone-based payments.

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
