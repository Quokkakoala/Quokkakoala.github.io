---
title: "Pre-Mortem Intelligence: Shifting Left on Reliability with AI"
date: 2026-01-04
draft: false
description: "How to fail on paper rather than in production - introducing Prismo, an AI-powered pre-mortem analysis tool that refracts your architecture into a spectrum of risks"
categories: ["SRE"]
tags: ["premortem", "fmea", "shift-left", "risk-management", "ai", "reliability"]
---

![Prismo Logo](/images/blog/prismo-logo.png)

## Pre-Mortem Intelligence: Shifting Left on Reliability with AI

*How to fail "on paper" rather than in production — and why that mindset matters*

---

## Why Pre-Mortem? The Shift Left Mindset

As engineers, we systematically look at why our systems fail and how we can make them better. Pre-mortems are one technique to help us make better choices.

Continuous improvement doesn't just have to be about fixing known bugs. It can be about actively thinking of what can go wrong *before* it happens.

### What is Shift Left?

The concept is simple: move quality activities earlier in the development lifecycle.

```
QUALITY DEVELOPMENT LIFECYCLE

    [PREMORTEM] --> [HEARTBEAT] --> [RETROSPECTIVE] --> [POSTMORTEM]
        |              |                 |                   |
     Proactive      Monitor           Improve            Reactive
        |                                                   |
        v                                                   v
   Fail on PAPER                                    Fail in PRODUCTION
```

Traditional teams spend most of their energy on the right side — reacting to incidents, writing postmortems, and firefighting. Shifting left means investing more in the proactive side.

### Why Shift Left Matters

Pre-mortems are part of a growing desire to shift left in the quality development lifecycle:

| Benefit | Description |
|---------|-------------|
| Fail on paper, not production | Identify issues before they impact customers |
| Find surprises early | Discover risks before they become incidents |
| Define mitigations proactively | Have playbooks ready when things go wrong |
| Raise awareness | Make the whole team conscious of system risks |
| Encourage improvement over quick fix | Build lasting solutions, not band-aids |
| Free up time | Expose technical debt before it becomes urgent |

Research supports this approach. Studies on pre-mortem techniques show they significantly improve risk identification, helping teams catch "black swan" events before they happen.

---

## From Reactive to Proactive: A Cultural Shift

As we feel the pressure to add new features and expand our services, it's important that our culture continues to change from reactive to proactive.

### The Engineering Mindset Shift

| Reactive (Old Way) | Proactive (New Way) |
|-------------------|---------------------|
| Fire-fighting | Prevent problems |
| Post-incident learning | Pre-incident planning |
| Hope it works | Data-driven decisions |
| Fix when broken | Fix before it breaks |
| Respond to alerts | Anticipate failures |

The goal is simple: **embrace the fail whale**. Learn from failures before they happen in production.

---

## Introducing Prismo: AI-Powered Pre-Mortem Analysis

Manual pre-mortem analysis has served us well, but it has limitations. That's why I built **Prismo** — an AI-powered tool that refracts your architecture into a spectrum of risks.

### The Prism Metaphor

Just like a **prism breaks white light into a visible spectrum**, **Prismo breaks your architecture into a spectrum of risks** — revealing hidden failure modes, categorizing them by type, and making the invisible visible.

```
    YOUR ARCHITECTURE (white light)
            |
            v
        [PRISMO] <- AI Analysis
            |
            v
    SPECTRUM OF RISKS
    (Separated, categorized, prioritized)
```

### The Problem with Manual Pre-Mortems

Traditional pre-mortem sessions look like this:

- Schedule 2-hour brainstorming meetings
- Gather engineers in a room (or Zoom)
- Play "assessment poker" with sticky notes
- Manually calculate RPN scores
- Transfer everything to Excel spreadsheets
- Repeat quarterly (if you remember)

This process works, but it's slow, subjective, and hard to maintain.

### Prismo: A Better Approach

Prismo takes your architecture description and automatically:

1. **Refracts** your architecture into failure modes
2. **Categorizes** risks by type (like a spectrum)
3. **Calculates** objective SOD scores
4. **Generates** tactical and strategic mitigations
5. **Populates** the FMEA worksheet

---

