# Roles and Permissions

TransitFM uses a role-based access control (RBAC) system to ensure users have appropriate permissions for their responsibilities.

## Built-in Roles

### Administrator
- Full system access
- User and team management
- System configuration
- Financial and reporting access
- Facility setup and management

Permissions: All

### Facility Manager
- Manage work orders within assigned facilities
- Schedule preventive maintenance
- View team performance metrics
- Generate facility-specific reports
- Manage facility locations and contacts

Permissions:
- Create and edit work orders
- Assign work orders
- View facility reports
- Manage preventive maintenance plans
- Access facility dashboard

### Technician
- View assigned work orders
- Update work order status
- Log work hours and materials
- Access mobile app for fieldwork
- Upload completion documentation

Permissions:
- View assigned work orders
- Update work order status
- Add work logs and notes
- View work order details
- Submit completion reports

### Supervisor
- Monitor team work orders
- Review and approve completed work
- Manage team schedules
- Generate team performance reports
- Handle escalated issues

Permissions:
- View team work orders
- Approve work order completion
- View team performance metrics
- Manage team availability
- Access supervisory dashboard

### Viewer
- Read-only access to assigned facilities
- View work order history
- Access reports (limited)
- No editing capabilities

Permissions:
- View work orders
- View facility information
- View reports
- Access dashboard (read-only)

## Custom Roles

Organizations can create custom roles by:
1. Navigate to **Administration** → **Roles**
2. Click **Create Custom Role**
3. Select base permissions from available features
4. Define scope (all facilities or specific facilities)
5. Assign the role to users

## Permission Categories

### Work Order Permissions
- Create work orders
- Edit work orders
- Delete work orders
- Assign work orders
- View all work orders
- View assigned work orders only

### Maintenance Permissions
- Create maintenance plans
- Edit maintenance plans
- View maintenance plans
- Execute maintenance tasks

### User Management Permissions
- Create users
- Edit users
- Deactivate users
- Assign roles
- View user activity logs

### Financial Permissions
- View costs
- Manage budgets
- Access financial reports
- Approve purchase orders

### System Permissions
- Configure system settings
- Manage integrations
- View audit logs
- Backup and restore data

## Assigning Roles to Users

### Individual User Assignment
1. Navigate to **Administration** → **Users**
2. Select the user
3. Click **Edit**
4. Select role from dropdown
5. Choose facility scope if applicable
6. Click **Save**

### Bulk Role Assignment
1. Navigate to **Administration** → **Users**
2. Select multiple users using checkboxes
3. Click **Bulk Actions** → **Assign Role**
4. Select role and facilities
5. Click **Apply**

## Permission Hierarchy

Permissions follow a hierarchical structure:
- Administrator role overrides all permissions
- Facility Manager can override Technician permissions within their facility
- Supervisor can view but not modify Technician work orders
- Viewers have read-only access to their scope

## Audit and Compliance

All permission changes are logged including:
- User making the change
- Role or permission modified
- Timestamp of change
- Facility or scope affected

Access the audit log in **Administration** → **Audit Logs**.

## Best Practices

- Follow the principle of least privilege
- Regularly review and update user permissions
- Use built-in roles before creating custom roles
- Document any custom role definitions
- Monitor permission-related audit logs
- Deactivate users who no longer need access