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
clerk.com - app - customization - branding - hide clerk branding - 
```

.env
```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_PUBLISHABLE_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
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