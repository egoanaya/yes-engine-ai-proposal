# Yes Engine: AI-Assisted Shift-Swap Validation and Approval System

**Springboard AI for Programmers. Week 7 Final Project**

**Project Option 2**: Comprehensive AI Project Proposal

**Project Status**: Proposed Architecture and Implementation Plan

Technology Focus: Python, OpenAI API, Structured Outputs, Retrieval-Augmented Generation (RAG), Human-in-the-Loop (HITL), and AI Observability

-------------------------------------------------------------

## 1. Project Overview
The Yes Engine is a proposed AI-assisted system for validating and approving shift swaps, designed to simplify employee scheduling requests, maintain operational compliance, reduce administrative workload, and preserve human oversight.

The project builds on an earlier workflow automation initiative I explored in my professional environment, where I investigated using Microsoft Forms, Excel, and Power Automate to streamline employee shift exchanges.

The original concept relied primarily on structured form submissions, spreadsheet calculations, and predefined business rules. While this approach showed how automation could reduce repetitive administrative tasks, it also revealed opportunities to introduce more flexible and intelligent interactions.

The proposed Yes Engine builds on this concept by incorporating Large Language Models (LLMs), Python-based validation, structured outputs, and human-in-the-loop approval checkpoints.

Rather than requiring employees to fill out multiple form fields, the proposed system would allow users to submit natural-language requests, such as:
"Can I swap my Friday closing shift with another team member who works earlier that day?"

The AI would interpret the request, identify the required scheduling information, and convert it into a structured format. A deterministic validation engine would then evaluate the proposed exchange against the applicable scheduling constraints.

Before finalizing any schedule modification, the system would present its findings to an authorized reviewer for approval, correction, or rejection.

The objective is not to replace Workforce Management professionals but to provide an intelligent decision-support tool that reduces manual verification and improves the consistency, transparency, and efficiency of shift-swap processing.

-------------------------------------------------------------

## 2. Problem Statement

Employee shift exchanges can require multiple administrative steps, including verifying employee schedules, confirming agreement between team members, calculating working hours, reviewing scheduling policies, and determining whether a proposed exchange is operationally acceptable.

When these checks are performed manually, the process can become repetitive, time-consuming, and prone to inconsistencies.

Traditional workflow automation can address some of these challenges through structured forms and deterministic business rules. However, these workflows may struggle with incomplete submissions, conversational requests, policy explanations, and unusual scheduling scenarios.

The Yes Engine proposes an AI-assisted approach that combines flexible natural-language processing with reliable rule-based validation.

The system would address four primary challenges:
1.	**Manual administrative workload**: Reduce repetitive data collection and preliminary scheduling verification.
2.	**Unstructured employee requests**: Translate conversational requests into consistent, machine-readable information.
3.	**Scheduling compliance**: Evaluate requests against documented constraints using deterministic Python logic rather than relying on AI-generated assumptions.
4.	**Decision transparency**: Provide clear validation results and explanations while keeping final scheduling decisions under human control.

-------------------------------------------------------------

## 3. Project Objectives

The proposed system is designed to achieve the following objectives:
- Simplify employee shift-swap requests through natural-language interactions.
- Extract employee names, shift dates, times, and swap details into structured JSON objects.
- Retrieve relevant scheduling policies and supporting documentation when necessary.
- Validate scheduling constraints using Python-based calculations and predefined business rules.
- Identify missing information, scheduling conflicts, and requests requiring additional review.
- Implement human-in-the-loop checkpoints before approving or executing schedule modifications.
- Generate standardized decisions and structured records suitable for spreadsheet-based workflows.
- Establish evaluation metrics and observability practices to monitor reliability, consistency, and potential policy violations.

-------------------------------------------------------------

## 4. Project Scope and Assumptions

This project is a comprehensive technical proposal rather than a deployed software application.

The proposed implementation will use fictional employee identities, simulated schedules, and illustrative scheduling rules to demonstrate the intended system behavior.

Any references to existing enterprise tools or Workforce Management platforms indicate potential integration opportunities rather than confirmed technical connections.

Actual deployment would require authorized access to scheduling systems, formal policy verification, security reviews, and approval from the relevant operational stakeholders.

The design prioritizes reliability, maintainability, transparency, and responsible AI use over unfettered automation.

-------------------------------------------------------------

**Disclaimer: No live employee scheduling data, confidential company policies, or production system credentials are included in this public repository.**

-------------------------------------------------------------

## 5. Target Users and Stakeholders

The Yes Engine is designed to support three primary user groups in an employee scheduling environment.

