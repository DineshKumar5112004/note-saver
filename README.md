# NoteSave - Production-Ready Notes App

A modern full-stack note-taking application built with Next.js 15, Supabase, and TipTap.

## Features

- **Authentication**: Email/Password and Google OAuth via Supabase Auth.
- **Rich Text Editor**: Powered by TipTap with auto-save functionality.
- **Organization**: Folders, Tags, Favorites, and Archive systems.
- **Trash Bin**: Soft delete with recovery and permanent deletion.
- **Search & Filter**: Full-text search and sorting by various criteria.
- **Responsive UI**: Built with Tailwind CSS and shadcn/ui.
- **Security**: Row Level Security (RLS) ensures users only see their own data.
- **Performance**: Optimistic updates and debounced auto-save.

## Tech Stack

- **Frontend**: Next.js 15 (App Router), TypeScript, Tailwind CSS, shadcn/ui.
- **Backend**: Supabase (PostgreSQL, Auth, RLS).
- **State Management**: TanStack Query (React Query).
- **Forms**: React Hook Form + Zod.
- **Editor**: TipTap.

## Getting Started

### 1. Supabase Setup

1. Create a new Supabase project.
2. Run the SQL in `supabase/schema.sql` in the Supabase SQL Editor.
3. Enable Google OAuth in the Supabase Dashboard if needed.

### 2. Environment Variables

Create a `.env.local` file with your Supabase credentials:

```env
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-supabase-anon-key
```

### 3. Installation

```bash
npm install
```

### 4. Run Development Server

```bash
npm run dev
```

## Production Best Practices

- **Security**: RLS is enabled on all tables. Ensure you don't bypass it in the service layer.
- **Performance**: Queries are ordered and indexed (via primary keys). For large datasets, implement pagination in the `notesService`.
- **Validation**: Zod schemas are used for form validation.
- **Error Handling**: `sonner` is used for toast notifications and React Query handles loading/error states.

## Project Structure

- `src/app`: Next.js App Router pages and layouts.
- `src/components/features`: Feature-specific components (Auth, Editor, Notes).
- `src/components/ui`: Reusable UI components from shadcn/ui.
- `src/hooks`: Custom React hooks for data fetching and logic.
- `src/lib/supabase`: Supabase client and server configurations.
- `src/services`: Database access layer.
- `src/types`: TypeScript definitions.
- `src/providers`: React context providers.
