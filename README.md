# TransitFM

**Sample technical documentation for a facilities management platform**

TransitFM is a fictional facilities management platform designed to demonstrate how maintenance teams can manage assets, preventive maintenance activities, corrective work orders, inspections, and operational records across a large transport facility.

This repository is a technical writing portfolio project. It demonstrates documentation practices for enterprise software, including product documentation, workflow documentation, API examples, user guidance, and developer-focused content.

> **Portfolio disclaimer:** TransitFM is a fictional system created for demonstration purposes. The documentation does not describe or reproduce any proprietary system, organisation, customer implementation, or confidential business process.

---

## Overview

Large transport facilities contain thousands of maintainable assets, including mechanical, electrical, structural, and building-services equipment.

TransitFM provides a central platform for maintenance teams to:

* register and manage assets;
* schedule preventive maintenance;
* create and track corrective work orders;
* complete inspection and maintenance checklists;
* record maintenance findings;
* assign work to technicians;
* track work-order status;
* manage supporting photographs and attachments; and
* maintain an auditable history of maintenance activities.

The platform is designed for several user groups, including maintenance planners, supervisors, technicians, administrators, and operations teams.

---

## Documentation

### Getting Started

Learn the core concepts used throughout TransitFM.

* [Getting Started](docs/getting-started.md)
* [Understanding Assets](docs/assets.md)
* [Roles and Permissions](docs/roles-and-permissions.md)

### Work Management

Learn how maintenance activities are planned, created, executed, and completed.

* [Work Order Overview](docs/work-orders.md)
* [Preventive Maintenance](docs/preventive-maintenance.md)
* [Corrective Work Orders](docs/corrective-work-orders.md)
* [Maintenance Checklists](docs/checklists.md)
* [Work Order Lifecycle](docs/work-order-lifecycle.md)

### Developer Documentation

Resources for developers integrating external systems with TransitFM.

* [API Overview](api/README.md)
* [Work Orders API](api/work-orders-api.md)
* [Assets API](api/assets-api.md)
* [Error Handling](api/error-handling.md)

---

# Core Concepts

## Asset

An **asset** is a maintainable item recorded in TransitFM.

Examples include:

* air-handling units;
* pumps;
* escalators;
* lighting systems;
* ventilation equipment; and
* electrical distribution equipment.

Each asset can contain information such as:

| Field                | Description                                   |
| -------------------- | --------------------------------------------- |
| Asset ID             | Unique identifier for the asset               |
| Asset name           | Human-readable asset name                     |
| Category             | Type of equipment                             |
| Location             | Physical location of the asset                |
| Status               | Current operational state                     |
| Maintenance strategy | Preventive or corrective maintenance approach |

---

## Work Order

A **work order** represents a maintenance activity that must be performed.

A work order normally contains:

* a work-order number;
* asset information;
* location;
* work description;
* priority;
* assigned technician or team;
* target completion date;
* checklist requirements; and
* current status.

Two common work-order types are supported.

### Preventive Maintenance Work Order

Preventive maintenance work orders are created for scheduled maintenance activities.

Examples include:

* monthly equipment inspections;
* lubrication;
* filter replacement;
* safety checks; and
* scheduled servicing.

### Corrective Work Order

Corrective work orders are used when a defect or abnormal condition requires investigation or repair.

For example:

> During a scheduled inspection, a technician identifies abnormal vibration from a ventilation fan.

The technician can record the finding and create a corrective work order for further investigation.

---

# Example Work Order Lifecycle

A typical work order moves through several states.

```text
Draft
  ↓
Open
  ↓
Assigned
  ↓
In Progress
  ↓
Completed
  ↓
Closed
```

A work order may also move to an exception state.

```text
In Progress
     ↓
   On Hold
     ↓
In Progress
```

The exact transition available to a user depends on their role and the current work-order state.

---

# Example: Complete a Preventive Maintenance Task

The following example shows a typical maintenance workflow.

## 1. Open the assigned work order

From **My Work Orders**, select the required maintenance task.

Review:

* asset details;
* maintenance instructions;
* priority;
* due date; and
* required checklist.

## 2. Start the work

Select **Start Work**.

The work-order status changes from:

```text
Assigned → In Progress
```

The system records the start time and user performing the action.

## 3. Complete the checklist

Complete each required checklist item.

Example:

| Inspection item                      | Response    |
| ------------------------------------ | ----------- |
| Inspect equipment for visible damage | Pass        |
| Check for abnormal vibration         | Pass / Fail |
| Inspect mounting points              | Pass / Fail |
| Record operating condition           | Text        |
| Upload supporting photograph         | Attachment  |

Mandatory checklist items must be completed before the work order can be submitted.

## 4. Record findings

Add any relevant observations.

Example:

```text
Minor vibration detected during inspection.
No visible damage observed.
Further inspection recommended.
```

If additional maintenance is required, create a corrective work order.

## 5. Complete the work order

Select **Complete Work**.

The system validates that:

* mandatory checklist items are complete;
* required fields contain values; and
* required evidence has been provided.

The work order then moves to:

```text
In Progress → Completed
```

Depending on the organisation's workflow, a supervisor may review the work before the work order is closed.

---

# Example Corrective Maintenance Scenario

Consider the following scenario:

A technician performs a preventive inspection of an air-handling unit.

During the inspection, the technician discovers that the unit is producing abnormal vibration.

Instead of modifying the original preventive maintenance task, the technician creates a new corrective work order.

```text
Preventive Maintenance Work Order
            │
            │ Finding detected
            ↓
Corrective Work Order
            │
            ↓
Investigation
            │
            ↓
Repair
            │
            ↓
Verification
```

Maintaining separate work records provides clearer traceability between the scheduled maintenance activity and the resulting repair.

---

# API Example

External systems can create work orders through the TransitFM REST API.

## Request

```http
POST /api/v1/work-orders
Content-Type: application/json
Authorization: Bearer <token>
```

```json
{
  "assetId": "AHU-00142",
  "type": "CORRECTIVE",
  "priority": "MEDIUM",
  "title": "Investigate abnormal vibration",
  "description": "Abnormal vibration observed during scheduled inspection."
}
```

## Response

```json
{
  "workOrderId": "WO-10482",
  "status": "OPEN",
  "createdAt": "2026-08-24T08:30:00Z"
}
```

A successful request returns `201 Created`.

For complete request and response definitions, see the [Work Orders API](api/work-orders-api.md).

---

# Documentation Principles

The documentation in this repository follows several principles.

### Task-oriented

User documentation focuses on what users need to accomplish rather than describing every interface element.

### Scannable

Headings, tables, lists, examples, and short sections allow readers to locate information quickly.

### Audience-specific

Content is separated where appropriate for:

* operational users;
* administrators;
* maintenance personnel; and
* developers.

### Example-driven

Technical concepts are accompanied by realistic examples to help users understand expected system behaviour.

### Maintainable

Documentation is written in Markdown and structured as modular topics so individual pages can be updated without rewriting an entire manual.

---

# About This Project

This repository was created as part of my technical writing portfolio.

My professional background includes business analysis, enterprise software implementation, technical documentation, requirements engineering, software testing, workflow documentation, and collaboration with software development teams.

This project demonstrates my approach to:

* technical writing;
* information architecture;
* developer documentation;
* API documentation;
* software workflow documentation;
* Markdown;
* Git-based documentation; and
* translating complex system behaviour into clear user guidance.
