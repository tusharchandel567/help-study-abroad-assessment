# Help Study Abroad - Admin Dashboard

A modern admin dashboard built with Next.js, MUI, Zustand, and NextAuth.
Uses DummyJSON public API for all backend data.

---

## Tech Stack

- **Next.js 14** - React framework with App Router
- **Material UI (MUI)** - UI components and responsive design
- **Zustand** - State management (chosen over Redux for simplicity,
  zero boilerplate, built-in async, tiny bundle size)
- **NextAuth** - Authentication and session management
- **Axios** - HTTP requests

---

## Features

- Admin login with NextAuth + DummyJSON auth API
- Protected dashboard routes (unauthenticated users redirected to login)
- Users list with search, pagination, and detail view
- Products list with search, category filter, pagination, and detail view
- Zustand state management with client-side caching
- Fully responsive UI with MUI components
- Performance optimized with React.memo, useCallback, useMemo

---

## Setup Instructions

### 1. Clone the repository

git clone https://github.com/tusharchandel567/help-study-abroad-assessment.git
cd help-study-abroad-assessment

### 2. Install dependencies

npm install

### 3. Create environment variables

Create a .env.local file in the root of the project:

NEXTAUTH_SECRET=mysecretkey123
NEXTAUTH_URL=http://localhost:3000

### 4. Run the development server

npm run dev

Open http://localhost:3000 in your browser.

---

## Login Credentials (DummyJSON Test Account)

Username: emilys
Password: emilyspass

---

## Folder Structure

src/
├── app/
│   ├── api/auth/[...nextauth]/route.ts   # NextAuth API route
│   ├── login/page.tsx                    # Login page
│   └── dashboard/
│       ├── layout.tsx                    # Protected layout
│       ├── page.tsx                      # Dashboard home
│       ├── users/
│       │   ├── page.tsx                  # Users list
│       │   └── [id]/page.tsx             # Single user
│       └── products/
│           ├── page.tsx                  # Products list
│           └── [id]/page.tsx             # Single product
├── components/
│   ├── Navbar.tsx
│   ├── Sidebar.tsx
│   ├── SessionWrapper.tsx
│   ├── users/UserTable.tsx
│   └── products/ProductCard.tsx
├── store/
│   ├── authStore.ts                      # Auth Zustand store
│   ├── usersStore.ts                     # Users Zustand store
│   └── productsStore.ts                  # Products Zustand store
└── lib/
    └── axios.ts                          # Axios instance

---

## Why Zustand?

- Zero boilerplate compared to Redux
- Built-in async actions (no need for thunk/saga)
- Tiny bundle size (~1kb)
- Simple API, easy to learn
- Perfect for small to medium apps

## Caching Strategy

- List results are cached in Zustand store using a key
  format of "limit_skip_query_category"
- On revisit of same page/filter, data is served from
  cache instead of making a new API call
- This reduces unnecessary network requests and
  improves performance