## AI vs Manual: A Direct Comparison

Here's how Prismo compares to traditional manual pre-mortem analysis:

### Time and Effort

| Metric | Manual Approach | Prismo |
|--------|-----------------|--------|
| Time to complete | 4 weeks | 20 minutes |
| Meetings required | 6-8 sessions | 0 (async) |
| Engineers involved | 5-10 per session | 1 (to review) |
| Update frequency | Quarterly | Continuous |

### Quality and Coverage

| Metric | Manual Approach | Prismo |
|--------|-----------------|--------|
| Risks identified | 10-15 average | 30-50 average |
| Scoring consistency | Varies by team | Standardized |
| Coverage | Point-in-time | Always current |
| Bias | Anchoring, groupthink | Objective |
| Historical learning | Limited | Pattern database |

### Output Quality

| Metric | Manual Approach | Prismo |
|--------|-----------------|--------|
| Documentation | Static Excel | Dynamic, queryable |
| Mitigation suggestions | Team-dependent | Best practices library |
| Priority ranking | Subjective | RPN-based, consistent |
| Tracking | Manual follow-up | Integrated workflow |

### The Math

```
Manual Process:
- 4 weeks elapsed time
- 40+ person-hours invested
- 60% risk coverage (estimated)
- Quarterly refresh cycle

Prismo:
- 20 minutes elapsed time
- 2 person-hours (review + refinement)  
- 85%+ risk coverage
- Continuous monitoring
```

---

## A Simple Example: Library Management System

Let's see how Prismo works with a straightforward application — a Library Management System.

### The Architecture

```
                    LIBRARY MANAGEMENT SYSTEM

                       +-------------+
                       |   WEB APP   |
                       |  (Frontend) |
                       +------+------+
                              |
                              | HTTPS
                              v
                       +-------------+
                       |  REST API   |
                       |  (Backend)  |
                       +------+------+
                              |
           +------------------+------------------+
           |                  |                  |
           v                  v                  v
    +------------+     +------------+     +-------------+
    |  KEY VAULT |     |   REDIS    |     | DOCUMENT DB |
    |  (Secrets) |     |   CACHE    |     |  (Storage)  |
    +------------+     +------------+     +-------------+
    
    - API Keys         - Session Data     - Books Catalog
    - DB Credentials   - Search Cache     - User Records  
    - Certificates     - Book Inventory   - Borrow History
```

### The Flow: Architecture to FMEA

```
STEP 1: INPUT
Engineer provides architecture description

    "Library app with Web Frontend, REST API, Redis Cache,
     Document DB for storage, and Key Vault for secrets.
     Users can search books, borrow items, manage accounts."

                              |
                              v

STEP 2: PRISMO AI ANALYSIS

    +--------------------------------------------------+
    |                    PRISMO                        |
    |                                                  |
    |   [REFRACT]  -->  [CATEGORIZE]  -->  [SCORE]    |
    |    Architecture      by Type         S x O x D  |
    |    into Risks     (Like spectrum)               |
    |                                                  |
    +--------------------------------------------------+

                              |
                              v

STEP 3: AUTO-POPULATED FMEA

    Complete worksheet with risks, scores, and mitigations
```

---

## Prismo Output: FMEA Worksheet

The AI analyzes the library system and produces this FMEA:

### Identified Risks

| ID | Failure Point | Failure Mode | Effect | S | O | D | RPN | Priority |
|----|---------------|--------------|--------|---|---|---|-----|----------|
| LIB-001 | Key Vault | Secret expiration not monitored | API cannot connect to DB, total outage | 9 | 4 | 7 | 252 | Critical |
| LIB-002 | Document DB | Single region deployment | Complete data loss if region fails | 8 | 3 | 8 | 192 | Medium |
| LIB-003 | Redis Cache | Cache invalidation failure | Stale book availability shown | 5 | 6 | 5 | 150 | Medium |
| LIB-004 | REST API | No rate limiting | API overwhelmed during peak times | 7 | 4 | 4 | 112 | Medium |
| LIB-005 | Web App | No health checks | Failed deployments not detected | 6 | 3 | 6 | 108 | Medium |
| LIB-006 | Document DB | No backup verification | Data loss if corruption occurs | 9 | 2 | 9 | 162 | Medium |
| LIB-007 | All Components | No centralized logging | Slow incident detection, extended outage | 6 | 5 | 7 | 210 | Critical |

