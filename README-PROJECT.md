# Rumesh Prasanga — Portfolio

A clean, white, minimalistic portfolio for an AI developer / fullstack designer.
Built with **Next.js 16**, **TypeScript**, **Tailwind CSS 4**, **shadcn/ui**, **Prisma** (SQLite),
and **Framer Motion**.

## Quick Start

### 1. Install dependencies
```bash
npm install
# or
bun install
```

### 2. Set up the database
The project uses SQLite via Prisma. Create a `.env` file in the project root:

```env
DATABASE_URL="file:./db/custom.db"
```

Then push the schema and seed the sample projects:

```bash
npx prisma db push
npx prisma generate
node scripts/seed.js      # or: bun run scripts/seed.ts
```

> If you run the seed script with Node, compile it first or use `tsx`.
> With Bun you can run the `.ts` file directly: `bun run scripts/seed.ts`.

### 3. Run the dev server
```bash
npm run dev
# or
bun run dev
```

Open http://localhost:3000 in your browser.

---

## What's Included

- **Single-page portfolio** at `/` with 7 sections:
  Hero · About · Skills · Selected Work · Experience · Services · Contact
- **Working contact form** — saves messages to the SQLite database via `/api/contact`
- **Projects API** — `/api/projects` serves project cards from the database
- **Stats API** — `/api/stats` returns counts for the About section
- **Light / Dark theme** toggle (next-themes)
- **Fully responsive** with a mobile hamburger menu
- **AI-generated portrait + project images** in `public/images/`

## Tech Stack

| Layer       | Technology                                   |
|-------------|----------------------------------------------|
| Framework   | Next.js 16 (App Router)                      |
| Language    | TypeScript 5                                 |
| Styling     | Tailwind CSS 4 + shadcn/ui (New York)        |
| Fonts       | Sora (display) · Inter (body) · JetBrains Mono |
| Database    | Prisma ORM + SQLite                          |
| Animation   | Framer Motion                                |
| Forms       | React Hook Form + Zod                        |
| Icons       | Lucide React                                 |

## Project Structure

```
.
├── prisma/
│   └── schema.prisma          # ContactMessage + Project models
├── public/
│   └── images/                # Portrait + project thumbnails
├── scripts/
│   ├── seed.ts                # Seed 4 sample projects
│   ├── gen-images.ts          # AI image generation (z-ai SDK)
│   ├── process-portrait.ts    # Sharp image processing
│   └── soften-portrait-bg.ts  # Background replacement
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── contact/route.ts
│   │   │   ├── projects/route.ts
│   │   │   └── stats/route.ts
│   │   ├── globals.css
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── components/
│   │   ├── portfolio/         # All portfolio sections
│   │   ├── theme/             # Theme provider + toggle
│   │   └── ui/                # shadcn/ui components
│   ├── hooks/
│   └── lib/
│       ├── db.ts              # Prisma client
│       └── utils.ts
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── next.config.ts
```

## Customizing

- **Your details** (name, roles, bio, email, location) live in:
  `src/components/portfolio/hero.tsx`, `about.tsx`, `contact.tsx`, `footer.tsx`
- **Projects** are in the database — edit `scripts/seed.ts` and re-run it,
  or manage them via the Prisma Studio (`npx prisma studio`).
- **Experience & Services** are in `experience.tsx` and `services.tsx`.
- **Colors / theme** are in `src/app/globals.css` (CSS variables).
- **Your photo**: replace `public/images/portrait.jpg` with your own (4:5 ratio recommended).

## Build for Production

```bash
npm run build
npm run start
```

## Notes

- The `z-ai-web-dev-sdk` is used only in backend scripts (`scripts/`) for image generation.
  It is not required to run the site — only if you want to regenerate images.
- The contact form stores messages in SQLite. To view them, use Prisma Studio.

---

© Rumesh Prasanga. Designed & Built With Care.
