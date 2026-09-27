# Finvia E-Commerce

A full-featured e-commerce storefront and admin dashboard built with Next.js 15, TypeScript, Tailwind CSS, and shadcn/ui components.

## What it does

**Finvia Store** is a complete demo e-commerce application covering both the customer-facing shop and a back-office admin panel:

- **Storefront** — homepage with hero section, category browsing (Men's Clothing, Women's Clothing, Kids Wear, Combo Offers, Hoodies), product cards, product detail pages, top-sellers listing, search, cart, wishlist, and order tracking.
- **Auth flows** — login and registration pages backed by mock API routes (`/api/auth/login`, `/api/auth/register`, `/api/user/update`).
- **Admin dashboard** — admin-only area (`/admin`) guarded by middleware: revenue/sales charts, customer stats, recent orders, top products, inventory management, and date-range filtered reports.
- **Extras** — multi-currency selector, dark-mode theming (`next-themes`), toast notifications, and Vercel Analytics wiring.

> Note: product catalog, users, and auth are mock/in-memory (see `lib/`). There is no real database or payment gateway — this is a UI/UX reference implementation generated with v0.

## Tech stack

- **Framework:** Next.js 15 (App Router), React 19, TypeScript
- **Styling:** Tailwind CSS 3.4, `tailwindcss-animate`, shadcn/ui + Radix UI primitives
- **Charts:** Recharts, chart.js, react-chartjs-2
- **Forms:** react-hook-form + zod validation
- **Misc:** lucide-react icons, embla-carousel, cmdk command palette, sonner toasts, date-fns, xlsx (report export), next-themes

## Quick start

Prerequisites: Node.js 18+ and npm (or pnpm/yarn).

```bash
npm install
npm run dev
```

Open http://localhost:3000. Admin area: http://localhost:3000/admin (requires a mock admin login — check `lib/auth.ts` for seeded users).

Production build:

```bash
npm run build
npm run start
```

## Project structure

```
app/                  # Next.js App Router
  page.tsx            # storefront homepage
  cart/               # cart page
  wishlist/           # wishlist page
  product/[id]/       # product detail
  category/[slug]/    # category listing
  auth/login|register # auth pages
  admin/              # admin dashboard (dashboard, inventory, reports)
  api/                # mock API routes (auth login/register, user update)
components/           # UI components
  ui/                 # shadcn/ui primitives
  admin/              # admin dashboard widgets (charts, stats)
  auth/               # login/register forms
  cart-provider.tsx   # cart state
  site-header.tsx     # header w/ search + currency selector
lib/                  # helpers: products catalog, auth, utils
middleware.ts         # admin route guard
public/               # static assets
styles/               # global styles
```

## Environment variables

None required — all data is mocked in `lib/`. Optional: add `NEXT_PUBLIC_*` analytics keys as needed.

## Deployment

Deploys as a standard Next.js app (Vercel recommended: `vercel deploy`). Needs a Node server or serverless runtime because it uses API routes and middleware — it cannot be statically exported.

---

Built by Girish Lade — https://ladestack.in
