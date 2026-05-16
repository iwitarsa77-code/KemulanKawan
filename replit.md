# Kemulan Kawan

## Overview

Website informasi komunitas warga "Kemulan Kawan" — platform untuk kegiatan, program kerja, laporan donasi, dan pengumuman.

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (artifacts/kemulan-kawan)
- **API framework**: Express 5 (artifacts/api-server)
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod, drizzle-zod
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)
- **File uploads**: Multer + Object Storage (GCS)
- **Sessions**: express-session (admin auth, password: admin123)

## Key Pages

- `/` — Home: Rekap laporan donasi matrix (Juli 2025 – Juni 2027) + summary cards
- `/donasi` — Form input donasi publik (select donatur atau nama baru)
- `/pengumuman` — Daftar pengumuman
- `/program` — Daftar program kerja
- `/admin` — Panel admin (login password: admin123)

## Admin Features

- Kelola donatur (approve/reject/tambah)
- Kelola donasi (approve/reject, lihat bukti)
- Kelola pengumuman (CRUD)
- Kelola program kerja (CRUD)
- Upload logo website
- Upload gambar latar

## DB Schema

- `donors` — master donatur
- `donations` — data donasi per bulan per donatur
- `announcements` — pengumuman
- `programs` — program kerja
- `site_settings` — logo, background, admin password

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)

## Environment Variables

- `SESSION_SECRET` — Express session secret
- `DATABASE_URL` — PostgreSQL connection string
- `DEFAULT_OBJECT_STORAGE_BUCKET_ID` — GCS bucket for file uploads
- `PUBLIC_OBJECT_SEARCH_PATHS` — public object search paths
- `PRIVATE_OBJECT_DIR` — private object directory