-------------------------------------------------------------

### 5.1 Employees

Employees would use the system to submit shift-swap requests via natural language or a structured form.

The proposed interface would allow employees to:

- Request single-day or full-week shift exchanges.
- Identify the coworker involved in the exchange.
- Confirm that both employees have agreed to the proposed swap.
- Provide missing information when prompted.
- Receive updates regarding the status of their request.

-------------------------------------------------------------

### 5.2 Team Leaders and Authorized Reviewers

Team leaders or designated scheduling reviewers would review proposed changes before final approval.

Their responsibilities would include:

- Reviewing AI-extracted scheduling information.
- Examining validation results and potential policy conflicts.
- Approving, correcting, rejecting, or escalating requests according to their authorization.
- Providing feedback when the system produces incomplete or inaccurate recommendations.

-------------------------------------------------------------

### 5.3 Workforce Management (WFM)

Workforce Management professionals would provide domain expertise and help establish policies governing shift exchanges.

Their responsibilities in the proposed implementation would include:

- Reviewing and validating scheduling rules.
- Defining acceptable working-hour limits and required rest periods.
- Identifying additional restrictions related to staffing and coverage.
- Reviewing exceptions and escalated requests.
- Evaluating whether the system's proposed decisions align with operational requirements.

The team would establish final approval authority through an agreed operational policy before deployment.

-------------------------------------------------------------

## 6. Proposed Core Workflow

The Yes Engine would use a sequential workflow combining AI-assisted information extraction, deterministic scheduling checks, and human approval.

-------------------------------------------------------------

### Step 1: Employee Submits a Request

An employee initiates a shift exchange via a proposed conversational interface or a structured form.

Example request:
"Can I trade my Friday closing shift for Alex's morning shift? We have already agreed to switch shifts."

The system would collect the request without assuming that all necessary details have been included.

-------------------------------------------------------------

### Step 2: AI Extracts Structured Information

An LLM would analyze the employee's request and extract relevant information into a predefined JSON schema.

Potential fields include:

- Requesting employee
- Swap partner
- Requested date or date range
- Original shift
- Proposed replacement shift
- Swap type
- Partner agreement confirmation

Pydantic models would validate the structure of the extracted data.

Missing or ambiguous details would prompt a clarification request rather than an automatic assumption.

-------------------------------------------------------------

### Step 3: Retrieve Scheduling Policies and Data

The proposed system would retrieve relevant scheduling information from authorized sources.

A Retrieval-Augmented Generation (RAG) component could provide contextual information from approved policy documents.

Current shift assignments and working hours would be retrieved separately from the structured scheduling records.

The system would maintain a distinction between retrieved policy guidance and authoritative numerical scheduling data.

-------------------------------------------------------------

### Step 4: Validate the Proposed Exchange

A Python-based validation engine would evaluate the request against the applicable scheduling constraints.

Illustrative checks include:

- Whether both employees are assigned to the relevant shifts.
- Whether the proposed exchange creates overlapping assignments.
- Whether projected weekly working hours exceed the configured limits.
- Whether mandatory rest periods would be violated.
- Whether the exchange satisfies applicable scheduling and coverage requirements.
- Whether the request falls within an authorized submission window.

These checks would use deterministic calculations and explicitly configured business rules rather than relying on the LLM to assess compliance.

A request that fails a mandatory constraint would be flagged or rejected per the approved workflow.

-------------------------------------------------------------

### Step 5: Human-in-the-Loop Review

Before a schedule change is finalized, the system would present the proposed exchange and validation findings to an authorized human reviewer for review.

The reviewer could:

- Approve the proposed change.
- Request additional information.
- Correct inaccurate information.
- Reject a request.
- Escalate an exception for further review.

The system would pause execution until the required human decision is made.

-------------------------------------------------------------

### Step 6: Generate the Final Decision Record

Following review, the Yes Engine would generate a structured record containing:

- The original request
- Extracted scheduling details
- Validation results
- Applicable policy references
- Reviewer decision and any corrections
- Final request status
- Relevant timestamps

The record could be exported to an Excel-compatible format to support operational review and reporting.

Any future integration that alters a production schedule would require separate authorization and additional safeguards.

-------------------------------------------------------------

### Step 7: Capture Feedback for Improvement

Reviewer corrections and identified errors would be compiled as evaluation examples, subject to appropriate data protection controls.

These examples could help improve:

- Prompt accuracy
- Structured data extraction
- Policy retrieval
- Validation coverage
- Exception handling

The system would use this feedback to support controlled testing and future improvements rather than automatically modifying its own business rules.
