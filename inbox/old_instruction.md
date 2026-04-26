# Commercial Website Prototype

## Project goal

The goal is to build a working prototype of a commercial business website that can later grow into a production-ready system.

The prototype should prove that the project can support:

* public business pages
* store/location information
* promotions and news
* pricing information
* contact or collaboration forms
* multilingual content
* SEO-friendly pages
* admin-managed content

The first version should stay realistic and focused. Advanced features should be delayed until the core website works well.

---

## Prototype scope

### MVP features

The prototype should include:

* Home page
* About page
* Store/location list page
* Store/location detail page
* Promotions or news page
* Pricing page
* Contact form
* Basic admin/content management approach
* SEO metadata support
* Sitemap support
* Responsive design
* Image optimization

### Optional after MVP

These features are useful, but should not block the first prototype:

* loyalty or bonus system
* barcode/account integration
* push notifications
* analytics dashboard
* advanced user accounts
* complex CRM integrations
* payment system

---

## Suggested technology stack

The initial prototype should use a practical, modern stack:

```text
Frontend: Next.js
Language: TypeScript
Styling: Tailwind CSS
Database: PostgreSQL
ORM: Prisma
Backend: Next.js API routes first, NestJS later if needed
Hosting: Vercel or similar platform
Storage: Cloudflare R2 or S3-compatible storage later
DNS/CDN: Cloudflare later
```

This stack is good for the prototype because it supports server-rendered pages, good SEO, reusable frontend components, typed development, and a clear path toward production.

---

## Recommended first technical decision

Start simple:

```text
Next.js + TypeScript + Tailwind CSS
```

Do not add too many backend tools at the beginning.

For the first prototype, mock data or local JSON files are acceptable. Add PostgreSQL and Prisma after the page structure and content model are clear.

Recommended prototype phases:

1. Static public pages with mock data
2. Reusable layout and components
3. Store and promotion data model
4. Database with Prisma + PostgreSQL
5. Admin/content editing
6. Deployment

---

## Planned project structure

A possible starting structure:

```text
repo_project./
├── README.md
├── AGENTS.md
├── package.json
├── next.config.js
├── tsconfig.json
├── .env.example
├── public/
│   └── images/
├── src/
│   ├── app/
│   │   ├── page.tsx
│   │   ├── about/
│   │   ├── stores/
│   │   ├── promotions/
│   │   ├── pricing/
│   │   └── contact/
│   ├── components/
│   ├── data/
│   ├── lib/
│   └── styles/
├── prisma/
│   └── schema.prisma
└── docs/
```

The exact structure can change after the prototype starts.

---

## Pages to build first

### 1. Home page

Purpose:

* explain what the business offers
* show main call-to-action
* highlight stores, promotions, and pricing

Suggested sections:

* hero section
* short business description
* popular services/products
* current promotions
* store/location preview
* contact call-to-action

---

### 2. Stores page

Purpose:

* list all store locations
* allow users to find a nearby or relevant store

Suggested fields:

* store name
* address
* working hours
* phone number
* map link
* available services

---

### 3. Store detail page

Purpose:

* provide detailed information about one location

Suggested fields:

* store name
* address
* working hours
* contact details
* promotions available at this store
* map link
* images

---

### 4. Promotions / news page

Purpose:

* show current offers, updates, and announcements

Suggested fields:

* title
* description
* image
* start date
* end date
* related store/location

---

### 5. Pricing page

Purpose:

* clearly show service or product pricing

Suggested fields:

* category
* item/service name
* description
* price
* notes

---

### 6. Contact page

Purpose:

* let customers contact the business
* support collaboration or partnership requests

Suggested fields:

* name
* email
* phone
* message
* request type

---

## Data model draft

The first real database version may include these entities:

```text
Store
Promotion
PriceItem
Page
ContactRequest
MediaAsset
AdminUser
```

### Store

```text
id
name
slug
address
phone
email
workingHours
mapUrl
isActive
createdAt
updatedAt
```

### Promotion

```text
id
title
slug
description
imageUrl
startDate
endDate
storeId optional
isActive
createdAt
updatedAt
```

### PriceItem

```text
id
category
name
description
price
currency
sortOrder
isActive
createdAt
updatedAt
```

### ContactRequest

```text
id
name
email
phone
requestType
message
status
createdAt
```

---

## Development setup

### Prerequisites

Install:

* Node.js LTS
* npm or pnpm
* Git

PostgreSQL is not required for the earliest static prototype, but it will be needed later.

---

## Getting started

Clone the repository:

```bash
git clone <repository-url>
cd repo_project.
```

Install dependencies:

```bash
npm install
```

Run the development server:

```bash
npm run dev
```

Open the app:

```text
http://localhost:3000
```

---

## Suggested initialization command

If the project has not been initialized yet, start with:

```bash
npx create-next-app@latest . --typescript --tailwind --eslint --app --src-dir
```

Recommended answers:

```text
TypeScript: Yes
ESLint: Yes
Tailwind CSS: Yes
src/ directory: Yes
App Router: Yes
Turbopack: Optional
Import alias: Yes
```

---

## Environment variables

Create an `.env.example` file when backend/database work begins.

Possible future variables:

```env
DATABASE_URL="postgresql://user:password@localhost:5432/commercial_website"
NEXT_PUBLIC_SITE_URL="http://localhost:3000"
ADMIN_EMAIL="admin@example.com"
```

Do not commit real secrets.

---

## Scripts

Expected scripts after project initialization:

```bash
npm run dev
npm run build
npm run start
npm run lint
```

Later, after Prisma is added:

```bash
npx prisma generate
npx prisma migrate dev
npx prisma studio
```

---

## Prototype roadmap

### Phase 1 — Static prototype

Goal: prove page structure and design direction.

Tasks:

* initialize Next.js project
* create layout
* create navigation
* create home page
* create stores page using mock data
* create promotions page using mock data
* create pricing page using mock data
* create contact page UI

---

### Phase 2 — Data model

Goal: define real content structure.

Tasks:

* design TypeScript types
* create mock data files
* decide database schema
* add Prisma
* add PostgreSQL

---

### Phase 3 — Admin/content management

Goal: allow content editing.

Options:

1. Build a small custom admin panel.
2. Use Strapi or another CMS for faster content management.

Decision should be recorded in the knowledge repository before implementation.

---

### Phase 4 — SEO and deployment

Goal: make the site closer to production quality.

Tasks:

* add metadata for pages
* generate sitemap
* add robots.txt
* optimize images
* deploy prototype
* test performance and mobile layout

---

## Documentation rule

This repository should document how to run and develop the application.

The knowledge repository should document why technical choices were made.

When a major implementation choice is made, record it in:

```text
../Knowlage/repo_knowlage./decisions/
```

When a prototype or test is performed, record it in:

```text
../Knowlage/repo_knowlage./expiriments/
```

When raw GPT information is processed into a plan, record it in:

```text
../Knowlage/repo_knowlage./synthesis/
```

---

## First implementation checklist

* [ ] Initialize Next.js project
* [ ] Add `AGENTS.md`
* [ ] Create basic layout
* [ ] Add navigation
* [ ] Build home page
* [ ] Build stores page with mock data
* [ ] Build store detail page with mock data
* [ ] Build promotions page with mock data
* [ ] Build pricing page with mock data
* [ ] Build contact page UI
* [ ] Add responsive styling
* [ ] Add basic SEO metadata
* [ ] Commit first prototype version

---

## Suggested first commit

```bash
git add .
git commit -m "Initialize commercial website prototype"
```

---

## Current status

```text
Prototype planning stage
```

The next step is to initialize the Next.js project and build the first static version using mock data.
