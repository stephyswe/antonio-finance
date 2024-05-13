### Pre-setup

`bunx replaces npx`

`sfc in empty page.tsx`

### Initial Setup

bunx create-next-app@latest antonio-finance-clone
```
√ Would you like to use TypeScript? ... Yes
√ Would you like to use ESLint? ... Yes
√ Would you like to use Tailwind CSS? ... Yes
√ Would you like to use `src/` directory? ... No
√ Would you like to use App Router? (recommended) ... Yes
√ Would you like to customize the default import alias (@/*)? ... No
```

`cd folder`

bunx shadcn-ui@latest init
```
√ Which style would you like to use? » Default
√ Which color would you like to use as base color? » Slate
√ Would you like to use CSS variables for colors? ... yes

bunx shadcn-ui@latest add button
```

### Authentication (Clerk)

```
bun add @clerk/nextjs@5.0.6
clerk.com - login - create app: "antonio-finance-clone" - "remove email option" - create application
copy API KEYS to .env.local
clerk.com - app - customization - branding - hide clerk branding
```

.env.local
```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
```

### Hono.js Setup

```
bun add hono@^4.3.2 @hono/zod-validator@^0.2.1 zod@^3.23.6
.
https://hono.dev/getting-started/vercel
https://hono.dev/guides/rpc
https://hono.dev/middleware/third-party
https://hono.dev/guides/best-practices
.
[clerk middleware for hono](https://github.com/honojs/middleware/tree/main/packages/clerk-auth)
bun add @hono/clerk-auth@^2.0.0 @clerk/backend@^1.1.1
```

.env.local
```
CLERK_PUBLISHABLE_KEY=
```

### Header component

```
bunx shadcn-ui@latest add sheet
bun add react-use@^17.5.0
``` 

### Neon & Drizzle

```
https://neon.tech 
- create antonio-finance-postgres - "create project"

https://orm.drizzle.team/docs/get-started-postgresql

bun add drizzle-orm@^0.30.10 @neondatabase/serverless@^0.9.3
bun add -D drizzle-kit@^0.21.1

https://orm.drizzle.team/docs/sql-schema-declaration

bun add -D dotenv@^16.4.5

https://neon.tech/docs/guides/drizzle-migrations#run-the-migration

bun run db:generate
bun run db:migrate
bun run db:studio

https://orm.drizzle.team/docs/rqb#find-first
or
https://orm.drizzle.team/docs/select#basic-and-partial-select
```

.env.local
```
DATABASE_URL=
```

### Deployment

foreach
```
git add .
git commit -m "XX: message"
git push
validate deployment succeed
```
once
```
github.com/new - create repo
use second option - "push an existing repo"
.
vercel.com/new - import - deploy
settings - environment variables - add from .env
```