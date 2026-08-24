# Work Orders API

The TransitFM Work Orders API enables programmatic creation, retrieval, updating, and management of work orders.

## Base URL

```
https://api.transitfm.com/v1
```

## Authentication

All API requests require authentication using a Bearer token:

```
Authorization: Bearer YOUR_API_TOKEN
```

Obtain your API token from **Settings** → **API Tokens** → **Generate New Token**.

## Endpoints

### List Work Orders

Retrieve a paginated list of work orders.

**Request:**
```
GET /work-orders
```

**Query Parameters:**
- `status` (optional) - Filter by status: draft, open, in_progress, on_hold, completed, closed
- `facility_id` (optional) - Filter by facility
- `assigned_to` (optional) - Filter by assigned user ID
- `priority` (optional) - Filter by priority: critical, high, medium, low
- `limit` (optional, default: 20, max: 100) - Number of results to return
- `offset` (optional, default: 0) - Pagination offset

**Response:**
```json
{
  "data": [
    {
      "id": "wo-12345",
      "title": "HVAC Filter Replacement",
      "facility_id": "fac-001",
      "priority": "high",
      "status": "open",
      "assigned_to": "user-456",
      "created_at": "2025-01-15T10:30:00Z",
      "updated_at": "2025-01-15T14:45:00Z"
    }
  ],
  "pagination": {
    "total": 150,
    "limit": 20,
    "offset": 0
  }
}
```

### Get Work Order Details

Retrieve detailed information for a specific work order.

**Request:**
```
GET /work-orders/{id}
```

**Response:**
```json
{
  "id": "wo-12345",
  "title": "HVAC Filter Replacement",
  "description": "Replace HVAC filters in main building",
  "facility_id": "fac-001",
  "category": "hvac",
  "priority": "high",
  "status": "open",
  "assigned_to": "user-456",
  "estimated_duration_minutes": 60,
  "target_completion_date": "2025-01-20T17:00:00Z",
  "created_at": "2025-01-15T10:30:00Z",
  "updated_at": "2025-01-15T14:45:00Z",
  "created_by": "user-123",
  "notes": [],
  "attachments": []
}
```

### Create Work Order

Create a new work order.

**Request:**
```
POST /work-orders
```

**Request Body:**
```json
{
  "title": "HVAC Filter Replacement",
  "description": "Replace HVAC filters in main building",
  "facility_id": "fac-001",
  "category": "hvac",
  "priority": "high",
  "assigned_to": "user-456",
  "estimated_duration_minutes": 60,
  "target_completion_date": "2025-01-20T17:00:00Z"
}
```

**Response:** (201 Created)
```json
{
  "id": "wo-12345",
  "title": "HVAC Filter Replacement",
  "status": "draft",
  "created_at": "2025-01-15T10:30:00Z"
}
```

### Update Work Order

Update an existing work order.

**Request:**
```
PATCH /work-orders/{id}
```

**Request Body:**
```json
{
  "status": "in_progress",
  "assigned_to": "user-789",
  "priority": "critical"
}
```

**Response:** (200 OK)
```json
{
  "id": "wo-12345",
  "status": "in_progress",
  "updated_at": "2025-01-15T15:20:00Z"
}
```

### Delete Work Order

Delete a work order (only draft status).

**Request:**
```
DELETE /work-orders/{id}
```

**Response:** (204 No Content)

### Add Work Order Note

Add a note or work log to a work order.

**Request:**
```
POST /work-orders/{id}/notes
```

**Request Body:**
```json
{
  "content": "Started work on HVAC filters. Found additional damage.",
  "note_type": "work_log"
}
```

**Response:** (201 Created)
```json
{
  "note_id": "note-001",
  "content": "Started work on HVAC filters. Found additional damage.",
  "created_at": "2025-01-16T09:15:00Z",
  "created_by": "user-456"
}
```

## Status Codes

- `200 OK` - Successful GET or PATCH request
- `201 Created` - Successful POST request
- `204 No Content` - Successful DELETE request
- `400 Bad Request` - Invalid request parameters
- `401 Unauthorized` - Missing or invalid authentication
- `403 Forbidden` - Insufficient permissions
- `404 Not Found` - Resource not found
- `422 Unprocessable Entity` - Validation error
- `500 Internal Server Error` - Server error

## Rate Limiting

API requests are rate limited to 1000 requests per hour per API token.

Rate limit headers:
- `X-RateLimit-Limit` - Maximum requests per hour
- `X-RateLimit-Remaining` - Remaining requests
- `X-RateLimit-Reset` - Unix timestamp of rate limit reset

## Error Responses

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid priority value",
    "details": [
      {
        "field": "priority",
        "message": "Must be one of: critical, high, medium, low"
      }
    ]
  }
}
```