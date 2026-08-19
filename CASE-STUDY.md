# Zenith Property Repairs

## Turning an ambiguous property-repair brief into a controlled service-delivery system

**Role:** Product Owner — Technical Delivery  
**Team:** 1 Backend Engineer · 2 Frontend Engineers  
**Product:** Managed marketplace for property repairs, renovations and development  
**Status:** End-stage QA / Pre-production

---

## The challenge

Property repair is not a single transaction. It is a chain of decisions and risks.

A property owner may know that something is wrong without knowing what the problem is, what the work should cost, who is qualified to do it, what is included in the scope, whether progress has actually been completed, or when payment should be released.

The risks extend beyond diagnosis and pricing into contractor quality, delivery, compliance, delays, disputes and the business fallout that follows when the process is poorly controlled.

Contractors face a different problem: finding qualified work, understanding the scope, mobilising to site and getting paid through a structured process without carrying the entire burden of client acquisition and sales.

The product challenge was therefore broader than building a contractor marketplace.

**The system needed to control the relationship between the property owner and contractor.**

---

## My role

I owned the product workflow from business problem through implementable product behaviour.

My work included:

- decomposing the initial business problem
- researching and structuring the service model
- defining the actors and their responsibilities
- designing the connected workflows
- defining business rules and decision points
- specifying state changes and exceptions
- designing contractor qualification and assignment logic
- defining inspection and triage behaviour
- structuring the quotation and payment model
- translating the product into implementation requirements
- working directly with engineering through build
- validating the connected system through QA

The product was developed by **one backend engineer and two frontend engineers**.

The product model became the bridge between a broad business brief and what engineering could actually implement.

---

## Framing the product

The key product insight was that Zenith should not behave like an open directory where a property owner finds a contractor and manages the relationship independently.

Instead, Zenith would sit between both sides as the **operational control and quality-enforcement layer**.

**Property Owner ↔ Zenith ↔ Qualified Contractor**

That led to three principles:

> **Inspect before you quote.**  
> **Vet before you assign.**  
> **Pay in milestones, not upfront.**

The third principle has an important operational qualification: contractors receive an initial deployment payment to mobilise to site, while subsequent project payments are tied to milestones and verification.

![Zenith operating model](assets/zenith-operating-model.png)

---

## Designing the operating model

I translated the verbal business problem into an interconnected operating model rather than treating each feature as a separate screen.

The model connected three primary actors:

**Property Owner → Zenith Admin → Contractor**

The owner initiates the service request and participates in approvals, evaluation and payments.

The contractor provides technical work, estimates and delivery evidence.

Zenith controls qualification, inspection, assignment, commercial negotiation, verification, disputes and payment progression.

The product therefore became a controlled lifecycle:

**Request → Inspect/Triage → Assign → Estimate → Quote → Contract → Execute → Verify → Pay**

![Zenith service lifecycle](assets/service-lifecycle.png)

The important product work was defining what happens **between** those visible stages: who can act, what information is required, what conditions must be satisfied, what state changes, and what happens when something goes wrong.

---

## Decision 1: turn an uncertain repair request into an inspection decision

The initial request can be incomplete or ambiguous. A property owner may describe symptoms rather than a confirmed technical problem.

I designed an inspection decision model rather than assuming every request required the same process.

The system uses three inspection tiers:

- **Express Digital** — desktop/photo assessment
- **Remote Video** — scheduled live walkthrough
- **Full Physical** — physical inspection with applicable geographic pricing

![AI-assisted inspection triage](assets/inspection-and-ai-traige.png)

The decision model considers repair category, safety conditions, confidence, scope certainty, solution specificity and escalation requirements.

Safety rules can override ordinary confidence scoring. Certain property conditions require physical inspection, while other categories impose minimum inspection levels.

The result is a structured downstream decision rather than an unbounded request:

**Tier · Confidence · Category · Safety · Specialist requirement · Scope certainty · Reason · Escalation**

The product turns an ambiguous property problem into an operationally usable inspection path.

---

## Decision 2: qualification before assignment

A marketplace only becomes useful when its supply can be trusted.

I designed contractor onboarding as an eligibility process rather than treating registration as permission to receive work.

The workflow establishes qualification and compliance information including documentation, licensing, insurance, agreements and payout readiness.

![Contractor onboarding](assets/contractor-onboarding.png)

This creates two distinct decisions:

**Is this contractor eligible?**  
**Is this contractor appropriate for this job?**

Only after the first decision can the assignment process operate safely.

![Contractor assignment](assets/assignment.png)

The product therefore uses Zenith as the control point between contractor supply and client work rather than allowing direct, uncontrolled matching.

---

## Decision 3: separate technical estimation from commercial control

The contractor is closest to the technical work, so the contractor provides the estimate.

