# UNotes — Note Sharing for UMass Students

> Team project for COMPSCI 320 at UMass Amherst, built by a team of 10.
> Original repository: https://github.com/ahaan0502/COMPSCI-320

UNotes is a full-stack web app where UMass students share and find class notes. Students sign in with their UMass Google account, browse courses, post and save notes, and report content that breaks the rules. Admins review reports and moderate each class.

![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?logo=supabase&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?logo=tailwindcss&logoColor=white)

---

## Features

- **UMass-only sign-in** — Google OAuth through Supabase. Only `@umass.edu` accounts can sign in.
- **Course catalogue** — browse UMass departments and classes, imported from SPIRE.
- **Share notes** — post notes to a class, with tags and visibility settings.
- **Discovery** — filter by course or semester, or search by topic.
- **Saved notes and profiles** — save other students' notes and manage your own posts from your profile.
- **Reporting and moderation** — report posts (spam, harassment, inaccurate content, academic policy). Admins get a review queue where they can edit or delete posts, resolve or dismiss reports, and ban users from a course.

## Tech Stack

| Layer    | Tools                                                     |
|----------|-----------------------------------------------------------|
| Frontend | Next.js (App Router), React, TypeScript, Tailwind CSS     |
| Backend  | Node.js, Express                                          |
| Data and auth | Supabase (Postgres, Auth, Google OAuth)              |
| Testing  | Jest, React Testing Library, Playwright (end-to-end)      |

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or later (comes with npm)
- Git

### 1. Clone the repository

```bash
git clone https://github.com/Mahesh170505/COMPSCI-320.git
cd COMPSCI-320
```

### 2. Set up environment variables

```bash
cp frontend/.env.local.example frontend/.env.local
cp backend/.env.example backend/.env
```

Fill in the Supabase and API values in both files.

### 3. Install dependencies

```bash
cd frontend && npm install
cd ../backend && npm install
```

### 4. Run the app

Use two terminals:

```bash
# Terminal 1 – backend
cd backend && npm run dev
```

```bash
# Terminal 2 – frontend
cd frontend && npm run dev
```

Then open [http://localhost:3000](http://localhost:3000).

---

## Testing

```bash
cd frontend
npm test            # unit tests (Jest)
npm run test:e2e    # end-to-end tests (Playwright)
```

Some end-to-end tests need a signed-in session. Save one first, with the app running:

```bash
npx playwright codegen --save-storage=e2e/auth-state.json http://localhost:3000
```

---

## Project Structure

```
COMPSCI-320/
├── frontend/              # Next.js app
│   └── app/
│       ├── admin/         # Moderation dashboard and per-class admin pages
│       ├── auth/          # Google OAuth sign-in and callback
│       ├── catalogue/     # Department and course browsing
│       ├── classes/       # Class pages
│       ├── notes/         # Note feed and note detail pages
│       ├── profile/       # User profile and the user's own posts
│       ├── savednotes/    # Saved notes
│       ├── components/    # Shared UI components
│       └── lib/           # Supabase client and data helpers
├── backend/               # Express API server
└── scripts/               # Utilities (for example, importing UMass courses)
```

---

## My Contributions

I'm [Mahesh Ganesh](https://github.com/Mahesh170505), one of the ten team members. My main work:

- **Moderation system** — wrote `frontend/app/lib/moderation.ts`, which handles post reports, the admin review queue, editing and deleting posts, resolving reports, and course-level bans. Built the admin dashboard UI and the report and moderation components on top of it.
- **Profile page** — rewrote the profile page and added editing of a user's own notes. Edits are limited to the post's author.
- **UMass-only sign-in** — added the `@umass.edu` check to the Google OAuth callback, user records created on first login, and error redirects.

## Team

Built by Team 2 for COMPSCI 320 (Software Engineering), UMass Amherst. See the [original repository](https://github.com/ahaan0502/COMPSCI-320) and its [contributors](https://github.com/ahaan0502/COMPSCI-320/graphs/contributors).
