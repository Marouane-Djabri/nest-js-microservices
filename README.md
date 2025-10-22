# Monorepo workspace (Nx)

This repository contains multiple NestJS microservices. It has been organized as a lightweight Nx workspace so you can run and build the individual services from the repository root without moving files.

Included projects:

- `apigateway`
- `auth-service`
- `file-management-service`
- `users-service`

How to use

1. Install root-level dev tools (nx is used as a CLI wrapper):

```powershell
npm install -g nx@latest
npm install
```

2. Run a service via Nx (examples):

```powershell
npx nx run apigateway:start
npx nx run users-service:start:dev
npx nx run auth-service:build
```

Notes

- This workspace uses run-commands targets that call each service's own npm scripts (no files were moved).
- If you want a deeper Nx integration (workspace libs, caching across builds, generators), I can convert each service into proper Nx applications and hoist shared dependencies.

Publishing this example to GitHub

1. Create a new repository on GitHub (for example: `NSPE-insp/apigateway-example`).
2. Push the existing folder to the new repository from your local machine:

```powershell
git init
git add .
git commit -m "chore: init monorepo Nx example"
git branch -M main
git remote add origin https://github.com/<your-org-or-username>/<repo>.git
git push -u origin main
```

3. The included GitHub Actions workflow (`.github/workflows/ci.yml`) will run on push and PR to `main` and execute `npm run build:all` to build all microservices.

If you'd like, I can also:

- Create the GitHub repository for you (requires a GitHub token or authorization),
- Add more CI steps (lint, test, cache), or
- Convert this into a fully Nx-managed monorepo with hoisted devDependencies.

