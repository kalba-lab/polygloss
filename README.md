# Polygloss

Multilingual e-commerce engine (v2). Projects's page: [polygloss.dev](https://polygloss.dev/)

Self-hosted solution for building online stores with native multi-language support. This is the second iteration of the platform, rebuilt from the ground up with a modern tech stack.

## Live Demo

- **Store:** https://demo.polygloss.dev
- **Admin Panel:** https://admin.polygloss.dev
  - Demo access: `demo@polygloss.dev` / `demo123` (read-only)

## Why Polygloss

Machine translation (Google Translate, browser plugins) doesn't work well for e-commerce. Product names get mangled, descriptions lose meaning, customers lose trust.

Polygloss takes a different approach: every piece of content — products, categories, UI elements — has proper translations managed by humans.

## Key Features

- **Native multilingual architecture** — not a plugin, built into the core
- **Unlimited languages** — add as many as needed
- **UI localization** — translate the entire interface, not just products
- **Fallback system** — missing translation? Show default language
- **Self-hosted** — your data stays on your server
- **No payment lock-in** — integrate your own payment provider

## Tech Stack

**Backend**
- Java 21, Spring Boot 3.2
- PostgreSQL 14+
- Spring Security, JWT authentication
- Flyway migrations

**Frontend**
- Angular 19
- Tailwind CSS (storefront)
- Angular Material (admin panel)

## Project Structure

```
polygloss/
├── backend/
│   └── src/main/java/dev/polygloss/
│       ├── config/         # Security, CORS, mail configuration
│       ├── controller/     # REST endpoints
│       ├── dto/            # Data Transfer Objects
│       ├── entity/         # JPA entities
│       ├── exception/      # Custom exceptions
│       ├── mapper/         # Entity-DTO mappers
│       ├── repository/     # Data access layer
│       ├── security/       # JWT filter, authentication
│       └── service/        # Business logic
├── frontend-admin/         # Angular admin panel (Material UI)
├── frontend-shop/          # Angular storefront (Tailwind CSS)
└── README.md
```

## Configuration

Key settings in `application.properties`:

| Property | Description |
|----------|-------------|
| `spring.datasource.url` | PostgreSQL connection URL |
| `spring.datasource.username` | Database user |
| `spring.datasource.password` | Database password |
| `jwt.secret` | JWT signing key (min 64 chars) |
| `app.cors.allowed-origins` | Allowed frontend origins |
| `spring.mail.*` | SMTP configuration for email notifications |

## API Overview

| Resource | Description |
|----------|-------------|
| `/api/languages` | Language management |
| `/api/categories` | Product categories with translations |
| `/api/products` | Products with translations and images |
| `/api/orders` | Order management |
| `/api/ui` | UI element translations |
| `/api/ui-texts` | Long-form content translations |
| `/api/users` | User management (admin) |
| `/api/checkout` | Public checkout flow with email verification |

Full API documentation available via Swagger UI at `/swagger-ui.html`.

## Payment Integration

Polygloss is intentionally shipped without a payment module. Every business has different requirements — payment providers, merchant accounts, regional regulations.

The checkout flow collects customer data and creates orders. Payment integration is left for the implementer to add based on their specific needs.


---

Developed by [Kalba Lab](https://kalba.dev)

