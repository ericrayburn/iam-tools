# Screener Test Cases — Synthetic Suite
# Generated: 2026-06-26 | Screener commit: f14a6c8
# Thresholds: DROP < 6 | BORDERLINE 6–13 | STRONG ≥ 14

Paste each posting block into the screener. Expected verdict is listed above each block.
Platform: leave on Auto-detect unless noted.

---

## TEST 01 — WWT (PSO FTE exception) | Expected: STRONG (score ≥ 14)

Why: World Wide Technology triggers isPSO = true. The FTE -4 penalty is skipped.
Rich L3/L2 content + arch signal + remote carries the score well above 14.

---PASTE START---
World Wide Technology — IAM Architect (Full-Time, Remote)

World Wide Technology is building out its Identity and Access Management practice and needs a senior IAM Architect. This is a full-time position, fully remote, US candidates only.

Responsibilities:
- Lead IAM architecture design across enterprise client engagements
- Define identity governance and access governance frameworks
- Design joiner, mover, and leaver lifecycle automation across the enterprise
- Oversee provisioning and deprovisioning workflows using Okta and Microsoft Entra ID
- Advise on privileged access management strategy and MFA rollout
- Ensure compliance alignment for SOC 2 and HIPAA environments
- Build IAM roadmaps and conduct IAM maturity assessments
- Drive Active Directory consolidation and identity lifecycle management improvements
- Define RBAC models and access control frameworks
- Lead Zero Trust initiative planning and identity strategy

Requirements:
- 10+ years IAM architecture experience
- Deep knowledge of identity governance and administration (IGA)
- SAML 2.0, SCIM 2.0, OAuth 2.0, OIDC federation experience
- Experience with SailPoint IdentityNow, Okta, Microsoft Entra ID
- Privileged identity and PAM program experience

Location: Fully remote — US only
Type: Full-time employee
---PASTE END---

---

## TEST 02 — Implementation / Coding Role | Expected: DROP (knockout: implementation role)

Why: IMPL_SIGNALS dominate — "build and implement", "technical implementation", "hands-on implementation".
roleType.type === 'Implementation' → knockout.

---PASTE START---
IAM Platform Engineer — Build and Implement

We are looking for an IAM engineer to build and implement our identity platform from the ground up. This is a hands-on technical implementation role, not advisory.

Responsibilities:
- Execute technical implementation of Okta and SailPoint connectors
- Hands-on implementation of provisioning workflows
- Build and deploy SCIM integrations
- Write and deploy scripts to automate identity lifecycle tasks
- Deliver the build of the access governance system
- Develop and deploy role-based access control configurations

Requirements:
- 5+ years hands-on IAM development and implementation
- Scripting and automation skills required
- Experience building integrations with Okta Workflows

Location: Remote, US
Type: Contract (6 months)
---PASTE END---

---

## TEST 03 — Okta Workflows Developer | Expected: DROP (knockout: red flag)

Why: "okta workflows developer" matches RED_FLAGS exactly. flags.length > 0 → knockout.

---PASTE START---
Okta Workflows Developer — Remote Contract

We need an Okta Workflows developer to build and maintain automated identity flows within our Okta tenant. The Okta Workflows developer will design, build, and test workflow automations using the Okta Workflows drag-and-drop interface and API connectors.

Responsibilities:
- Design and build Okta Workflows automations
- Connect Okta Workflows to HR systems and downstream SaaS apps
- Maintain and debug existing workflow logic
- Document workflow configurations for IT operations

Requirements:
- 3+ years as an Okta Workflows developer or in Okta Workflows development
- Strong knowledge of Okta Workflows event hooks and scheduled flows
- API connector experience within Okta Workflows

Location: Remote
Type: Contract
---PASTE END---

---

## TEST 04 — Groovy / Saviynt EIC | Expected: DROP (knockout: red flag)

Why: "groovy" and "saviynt eic" both match RED_FLAGS. flags.length > 0 → knockout.

---PASTE START---
Saviynt EIC Developer — Identity Automation

We are seeking a Saviynt EIC specialist with groovy scripting expertise to build and maintain identity workflows on the Saviynt Enterprise Identity Cloud platform.

