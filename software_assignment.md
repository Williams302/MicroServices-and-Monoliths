# Software Assignment — Microservices Architecture

---

## Introduction

Programs are no longer based on monolithic systems where every part has its own data. The microservices architectural style structures an application as a collection of small, independently deployable services, each running its own process and communicating through lightweight mechanisms.

By avoiding shared databases, microservices can scale different services independently and rapidly. If any smaller software program is not working or slows down system requests, engineers can quickly isolate that component to ensure uninterrupted service. Each microservice runs independently and communicates via APIs, ensuring high availability and scalability.

---

## Section 1 — Company Using Microservices Architecture

### Example 1 — Amazon

Amazon is one of the earliest adopters. Netflix was an early pioneer in what has become increasingly common — transitioning from a monolith to a microservices architecture. Amazon itself broke its entire e-commerce platform into hundreds of microservices: product catalog, cart, checkout, payments, recommendations, and logistics are all separate independent services.

### Example 2 — Atlassian (Business Suite — Jira & Confluence)

Atlassian decided to re-architect Jira and Confluence and move them from a monolithic system to cloud applications hosted by AWS. The project, named **Vertigo**, was their largest infrastructure project to date — taking two years to complete the transition, migrating more than 100,000 customers in just over 10 months with no service interruptions.

---

## Section 2 — The Microservices Data Went to Monolith — and Why

### Case 1 — Amazon Prime Video (2023)

Prime Video had a tool that monitored the quality of every video stream watched by customers — checking for audio/video defects in real time. This tool was built on microservice infrastructure, but as the number of streams on the platform increased, it faced scaling bottlenecks and turned out to be very expensive.

**What they did:** They decided to re-architect the entire system into a monolith. The core logic of their media converter and defect detector microservices was sound, so they reused much of the code. Now that their media converter and defect detector ran on the same server, there was no longer a need for an intermediary storage system.

**Result:** This monolithic conversion ended up saving their organization **90% on their monthly AWS bill**.

### Case 2 — Segment (2017)

Segment is a customer data platform that collects data and sends it to partner tools like Google Analytics, Salesforce, etc.

In 2013, Segment started with a monolithic architecture. The lack of isolation within the monolith was addressed by moving to microservices, with one worker service per destination. Microservices improved modularity and visibility throughout the system.

A period of hypergrowth around 2016–2017 added over 50 new destinations — about three per month. Having a code repository for each service was manageable for a handful of destination workers, but became a problem as the scale increased. Shared libraries were created to provide behaviour that was similar for all workers. However, this created a new bottleneck where changes to the shared code could require a week of developer effort.

**What they did:** The decision in 2017 to move back to a monolith considered all the trade-offs. The resulting architecture, named **Centrifuge**, is able to handle billions of messages per day sent to dozens of public APIs. There is now a single code repository, and all destination workers use the same version of the shared library.

---

*Assignment submitted by Group Four*
