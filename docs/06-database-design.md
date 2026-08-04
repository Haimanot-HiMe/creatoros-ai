# CreatorOS AI - Database Design

Version: 0.1.0

Status: Draft

---

# 1. Database Overview

CreatorOS AI uses MongoDB as the primary database.

The database follows a document-based structure designed to support:

- Multiple users
- Multiple workspaces
- Multiple creator brands
- Content management
- Analytics tracking
- AI assistance
- Future SaaS expansion

---

# 2. Database Architecture

High-level relationship:

```
User
 |
 |
Workspace
 |
 |
Brand
 |
 ├── Social Accounts
 |
 ├── Content
 |
 ├── Assets
 |
 ├── Analytics
 |
 └── Goals
```

---

# 3. Collections Overview

MongoDB Collections:

```
users

workspaces

brands

socialAccounts

content

assets

analytics

goals

tasks

aiGenerations

notifications
```

---

# 4. Users Collection

Purpose:

Stores account information.

Example:

```javascript
{
  _id,
  name,
  email,
  password,
  role,
  avatar,
  createdAt,
  updatedAt
}
```

Fields:

| Field | Type | Description |
|-|-|-|
| name | String | User full name |
| email | String | Login email |
| password | String | Hashed password |
| role | String | User permission level |
| avatar | String | Profile image |

Roles:

```
owner
creator
teamMember
admin
```

---

# 5. Workspaces Collection

Purpose:

Represents a creator management environment.

Example:

```javascript
{
  _id,
  ownerId,
  name,
  description,
  createdAt
}
```

Relationship:

```
User
 |
owns
 |
Workspace
```

---

# 6. Brands Collection

Purpose:

Stores creator identities.

Example:

```javascript
{
  _id,
  workspaceId,
  name,
  description,
  category,
  audience,
  voice,
  colors,
  logo,
  goals
}
```

Example:

```
Brand:

Alaazar Haimanot

Category:
Education

Audience:
Students and Parents

Voice:
Inspirational + Educational
```

---

# 7. Social Accounts Collection

Purpose:

Stores connected social platforms.

Example:

```javascript
{
 _id,
 brandId,
 platform,
 username,
 followers,
 accessToken
}
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

# 8. Content Collection

Purpose:

Stores content workflow.

Example:

```javascript
{
 _id,
 brandId,
 title,
 type,
 status,
 platform,
 scheduledDate,
 description
}
```

Content Types:

```
video
image
article
live
podcast
```

Content Status:

```
idea

planning

production

review

published
```

---

# 9. Assets Collection

Purpose:

Stores creator files.

Example:

```javascript
{
 _id,
 brandId,
 name,
 type,
 url,
 size,
 tags
}
```

Assets:

```
videos

images

logos

documents

certificates
```

---

# 10. Analytics Collection

Purpose:

Stores performance data.

Example:

```javascript
{
 _id,
 socialAccountId,
 date,
 followers,
 views,
 likes,
 comments,
 shares
}
```

Metrics:

```
Followers

Views

Likes

Comments

Shares

Watch Time

Engagement Rate
```

---

# 11. Goals Collection

Purpose:

Tracks creator objectives.

Example:

```javascript
{
 _id,
 brandId,
 title,
 target,
 current,
 deadline,
 status
}
```

Example:

```
Goal:

Reach 100K TikTok followers

Target:
100000

Current:
15000
```

---

# 12. Tasks Collection

Purpose:

Manages creator workflow.

Example:

```javascript
{
 _id,
 brandId,
 title,
 assignedTo,
 priority,
 status,
 dueDate
}
```

Task Status:

```
todo

inProgress

completed
```

---

# 13. AI Generations Collection

Purpose:

Stores AI assistant history.

Example:

```javascript
{
 _id,
 brandId,
 type,
 input,
 output,
 createdAt
}
```

Types:

```
caption

script

idea

hook

analysis
```

---

# 14. Notifications Collection

Purpose:

Stores user notifications.

Example:

```javascript
{
 _id,
 userId,
 message,
 type,
 read,
 createdAt
}
```

---

# 15. Database Security Rules

The system must ensure:

- Users can only access their own workspaces.
- Brand data belongs to the correct workspace.
- Team permissions are respected.
- Sensitive information is protected.

---

# 16. Future Database Improvements

Possible additions:

- Subscription plans
- Payments
- AI memory
- Advanced analytics
- Community features
- Marketplace data

---

# Database Design Principle

The database should support:

Current Need:

Family creator management

+

Future Need:

Global creator SaaS platform