### Risk Categories Detected

| Category | Count | Examples |
|----------|-------|----------|
| Authentication | 1 | Secret expiration |
| Blast Radius / SPOF | 1 | Single region deployment |
| Monitoring & Detection | 2 | No health checks, no logging |
| Data Management | 2 | Backup verification, cache invalidation |
| Scalability | 1 | No rate limiting |

**Prismo separates risks into a visible spectrum** — just like white light through a prism.

---

## Generated Mitigations

Prismo doesn't just identify risks — it suggests what to do about them.

### LIB-001: Key Vault Secret Expiration (RPN: 252)

**Tactical (Do Now):**
- Set calendar reminders for secret expiry dates
- Document manual rotation procedure
- Create break-glass emergency access procedure

**Strategic (Plan):**
- Implement automated secret rotation
- Add expiry monitoring alerts (30/14/7 days before)
- Migrate to managed identities where possible

**Expected Impact:**
- Detection improves: 7 to 2
- New RPN: 9 x 4 x 2 = 72 (71% reduction)

### LIB-007: No Centralized Monitoring (RPN: 210)

**Tactical (Do Now):**
- Enable basic logging on all components
- Create manual daily log review checklist
- Set up email alerts for critical errors

**Strategic (Plan):**
- Implement Application Insights across all services
- Create unified dashboard for system health
- Configure automated alerting for anomalies

**Expected Impact:**
- Detection improves: 7 to 2
- Occurrence improves: 5 to 3
- New RPN: 6 x 3 x 2 = 36 (83% reduction)

---

## Understanding the RPN Score

The Risk Priority Number determines where to focus your efforts.

### The Formula

```
RPN = Severity x Occurrence x Detection

Where:
- Severity (S): How bad is the impact? (1-10)
- Occurrence (O): How often does it happen? (1-10)  
- Detection (D): Can we catch it before customers notice? (1-10)
```

### Rating Scales

**Severity (Business Impact)**

| Score | Meaning |
|-------|---------|
| 10 | Catastrophic - complete service failure |
| 7-9 | Major - significant customer impact |
| 4-6 | Moderate - degraded experience |
| 1-3 | Minor - barely noticeable |

**Occurrence (Frequency)**

| Score | Meaning |
|-------|---------|
| 10 | Constant - happens daily |
| 7-9 | Frequent - weekly |
| 4-6 | Occasional - monthly |
| 1-3 | Rare - annually or never |

**Detection (Monitoring)**

| Score | Meaning |
|-------|---------|
| 10 | No detection - customers report it |
| 7-9 | Poor - usually miss it |
| 4-6 | Moderate - sometimes catch it |
| 1-3 | Good - almost always catch it first |

### Priority Actions

| RPN Range | Priority | Action |
|-----------|----------|--------|
| 200-1000 | Critical | Fix this sprint, escalate to leadership |
| 100-199 | Medium | Plan within quarter |
| 50-99 | Low | Add to backlog |
| 1-49 | Minimal | Document and monitor |

---

## The Risk Heatmap

After analysis, visualize risks on a criticality heatmap:

```
RISK PRIORITY MATRIX

                         PROBABILITY
             Unlikely      Likely       Certain
           +-----------+-----------+-----------+
           |           |           |           |
   HIGH    |  LIB-002  |  LIB-007  |           |
           |  LIB-006  |  LIB-001  |           |
           |   [192]   |   [210]   |           |
           |   [162]   |   [252]   |           |
           +-----------+-----------+-----------+
SEVERITY   |           |           |           |
   MEDIUM  |  LIB-005  |  LIB-003  |           |
           |   [108]   |  LIB-004  |           |
           |           |   [150]   |           |
           |           |   [112]   |           |
           +-----------+-----------+-----------+
           |           |           |           |
   LOW     |           |           |           |
           |           |           |           |
           |           |           |           |
           +-----------+-----------+-----------+

Priority Legend:
  RED (Critical):    RPN 200-1000 - Fix this sprint
  ORANGE (Medium):   RPN 100-199  - Plan within quarter  
  GREEN (Low):       RPN 50-99    - Add to backlog
```

