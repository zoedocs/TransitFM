# Bug report

## Environment

- **Environment:** UAT
- **Severity:** High - User without approval permission can approve a work order

### Environment
- **Build:** 4.2.36
- **Environment:** UAT
- **Platform:** Web — Chrome [155.0.8059.39]
- **Module:** Work Order Management / RBAC
- **Severity:** High

### Preconditions
- Test user has work order viewing permission but no approval permission.
- A test work order is in **Pending Approval** status.

### Steps to reproduce
1. Sign in as the test user.
2. Navigate to the work order list.
3. Open a work order in **Pending Approval** status.
4. Click **Approve**.
5. Confirm the approval.

### Expected behaviour
The approval action is unavailable to this user. Any approval request made without the required permission is rejected, and the work order remains **Pending Approval**.

### Actual behaviour
The **Approve** button is available. Confirming the action changes the work order status to **Approved**.

### Impact
Users without approval permission can bypass the approval workflow and change work order status.

### Evidence
[Screenshots or a screen recording showing the user’s permissions and approval action.]

### Release verdict
**Do not release:** Approval permissions must be enforced before release.

### Retest checklist
- [ ] User without approval permission cannot approve through the UI.
- [ ] Approval requests from unauthorised users are rejected.
- [ ] User with approval permission can approve successfully.
- [ ] Failed approval attempts leave the work order status unchanged.
