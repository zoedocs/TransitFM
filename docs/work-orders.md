# Work Orders

Work orders are the core of TransitFM's maintenance management system. This document covers creating, managing, and tracking work orders throughout their lifecycle.

## What is a Work Order?

A work order is a documented request for maintenance or repairs at a specific facility. It includes details about the work needed, assigned personnel, priority levels, and tracking information.

## Creating a Work Order

### Steps to Create

1. Navigate to **Work Orders** → **New Work Order**
2. Fill in the following required fields:
   - **Title** - Brief description of the work needed
   - **Facility** - Location where work will be performed
   - **Priority** - Select from Critical, High, Medium, or Low
   - **Category** - Classification of maintenance type
   - **Description** - Detailed explanation of the issue

3. Assign the work order to a team member
4. Set the target completion date
5. Click **Create**

## Work Order Statuses

- **Draft** - Initial state, not yet assigned
- **Open** - Assigned and waiting for work to begin
- **In Progress** - Currently being worked on
- **On Hold** - Temporarily paused
- **Completed** - Work finished and verified
- **Closed** - Final status after review

## Managing Work Orders

### Assigning Work Orders
- Work orders can be assigned to individual team members or work teams
- Reassign as needed if circumstances change
- Automated notifications alert assignees of new work orders

### Updating Status
Team members can update work order status as they progress through tasks. All status changes are logged with timestamps.

### Adding Notes
Add internal notes and work logs to document:
- Work completed
- Issues encountered
- Materials used
- Time spent on maintenance

## Work Order Closure

Before closing a work order:
1. Ensure all work is documented
2. Add completion notes
3. Attach any photos or reports
4. Assign quality assurance verification if required
5. Mark as **Completed**

## API Integration

For programmatic work order management, see [Work Orders API](../api/work-orders-api.md).