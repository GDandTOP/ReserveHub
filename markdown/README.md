<div align="center">

# 🏢 Space Hub

**Premium Space Reservation Platform**

[![Next.js](https://img.shields.io/badge/Next.js-16-black?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](./LICENSE)

A full-stack space reservation platform where users can discover, book, and pay for premium venues — from study rooms to large seminar halls — in just a few clicks.

[Live Demo](#) · [Report Bug](#) · [Request Feature](#)

</div>

---

## ✨ Features

### For Users
- 🔐 **Authentication** — Email/password signup and social login via Supabase Auth
- 🏠 **Space Discovery** — Browse a curated catalog of reservable spaces with rich detail pages
- 📅 **Smart Booking** — Interactive date/time slot picker powered by React Day Picker
- 💳 **Secure Payment** — Integrated PortOne (포트원) V2 payment with full cancellation support
- 📋 **My Reservations** — Personal dashboard to view, track, and manage booking history

### For Admins
- 📊 **Analytics Dashboard** — Visual KPIs including daily/monthly revenue, reservation trends, top products, and category breakdowns (Recharts)
- 🗂️ **Product Management** — Full CRUD for spaces with image upload via Supabase Storage
- 🗓️ **Reservation Management** — Calendar and table views for all reservations (React Big Calendar)
- 💰 **Payment Management** — Detailed payment records with refund capabilities
- 🔔 **Real-time Notifications** — Live booking alerts powered by Supabase Realtime

### Infrastructure
- 🛡️ **Row Level Security** — Supabase RLS policies enforce data access at the database level
- 🔒 **Middleware Auth Guard** — Next.js middleware protects user and admin routes
- ⚡ **Server Actions** — Data mutations handled via Next.js Server Actions (no API route boilerplate)

---

## 🏗️ Tech Stack

| Category | Technology |
|---|---|
| **Framework** | Next.js 16 (App Router) |
| **Language** | TypeScript 5 |
| **Styling** | Tailwind CSS v4 |
| **UI Components** | Radix UI + shadcn/ui + Lucide React |
| **Backend / DB** | Supabase (PostgreSQL + Auth + Storage + Realtime) |
| **Payment** | PortOne V2 (포트원) |
| **Charts** | Recharts 3 |
| **Calendar** | React Big Calendar + React Day Picker |
| **Carousel** | Embla Carousel |
| **Validation** | Zod 4 |
| **Toast** | Sonner |

---

## 🚀 Quick Start

### Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) **v18.17+**
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- A [Supabase](https://supabase.com/) account and project
- A [PortOne](https://admin.portone.io/) account (for payment processing)

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/init-nextjs-project.git
cd init-nextjs-project
```

**2. Install dependencies**

```bash
npm install
```

**3. Set up environment variables**

```bash
cp .env.local.example .env.local
```

Open `.env.local` and fill in your credentials (see [Environment Variables](#-environment-variables) section below).

**4. Set up Supabase database**

Run the migrations in order using the Supabase CLI or the SQL editor in your Supabase Dashboard:

```bash
# If using Supabase CLI
supabase db push

# Or manually run the SQL files in your Supabase SQL editor:
# supabase/migrations/*.sql
# supabase/add_products_data.sql  ← seed data
```

**5. Start the development server**

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

**6. Set up admin access**

After creating your account, update your user role to `admin` in the Supabase Dashboard:

```sql
UPDATE profiles SET role = 'admin' WHERE email = 'your-email@example.com';
```

Then navigate to [http://localhost:3000/admin](http://localhost:3000/admin).

---

## 📁 Project Structure

```
init-nextjs-project/
├── src/
│   ├── app/                        # Next.js App Router pages
│   │   ├── actions/                # Server Actions (data mutations)
│   │   │   ├── admin/              # Admin-only server actions
│   │   │   ├── auth.ts             # Login, signup, logout
│   │   │   ├── payment.ts          # PortOne payment & cancellation
│   │   │   ├── products.ts         # Product fetching
│   │   │   └── reservations.ts     # Booking creation & management
│   │   ├── admin/                  # Admin panel (protected)
│   │   │   ├── analytics/          # Revenue & booking analytics
│   │   │   ├── dashboard/          # Overview & quick stats
│   │   │   ├── notifications/      # Real-time notification center
│   │   │   ├── payments/           # Payment records & refunds
│   │   │   ├── products/           # Product CRUD (list, new, edit)
│   │   │   └── reservations/       # Reservation management
│   │   ├── products/[id]/          # Space detail & booking page
│   │   ├── login/                  # Login page
│   │   ├── signup/                 # Registration page
│   │   ├── mypage/                 # User reservation history
│   │   ├── about/                  # About page
│   │   ├── faq/                    # FAQ page
│   │   └── page.tsx                # Landing page (Hero + Carousel + Features)
│   ├── components/
│   │   ├── admin/                  # Admin-specific UI components
│   │   │   ├── analytics/          # Chart components (Recharts)
│   │   │   ├── common/             # Sidebar, Header, Breadcrumb, NotificationBell
│   │   │   ├── dashboard/          # Dashboard widgets
│   │   │   ├── notifications/      # Real-time notification components
│   │   │   ├── payments/           # Payment table & detail modal
│   │   │   ├── products/           # Product form & table
│   │   │   └── reservations/       # Reservation detail modal
│   │   ├── auth/                   # Login & signup forms
│   │   ├── layout/                 # Header, Footer, Navigation
│   │   ├── mypage/                 # User profile & reservation cards
│   │   ├── products/               # Product card, carousel, booking form
│   │   └── ui/                     # shadcn/ui base components
│   ├── lib/
│   │   ├── api/                    # Server-side data fetching helpers
│   │   ├── payment/                # PortOne SDK wrappers
│   │   ├── supabase/               # Supabase client (browser, server, middleware)
│   │   └── utils/                  # Utility functions & mappers
│   └── types/                      # Global TypeScript type definitions
├── supabase/
│   ├── migrations/                 # Ordered database migration files
│   └── add_products_data.sql       # Seed data for products
├── middleware.ts                   # Auth & role-based route protection
├── next.config.ts                  # Next.js configuration
├── components.json                 # shadcn/ui configuration
└── .env.local.example              # Environment variable template
```

---

## 🔧 Environment Variables

Copy `.env.local.example` to `.env.local` and configure the following:

| Variable | Required | Description |
|---|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | ✅ Yes | Your Supabase project URL (`https://xxx.supabase.co`) |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | ✅ Yes | Supabase anonymous key (safe for client-side) |
| `SUPABASE_SERVICE_ROLE_KEY` | ✅ Yes | Supabase service role key (**server-only, never expose**) |
| `NEXT_PUBLIC_APP_URL` | ✅ Yes | Base URL of your app (e.g. `http://localhost:3000`) |
| `NEXT_PUBLIC_PORTONE_STORE_ID` | ✅ Yes | PortOne Store ID from the admin console |
| `NEXT_PUBLIC_PORTONE_CHANNEL_KEY` | ✅ Yes | PortOne Channel Key (PG channel identifier) |
| `PORTONE_V2_API_SECRET` | ✅ Yes | PortOne V2 API Secret (**server-only, never expose**) |
| `NEXT_PUBLIC_PAYMENT_ENV` | ✅ Yes | `development` for test payments, `production` for live |

> **Security Note:** Variables prefixed with `NEXT_PUBLIC_` are exposed to the browser. Never put secret keys there.

---

## 📡 Key Routes

| Route | Description | Access |
|---|---|---|
| `/` | Landing page with hero, featured spaces, and features section | Public |
| `/products` | Space catalog listing | Public |
| `/products/[id]` | Space detail page with booking form | Public |
| `/login` | Login with email or social provider | Public |
| `/signup` | New user registration | Public |
| `/mypage` | User's reservation history | 🔐 Authenticated |
| `/admin` | Admin panel root (redirects to dashboard) | 🔐 Admin only |
| `/admin/dashboard` | Overview stats, recent reservations, weekly sales | 🔐 Admin only |
| `/admin/products` | List, create, edit, delete spaces | 🔐 Admin only |
| `/admin/reservations` | Calendar and table view of all reservations | 🔐 Admin only |
| `/admin/payments` | Payment records and refund management | 🔐 Admin only |
| `/admin/analytics` | Detailed charts: revenue, bookings, top products | 🔐 Admin only |
| `/admin/notifications` | Real-time reservation notifications | 🔐 Admin only |

---

## 🗄️ Database Schema Overview

The database is managed through Supabase (PostgreSQL) with Row Level Security enabled.

**Core Tables:**

- **`profiles`** — Extended user data (name, role: `user` | `admin`, avatar URL)
- **`products`** — Space listings (name, description, price, capacity, images, available time slots)
- **`reservations`** — Booking records (user, product, date, time slot, status: `pending` | `confirmed` | `cancelled`)
- **`payments`** — Payment records linked to reservations (PortOne payment ID, amount, status)
- **`notifications`** — Real-time notification queue for admin alerts

---

## 💳 Payment Flow

This app uses **PortOne V2** (formerly I'mport) for secure Korean payment processing.

```
User selects timeslot
        ↓
Booking form submitted (Server Action)
        ↓
PortOne browser SDK opens payment modal
        ↓
Payment confirmed by PortOne
        ↓
Server-side verification via PortOne V2 API
        ↓
Reservation status updated to "confirmed"
        ↓
Admin receives real-time notification
```

To test payments in development, set `NEXT_PUBLIC_PAYMENT_ENV=development` and use PortOne's [test card numbers](https://developers.portone.io/docs/ko/v2-payment/test).

---

## 🔨 Available Scripts

```bash
# Start development server with hot-reloading
npm run dev

# Build for production
npm run build

# Start production server (run build first)
npm run start

# Run ESLint
npm run lint
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes:
   ```bash
   git commit -m "feat: add your feature description"
   ```
4. **Push** to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open** a Pull Request against the `main` branch

### Commit Message Convention

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

| Prefix | Use case |
|---|---|
| `feat:` | New feature |
| `fix:` | Bug fix |
| `docs:` | Documentation changes |
| `style:` | Code style / formatting |
| `refactor:` | Code refactoring |
| `chore:` | Build process / dependency updates |

---

## 📄 License

This project is licensed under the [MIT License](./LICENSE).

---

<div align="center">

Built with ❤️ using [Next.js](https://nextjs.org/) + [Supabase](https://supabase.com/) + [PortOne](https://portone.io/)

</div>