Responsibilities:
- Develop and maintain Saviynt EIC rules, roles, and connectors
- Write groovy scripts to customize Saviynt EIC provisioning logic
- Build Saviynt EIC integrations with HRMS and target applications
- Support Saviynt EIC upgrades and configuration changes
- Maintain groovy scripting library for identity automation

Requirements:
- 4+ years Saviynt EIC platform experience
- Groovy scripting proficiency required
- Saviynt EIC connector and rule development experience

Location: Remote, US
Type: Contract
---PASTE END---

---

## TEST 05 — Agentic AI Scope | Expected: DROP (knockout: AI exclusion)

Why: "agentic ai" and "generative ai" match AI_EXCLUSION. aiHits > 0 → knockout.
This is the standing exclusion regardless of any IAM content present.

---PASTE START---
IAM and Agentic AI Platform Architect

We are building an agentic AI platform with embedded identity controls. We need an architect who can bridge IAM architecture and generative AI deployment.

Responsibilities:
- Design identity and access management controls for our agentic AI platform
- Define authorization frameworks for AI agents operating on user data
- Advise on generative AI security governance
- Lead IAM architecture for our enterprise AI platform
- Evaluate PAM and MFA requirements across AI-driven workflows
- Oversee access governance for AI agent permissions

The scope includes both traditional IAM architecture and agentic AI identity design. Generative AI experience is required alongside IAM expertise.

Location: Remote, US
Type: Fractional engagement, 3 months
---PASTE END---

---

## TEST 06 — L1 Content Over 20% | Expected: DROP (knockout: L1 > 20%)

Why: Kubernetes, docker, machine learning, and react framework push L1 past 20% of total signals.
No other knockout applies — score alone would also be marginal.

---PASTE START---
Identity and Cloud Platform Engineer

We are looking for an engineer to work across identity and cloud infrastructure. The role combines IAM with cloud-native technologies.

Responsibilities:
- Design IAM architecture for our Kubernetes-based platform
- Manage access governance for containerized workloads running on Docker and Kubernetes
- Integrate Okta with our Kubernetes cluster via OIDC
- Build machine learning pipeline access controls
- Manage Kubernetes RBAC for cluster access
- Integrate identity providers across Docker Swarm and Kubernetes namespaces
- Advise on MFA rollout for platform teams
- Support React framework application authentication flows

Requirements:
- Kubernetes and Docker experience required
- IAM experience with Okta or Azure AD
- Machine learning infrastructure access control a plus
- React framework authentication integration experience

Location: Remote
Type: Contract
---PASTE END---

---

## TEST 07 — Staffing Firm, Minimal IAM | Expected: DROP (score < 6)

Why: staffingFirm type detected → W.staffingFirm = -6. Minimal L3/L2 content cannot recover.
Score: ~3 (L3) + 2 (L2) - 6 (staffingFirm) = -1 → DROP.

---PASTE START---
IAM Consultant — Placed with Our Client

Our staffing firm is sourcing for an IAM consultant on behalf of our client, a mid-size financial services company. This is a staffing agency placement. You will be placed with our client for the duration of the engagement.

We are a recruiting firm that specializes in identity and access management talent. Our client has requested a consultant familiar with identity and access management. The staffing firm will handle payroll and benefits under a corp-to-corp or W-2 arrangement.

Requirements:
- Identity and access management background
- Experience with Okta preferred
- Our client prefers candidates who can start quickly

Note: This is a third-party placement role. The staffing agency does not disclose client names at this stage.

Location: Remote
Type: Contract via staffing firm
---PASTE END---

---

## TEST 08 — FTE Non-PSO, Weak Signals | Expected: DROP (score < 6)

Why: FTE detected (no PSO firm) → W.fte = -4. Minimal IAM signals leave score below 6.
Score: ~2 (L2: Okta) - 4 (FTE) = -2 → DROP.

---PASTE START---
IT Security Analyst — Identity and Access

We are hiring a full-time IT Security Analyst with experience in identity and access tools. This is a permanent employee position with full benefits, 401k, and salary package.

