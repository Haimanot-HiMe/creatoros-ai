# CreatorOS AI - API Design

Version: 0.1.0

Status: Draft

---

# 1. API Overview

CreatorOS AI uses a REST API architecture.

The API provides communication between:

- Frontend application
- Backend server
- Database
- External services

Base URL:

```
/api
```

Example:

```
GET /api/brands
```

---

# 2. API Design Principles

The API follows:

- REST architecture
- JSON data format
- JWT authentication
- Role-based authorization
- Input validation
- Error handling standards

---

# 3. Authentication API

Base:

```
/api/auth
```

---

## Register User

```
POST /api/auth/register
```

Purpose:

Create a new user account.

Request:

```json
{
  "name": "Haimanot",
  "email": "user@email.com",
  "password": "password"
}
```

Response:

```json
{
  "message": "User created successfully",
  "userId": "123"
}
```

---

## Login User

```
POST /api/auth/login
```

Purpose:

Authenticate user.

Request:

```json
{
  "email": "user@email.com",
  "password": "password"
}
```

Response:

```json
{
  "token": "jwt_token",
  "user": {}
}
```

---

## Get Current User

```
GET /api/auth/me
```

Purpose:

Return logged-in user information.

Authentication:

Required

---

# 4. Workspace API

Base:

```
/api/workspaces
```

---

## Create Workspace

```
POST /api/workspaces
```

Purpose:

Create creator workspace.

---

## Get Workspaces

```
GET /api/workspaces
```

Purpose:

List user workspaces.

---

## Update Workspace

```
PUT /api/workspaces/:id
```

---

## Delete Workspace

```
DELETE /api/workspaces/:id
```

---

# 5. Brand API

Base:

```
/api/brands
```

---

## Create Brand

```
POST /api/brands
```

Example:

```json
{
"name":"Alaazar Haimanot",
"category":"Education",
"audience":"Students"
}
```

---

## Get Brands

```
GET /api/brands
```

---

## Get Single Brand

```
GET /api/brands/:id
```

---

## Update Brand

```
PUT /api/brands/:id
```

---

## Delete Brand

```
DELETE /api/brands/:id
```

---

# 6. Social Account API

Base:

```
/api/social-accounts
```

---

## Add Platform

```
POST /api/social-accounts
```

Platforms:

```
TikTok

YouTube

Instagram

Facebook

LinkedIn
```

---

## Get Connected Platforms

```
GET /api/social-accounts/:brandId
```

---

# 7. Content API

Base:

```
/api/content
```

---

## Create Content Idea

```
POST /api/content
```

Request:

```json
{
"title":"Math Challenge Episode 1",
"type":"video",
"platform":"TikTok"
}
```

---

## Get Content List

```
GET /api/content
```

---

## Update Content Status

```
PATCH /api/content/:id/status
```

Example statuses:

```
idea

planning

production

review

published
```

---

## Delete Content

```
DELETE /api/content/:id
```

---

# 8. Asset API

Base:

```
/api/assets
```

---

## Upload Asset

```
POST /api/assets/upload
```

Supports:

- Images
- Videos
- Documents

---

## Get Assets

```
GET /api/assets/:brandId
```

---

## Delete Asset

```
DELETE /api/assets/:id
```

---

# 9. Analytics API

Base:

```
/api/analytics
```

---

## Get Brand Analytics

```
GET /api/analytics/:brandId
```

Returns:

```json
{
"followers":10000,
"views":500000,
"engagement":8.5
}
```

---

## Add Analytics Data

```
POST /api/analytics
```

---

# 10. AI Assistant API

Base:

```
/api/ai
```

---

## Generate Content Idea

```
POST /api/ai/idea
```

Request:

```json
{
"brandId":"123",
"topic":"mathematics"
}
```

---

## Generate Caption

```
POST /api/ai/caption
```

---

## Generate Script

```
POST /api/ai/script
```

---

## Analyze Content

```
POST /api/ai/analyze
```

---

# 11. Goal API

Base:

```
/api/goals
```

---

## Create Goal

```
POST /api/goals
```

---

## Get Goals

```
GET /api/goals/:brandId
```

---

## Update Goal Progress

```
PATCH /api/goals/:id
```

---

# 12. Task API

Base:

```
/api/tasks
```

---

## Create Task

```
POST /api/tasks
```

---

## Update Task

```
PATCH /api/tasks/:id
```

---

## Delete Task

```
DELETE /api/tasks/:id
```

---

# 13. Standard Error Response

All errors follow:

```json
{
"success":false,
"message":"Error description"
}
```

---

# 14. API Security

Every protected route must include:

```
Authorization: Bearer TOKEN
```

Security requirements:

- JWT verification
- Role checking
- Input validation
- Rate limiting
- Secure headers

---

# 15. Future API Expansion

Future APIs:

```
/api/mobile

/api/webhooks

/api/integrations

/api/payments

/api/marketplace
```

---

# API Design Principle

The API should be:

- Secure
- Predictable
- Easy to maintain
- Ready for mobile applications
- Ready for future integrations