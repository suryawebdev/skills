Generate a complete Architectural Reference Document (ARD) for this project, then produce a standalone HTML version that can be opened in any browser.

If $ARGUMENTS is provided, treat it as a specific directory, repo path, or technology focus to prioritize.

---

## Phase 1 — Codebase Exploration

Read the project thoroughly before writing anything. Cover:

**Project structure**
- Root files: package.json / pom.xml / build.gradle / Cargo.toml / go.mod / requirements.txt — identify language, framework, version
- Directory layout: identify all major layers (api, services, models, controllers, components, etc.)
- Any README, CLAUDE.md, or docs/ folder

**Backend (if present)**
- All controllers/routes — every endpoint (method, path, auth requirement)
- Service layer — business logic, inter-service dependencies, external calls
- Data layer — ORM entities, schema, relationships, custom queries
- Security config — auth mechanism, roles, filters, CORS
- Configuration — all config files, environment variables, profiles (dev/prod/test)
- Scheduled tasks, background jobs
- External integrations (email, payments, storage, third-party APIs)
- Exception handling strategy
- Caching annotations or config
- WebSocket / real-time features

**Frontend (if present)**
- Framework and version, build tool, deployment target
- Routing — all routes, guards, lazy loading
- Component tree — major components and their responsibilities
- Services — HTTP calls, state management, auth handling
- HTTP interceptors
- Models / interfaces
- Forms and validation
- Styling approach
- Environment config files

**Infrastructure**
- Dockerfile, docker-compose, CI/CD files
- Deployment platform config (railway.toml, vercel.json, render.yaml, etc.)
- Database type and hosting

---

## Phase 2 — Generate the ARD

Produce a complete ARD in markdown with all of these sections. Do not skip sections — write "Not applicable" or "Not implemented" where genuinely absent.

### 1. System Context
- High-level ASCII diagram: actors → frontend → backend → database → external services
- User roles and permissions table
- System boundaries table (inside vs outside scope)

### 2. Layered Architecture
- Backend layer-by-layer ASCII diagram (filter → controller → service → repository → DB)
- Frontend layer-by-layer ASCII diagram (routing → components → services → HTTP → state)

### 3. Component Control Map
- Backend: full tree from main app → config → controllers → services → repositories
- Frontend: full tree from root component → routes → components → services

### 4. Service Dependencies
- Backend service dependency graph (which service depends on which)
- Frontend service dependency graph

### 5. Entity Relationships
- Full ERD as ASCII diagram with all tables, columns, PKs, FKs, and cardinality
- Cardinality summary table

### 6. Flow Aggregations
- One ASCII sequence diagram per major flow:
  - Registration / onboarding flow
  - Core user action flow (the primary thing users do)
  - Admin / management flow
  - Any background job or scheduled flow
  - Any external integration flow

### 7. API Call Patterns
- Complete endpoint inventory grouped by resource (method, path, auth, description)
- Key request/response JSON shapes

### 8. Auth & Security Architecture
- Auth token lifecycle diagram
- Security filter chain diagram
- Role-based access control matrix
- Any security gaps or known issues

### 9. Profiles & Configuration
- All profiles/environments and what changes between them
- Complete environment variable reference table (name, required, default, purpose)
- Scheduled tasks table

### 10. Error Handling
- Backend error handling table (exception → handler → HTTP status → response shape)
- Frontend error handling table (error source → handler → user feedback)

### 11. Deployment & Infrastructure
- Current deployment architecture ASCII diagram
- Dockerfile summary
- Deployment checklist

### 12. Kubernetes Readiness
- Readiness assessment table
- Suggested manifest sketch (Deployment + Service + Ingress)
- Scaling concerns

### 13. Resilience & Fault Tolerance
- Current mechanisms table
- Single points of failure table with mitigations
- Recommended improvements list

### 14. Observability
- Current stack table (layer → tool → coverage)
- Logging events table
- Gaps and recommendations table

### 15. Caching
- Current state (what is / isn't cached)
- Cache candidates table (endpoint, frequency, staleness tolerance, strategy)
- Code snippet for recommended implementation

### 16. Architectural Decisions (ADRs)
- One ADR per significant decision:
  - Decision, Rationale, Trade-offs, Status
  - Cover: auth approach, database choice, deployment platform, real-time strategy, state management, any notable workarounds

### Appendices
- Any domain-specific conventions (naming, formats, offsets, scoring rules, etc.)
- Known tech debt or flagged items

---

## Phase 3 — Generate the HTML file

After writing the markdown ARD, produce a single self-contained `ARD.html` file in the project root with:

- Dark theme (black background, light text)
- Sticky sidebar navigation with active-section highlighting on scroll
- All sections rendered with proper formatting:
  - ASCII diagrams in monospace code blocks with subtle borders
  - Tables with zebra striping and hover highlight
  - Color-coded status badges (green = good, yellow = warning, red = gap)
  - Callout boxes for action items and warnings
- TOC grid at the top linking to all sections
- No external dependencies — fully offline-capable (no CDN links)
- Document metadata: project name, version 1.0, generation date

---

## Output

1. Write `ARD.md` to the project root
2. Write `ARD.html` to the project root
3. Confirm both files created and state the section count

Do not ask for confirmation before starting. Explore first, write second.