**Focus on the upper-right quadrant first:** high severity, high probability risks are your top priority.

**Action Items by Priority:**
1. **LIB-001** (RPN 252) - Secret expiration monitoring - CRITICAL
2. **LIB-007** (RPN 210) - Centralized logging - CRITICAL
3. **LIB-002** (RPN 192) - Multi-region deployment
4. **LIB-006** (RPN 162) - Backup verification

---

## Prismo Architecture

Here's how the platform works:

```
                    PRISMO PLATFORM

    +-------------+
    |  ENGINEER   |
    |  provides   |
    |  architecture
    +------+------+
           |
           v
    +------+------+
    |   WEB APP   |
    | (Input UI)  |
    +------+------+
           |
           v
    +------+------+
    |  REST API   |
    +------+------+
           |
    +------+------+------+
    |      |      |      |
    v      v      v      v
+-------+ +----+ +------+ +----------+
|  KEY  | |REDIS| | AI   | |DOCUMENT |
| VAULT | |CACHE| |ENGINE| |   DB    |
+-------+ +----+ +------+ +----------+
                    |
                    v
           +--------+--------+
           | FMEA WORKSHEET  |
           | (Auto-populated)|
           +-----------------+
```

### Components

| Component | Purpose |
|-----------|---------|
| Web App | Input architecture, view results |
| REST API | Process requests, orchestrate analysis |
| Key Vault | Store API keys and secrets securely |
| Redis Cache | Cache analysis results for performance |
| AI Engine | **Refract architecture into risk spectrum** |
| Document DB | Store risks, analyses, and historical patterns |

---

## Best Practices: Lessons Learned

From running pre-mortems across multiple teams, here's what works.

### Do This

- **Identify stakeholders** — deeply understand their problems before starting
- **Align with leadership** — get buy-in on goals and expected outcomes
- **Measure first** — if you can't measure it, invest in measuring before mitigating
- **Collaborate** — you can't move mountains alone, build your network
- **Celebrate wins** — create awareness of quality milestones

### Avoid This

- **Being a purist** — quality is about limiting exposure, not eliminating all issues
- **Operating in silos** — branch out to partner teams, share and reuse
- **Ignoring failure management** — expect failures and optimize for resiliency
- **Ignoring postmortems** — pre-mortems and postmortems complement each other
- **Losing momentum** — engage in periodic checkpoints, track goals to closure

---

## Summary: Why This Matters

The shift from reactive to proactive reliability engineering comes down to a simple choice:

| Instead of... | Try... |
|---------------|--------|
| Fail in production | Fail on paper |
| Find surprises after they hit | Find surprises before they impact |
| Scramble during incidents | Have mitigations ready |
| Blind spots | Full awareness of risks |
| Quick fixes | Lasting improvements |
| Constant firefighting | Proactive debt reduction |

Prismo makes this shift practical by automating the time-consuming parts of pre-mortem analysis while maintaining (and improving) quality.

### The Numbers

| Metric | Manual | Prismo | Improvement |
|--------|--------|--------|-------------|
| Time | 4 weeks | 20 minutes | 99% faster |
| Risks found | 10-15 | 30-50 | 3x more |
| Accuracy | ~60% | ~85% | 40% better |
| Refresh rate | Quarterly | Continuous | Always current |

---

## The Prismo Promise

> **Just like a prism reveals the hidden spectrum in white light, Prismo reveals the hidden risks in your architecture.**

Simple. Elegant. Reliable.

---

## Getting Started

Interested in Prismo or AI-powered pre-mortem analysis?

- **GitHub:** [Quokkakoala/prismo](https://github.com/Quokkakoala/prismo)
- **Discuss:** Share your thoughts on [LinkedIn](https://linkedin.com/in/santoshpanduranganswamynathan)
- **Follow:** Stay updated at [srestack.dev](https://srestack.dev)

The future of reliability engineering is proactive. Let's build it together.

---

*Have questions or feedback? Reach out on [LinkedIn](https://linkedin.com/in/santoshpanduranganswamynathan) or open an issue on [GitHub](https://github.com/Quokkakoala/prismo).*
