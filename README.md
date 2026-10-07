# Fun Club Management System

A private web application for managing club members and tracking member contributions. Built with Node.js, Express, MySQL, and a vanilla HTML/CSS/JavaScript frontend.

## Architecture Overview

```
┌─────────────────┐     HTTP/REST      ┌─────────────────┐     SQL      ┌─────────────┐
│    Frontend     │ ◄────────────────► │     Backend     │ ◄──────────► │    MySQL    │
│  (HTML/CSS/JS)  │   JSON + JWT       │  (Express API)  │   mysql2     │  Database   │
└─────────────────┘                    └─────────────────┘              └─────────────┘
```

- **Frontend** — Static pages and client-side JavaScript in `frontend/`. Pages call the REST API and store JWT tokens for authenticated requests.
- **Backend** — Express MVC API in `backend/`. Handles authentication, authorization, business logic, and database access.
- **Database** — MySQL schema, migrations, and seeds in `database/`.

## User Roles

| Role   | Access |
|--------|--------|
| Admin  | Full club management: members, contributions, reports, settings |
| Member | Personal dashboard, profile, and own contribution history only |

## Planned Modules

1. Authentication
2. User/Member Management
3. Admin Dashboard
4. Member Dashboard
5. Contribution Management
6. Contribution History
7. Payment/Contribution Reports
8. Profile Management
9. Notifications
10. System Settings

## Project Structure

```
fun-club-management/
├── backend/           # Express REST API (MVC)
│   ├── config/        # Database, JWT, environment config
│   ├── controllers/   # Request handlers (thin layer)
│   ├── middleware/    # Auth, RBAC, validation, error handling
│   ├── models/        # Database queries / data access
│   ├── routes/        # API route definitions
│   ├── services/      # Business logic
│   ├── utils/         # Shared helpers
│   ├── validators/    # Input validation rules
│   ├── database/      # DB connection pool
│   ├── app.js         # Express app setup
│   └── server.js      # Server entry point
├── frontend/          # Client-side UI
│   ├── assets/        # CSS, JS, images, icons
│   ├── pages/         # HTML pages (auth, admin, member)
│   ├── components/    # Reusable HTML partials
│   └── index.html     # Landing / redirect page
├── database/          # SQL schema, migrations, seeds
├── .env.example       # Environment variable template
└── package.json       # Dependencies and scripts
```

## API Route Plan (Future)

| Area | Prefix | Description |
|------|--------|-------------|
| Auth | `/api/auth` | Login, token refresh |
| Admin | `/api/admin` | Members, contributions, stats, settings |
| Member | `/api/member` | Profile, own contributions |
| Notifications | `/api/notifications` | User notifications |

## Frontend Page Plan (Future)

### Admin
- `/admin/dashboard`
- `/admin/members`
- `/admin/members/create`
- `/admin/members/:id`
- `/admin/contributions`
- `/admin/contributions/create`
- `/admin/contributions/:id`

### Member
- `/member/dashboard`
- `/member/profile`
- `/member/contributions`

## Database Tables

| Table | Purpose |
|-------|---------|
| `users` | Admin and member accounts (roles: admin, member) |
| `contributions` | Payment/contribution records per member |
| `contribution_categories` | Optional categorization of contributions |
| `notifications` | In-app notifications |
| `audit_logs` | Admin action audit trail |
| `club_settings` | Club name, contact info, and configuration |

## Security (Planned)

- Password hashing with **bcrypt**
- **JWT**-based authentication
- **Role-based access control** (admin vs member)
- Protected API routes via middleware
- Input validation with **express-validator**
- Environment variables for secrets and DB credentials
- Members can only access their own contribution data

## Getting Started

### Prerequisites

- Node.js 18+
- MySQL 8+

### Setup

```bash
# Clone or navigate to the project
cd fun-club-management

# Install dependencies
npm install

# Configure environment
cp .env.example .env
# Edit .env with your MySQL credentials and JWT secret

# Create database and tables (when migrations are ready)
mysql -u root -p < database/schema.sql

# Start development server (when server.js is implemented)
npm run dev
```

## Development Approach

This project is built **in stages**. Stage 1 (current) establishes folder structure and architecture only. Subsequent stages will implement each module step by step.

## License

MIT — see [LICENSE](LICENSE).
