# AGENTS Guidelines for This Repository

This repository contains a StackOverflow Code Challenges located in the src folder of
this repository. When working on the project interactively with an agent (e.g. the Codex
CLI) please follow the guidelines below so that the development experience – in particular
Hot Module Replacement (HMR) – continues to work smoothly.

## 1. Use the Development Server, **not** `npm run build`

* **Always use `tox`** while iterating on the application.  This starts all the checks
  in development.
* **Do _not_ run `tox -e docs` inside the agent session.**  Running the production
  build command switches the `.next` folder to production assets which disables hot
  reload and can leave the development server in an inconsistent state.  If a
  production build is required, do it outside of the interactive agent workflow.

## 2. Keep Dependencies in Sync

If you add or update dependencies remember to:

1. Update the appropriate lockfile (`pylock.lock`).
2. Re-start the development server so that Next.js picks up the changes.

## 3. Coding Conventions

* Prefer TypeScript (`.tsx`/`.ts`) for new components and utilities.
* Co-locate component-specific styles in the same folder as the component when
  practical.

## 4. Useful Commands Recap

| Command            | Purpose                                             |
| ------------------ | --------------------------------------------------- |
| `tox`              | Run all tests and checks in the Python environment. |
| `tox -e lint`      | Run lint checks in the Python environment.          |
| `tox -e docs`      | Generate documentation (if configured).             |

---

Following these practices ensures that the agent-assisted development workflow stays
fast and dependable.  When in doubt, restart the dev server rather than running the
production build.