But the contractor is not given uncontrolled authority over the client-facing commercial relationship.

The workflow became:

**Inspection → Contractor Estimate → Zenith Review/Negotiation → Client Quote**

![Service request](assets/service-request.png)

![Quotation](assets/quote.png)

This distinction makes the roles explicit:

> **Contractors estimate. Zenith negotiates and quotes.**

Once the client accepts the quotation, the engagement moves into contract and project execution.

This was an important product boundary because it connected technical expertise with platform-level commercial control.

---

## Decision 4: connect delivery evidence to payment

Payment could not be treated as a separate checkout event if Zenith was expected to enforce delivery quality.

The project therefore uses a milestone model.

Contractor mobilisation requires an initial deployment payment. After that, project payments follow defined milestones rather than releasing the full project value upfront.

The control loop is:

**Milestone → Evidence → Admin Verification → Client Evaluation → Payment**

![Controlled delivery and payment](assets/delivery-and-payment.png)

If evidence is insufficient, the milestone can be returned for correction. If the client disputes the work, the dispute enters the defined workflow before payment proceeds.

The product connects **delivery state, evidence, quality control and financial release** rather than treating them as independent modules.

---

## Decision 5: make exceptions part of the product

Property work is inherently uncertain. Hidden conditions can appear after work begins and change the scope, price or schedule.

I therefore treated exceptions as product behaviour rather than assuming the happy path would be enough.

The workflow accounts for conditions including:

- reassignment
- mobilisation
- rescheduling
- insufficient evidence
- scope changes
- client disputes
- payment issues
- warranty claims
- contractor conduct
- compliance issues

Change orders are treated as explicit workflow events rather than informal conversations outside the system.

This is important because a workflow that only works when everything goes according to plan is not an operational system.

---

## Working with engineering

The engineering team consisted of **one backend engineer and two frontend engineers**.

My role was not a one-time requirements handoff. I worked with engineering while the product was being built to resolve ambiguity, review implementation implications and refine behaviour.

When dedicated UI/UX design capacity became unavailable, I translated the product workflows and requirements into detailed frontend design specifications and guided implementation.

That work was not about becoming the UI designer. It was about ensuring that the interface correctly represented the underlying product model: workflow state, permissions, decisions, responsibilities and operational conditions.

The working sequence was:

**Problem → Workflow → Rules → Engineering Input → Specification → Build → QA → Refinement**

---

## Validation

QA focused on the connected product rather than only checking whether individual screens functioned.

The validation work covered the major workflow and decision systems, including AI classification, inspection pricing, distance-band logic, contractor workflow, milestone evidence and payment behaviour.

The AI classification model was stress-tested with ambiguous and adversarial property scenarios. Workflow review also surfaced areas requiring refinement around work-order acceptance, reassignment, mobilisation, evidence sufficiency, milestone notices, client evaluation and dispute handling.

The principle was straightforward:

> **Validate whether the implemented system behaves according to the intended business rules.**

This meant treating inconsistencies and unresolved data issues as product problems to surface and resolve, rather than hiding them behind a passing screen-level test.

---

## What I built as a product owner

The most important output was not any individual screen.

It was the **system of decisions and controls connecting the screens**.

I translated an ambiguous service problem into:

- an actor model
- an inspection decision system
- contractor qualification rules
- assignment logic
- commercial boundaries
- project states
- milestone controls
- evidence requirements
- payment conditions
- exception paths
- operational responsibilities
- implementation requirements

That is the core product contribution I would carry from Zenith.

---

## Result

Zenith was designed as more than a contractor marketplace.

It became a managed property-services operating model in which Zenith controls the critical handoffs between **problem identification, qualified supply, commercial agreement, project execution, verification and payment**.

The product gives property owners a structured route to qualified contractors while giving contractors structured work and a governed delivery/payment process.

The measurable commercial outcomes of the product are not claimed here because the project was still at **end-stage QA / pre-production**.

The product outcome that can be demonstrated is the conversion of a broad, ambiguous property-repair brief into a connected, implementable system of workflows, rules and controls.

---

## What this demonstrates

**Product ownership** — taking an ambiguous business problem through product definition, engineering and validation.

**Systems thinking** — designing the relationships between actors, states, rules, handoffs and exceptions.

**Technical product management** — translating business behaviour into implementable requirements while working directly with a small engineering team.

**Operational product design** — embedding qualification, inspection, assignment, verification and payment controls into the service itself.

**Commercial thinking** — separating contractor estimation from Zenith's client-facing negotiation and quotation authority.

**Product quality** — validating the connected system against intended business rules rather than treating feature completion as the finish line.

---

## Repository

The accompanying README contains the broader product documentation, diagrams and selected interface evidence.

[View the Zenith Property Repairs repository](https://github.com/Xmokey/Zenith-Property-Repairs-Case-Study)
