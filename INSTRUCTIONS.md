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

### Accounts GET API

https://tanstack.com/query/latest/docs/framework/react/installation
https://hono.dev/guides/rpc#using-rpc-with-larger-applications

```
bun add @tanstack/react-query@^5.35.1

https://tanstack.com/query/latest/docs/framework/react/guides/advanced-ssr#advanced-server-rendering

http://localhost:3000/api/accounts
```

.env.local
```
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### Accounts POST API

```
bun add drizzle-zod@^0.5.1 @paralleldrive/cuid2@^2.2.2 zustand@^4.5.2
bunx shadcn-ui@latest add form input sonner
```

### Datatable component

```
bun add @tanstack/react-table@^8.16.0
bunx shadcn-ui@latest add card table checkbox

https://ui.shadcn.com/docs/components/data-table#column-definitions
https://ui.shadcn.com/docs/components/data-table#pagination
https://ui.shadcn.com/docs/components/data-table#sorting
https://ui.shadcn.com/docs/components/data-table#filtering
https://ui.shadcn.com/docs/components/data-table#row-selection
```

### Accounts bulk delete

```
https://github.com/honojs/hono/releases/tag/v4.3.0

bunx shadcn-ui@latest add skeleton

https://medium.com/@kch062522/useconfirm-a-custom-react-hook-to-prompt-confirmation-before-action-f4cb746ebd4e
```

### Accounts edit

```
http://localhost:3000/api/accounts - get one id
http://localhost:3000/api/accounts/:id

bunx shadcn-ui@latest add dropdown-menu

commit: get with id

commit: patch with edit

commit: delete with id
```

### Categories (API + UI)

```
bun run db:generate
bun run db:migrate
bun run db:studio
```

### Transactions API

```
https://orm.drizzle.team/docs/rqb#one-to-many

bun run db:generate
bun run db:migrate
bun run db:studio

bun add date-fns@^3.6.0

https://orm.drizzle.team/docs/delete#with-delete-clause
```

### Transactions Hooks

...

### Transactions Forms

```
commit: add features w/i form

bun add react-select@^5.8.0

commit: form with types

commit: create re-usable select

commit: select account & category in form

bunx shadcn-ui@latest add calendar popover

commit: create re-usable datepicker

commit: payee & datepicker in form

bunx shadcn-ui@latest add textarea

commit: textarea in form

bun add react-currency-input-field@^3.8.0
bunx shadcn-ui@latest add tooltip

commit: create re-usable amount input

fix: categoryId & z.string()

commit: onSubmit & amount converter
```

### Transactions Page

```
fix: transactions not showing - api

commit: api methods

fix: remove log in transaction-form / features

bunx shadcn-ui@latest add badge

commit: add badge + date column formatter

fix: accounts renamed acount

commit: muliunits in transactions getAll api

commit: add amount in transactions column

commit: add account in transactions column

commit: invalidateQuery "transactions" in account

commit: add category in transactions column + invalidateQueries

commit: enable edit and delete accounts + handle unassigned category

commit: filter "payee" on transaction page
```

### Transactions CSV import

```
bun add react-papaparse@^4.4.0

commit: upload-button (import) & import rendering skeleton

commit: import card

commit: import-table: render body

bunx shadcn-ui@latest add select

commit: add shadcn ui select

commit: add table-head-select skeleton in import-table

commit: table-head-select functionality in import card

commit: design fix

commit: handleContinue with reduce null values
```

### Transactions account select

...

### Summary API

```
commit: update csv to current month

commit: summary api

commit: fix - summary.ts lastPeriod variable
```

### Dashboard cards

```
clerk: dashboard - click user - copy userId
edit scripts/seed.ts - line 12: SEED_USER_ID
package.json - "db:seed": "bun ./scripts/seed.ts"

bun run db:seed
bun run dev

commit: seed script

bun add react-icons@^5.2.1

commit: data grid + data-card skeleton & use-get-summary, react-icons

commit: add data-card
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