Responsibilities:
- Manage Okta user accounts and access requests
- Support onboarding and offboarding checklists
- Respond to access-related helpdesk tickets
- Maintain user account inventories

Requirements:
- 2+ years IT support or security analyst experience
- Okta admin experience preferred
- Strong communication and ticketing skills

Benefits: Health, dental, 401k, PTO
Type: Full-time employee, permanent
Salary: Depends on experience
---PASTE END---

---

## TEST 09 — No IAM Signals | Expected: DROP (score = 0)

Why: No L3, L2, or L1 keywords from the screener arrays match. Score = 0, below DROP threshold.

---PASTE START---
Operations Manager — Supply Chain Logistics

We are seeking an experienced Operations Manager to oversee our supply chain and logistics operations. The role requires strong project management skills and experience coordinating cross-functional teams.

Responsibilities:
- Oversee daily warehouse operations and inventory management
- Coordinate with vendors and shipping partners
- Manage operations budgets and cost reduction initiatives
- Lead a team of 15 operations staff
- Report KPIs to senior leadership weekly

Requirements:
- 7+ years operations or supply chain management experience
- Strong Excel and ERP system skills
- PMP or APICS certification preferred
- Excellent verbal and written communication

Location: On-site, Chicago IL
Type: Full-time employee
---PASTE END---

---

## TEST 10 — Custom Connector Development | Expected: DROP (knockout: red flag)

Why: "custom connector" matches RED_FLAGS. flags.length > 0 → knockout.

---PASTE START---
SailPoint Architect — Custom Connector Development

We need a SailPoint architect to design and build custom connectors for our SailPoint IdentityNow environment. The primary deliverable is a set of custom connector integrations between SailPoint and our internal applications.

Responsibilities:
- Architect SailPoint IdentityNow provisioning workflows
- Design and develop custom connectors for non-standard target systems
- Build custom connector integrations using the SailPoint connector SDK
- Document custom connector architecture and maintenance procedures
- Advise on access governance and certification campaign design

Requirements:
- SailPoint IdentityNow architecture experience required
- Custom connector development experience required
- Java or Beanshell scripting for connector customization

Location: Remote, US
Type: Contract
---PASTE END---

---

## TEST 11 — Software Engineer Role | Expected: DROP (knockout: red flag)

Why: "software engineer" matches RED_FLAGS label "Engineering role — not architecture".
flags.length > 0 → knockout.

---PASTE START---
Senior Software Engineer — Identity Platform

We are hiring a senior software engineer to join our identity platform team. As a software engineer on the identity team, you will build and maintain the core systems that power our authentication and authorization platform.

Responsibilities:
- Design and develop backend services for our identity platform
- Build REST APIs for authentication and provisioning workflows
- Implement SAML and OIDC integrations with external identity providers
- Write unit and integration tests for identity platform components
- Collaborate with DevOps to deploy identity services on AWS

Requirements:
- 6+ years software engineering experience
- Strong Java or Python development skills
- Experience with SAML, OIDC, or OAuth protocols
- Familiarity with IAM concepts (provisioning, access governance)

Location: Remote, US
Type: Full-time employee
---PASTE END---

---

## Summary Table

| # | Label | Expected | Primary Mechanism |
|---|-------|----------|-------------------|
| 01 | WWT — PSO FTE | STRONG (≥14) | PSO exception skips FTE -4 penalty |
| 02 | Implementation role | DROP | Knockout: Implementation type |
| 03 | Okta Workflows developer | DROP | Knockout: red flag |
| 04 | Groovy / Saviynt EIC | DROP | Knockout: red flag |
| 05 | Agentic AI scope | DROP | Knockout: AI exclusion |
| 06 | L1 content over 20% | DROP | Knockout: L1 pct > 20% |
| 07 | Staffing firm, low content | DROP | Score < 6 (staffingFirm -6) |
| 08 | FTE non-PSO, weak signals | DROP | Score < 6 (FTE -4, no recovery) |
| 09 | No IAM signals | DROP | Score = 0 |
| 10 | Custom connector dev | DROP | Knockout: red flag |
| 11 | Software engineer | DROP | Knockout: red flag |
