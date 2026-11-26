# Client source structure

Keep application code under `src/` and group files by responsibility:

- `app/` — app setup, providers, and routing
- `components/` — reusable UI components shared across the app
- `features/` — feature-specific components and logic, grouped by feature
- `hooks/` — reusable React hooks
- `layouts/` — page shells and shared layout components
- `pages/` — route-level screens
- `services/` — API clients and external service integrations
- `utils/` — small, reusable helper functions
- `constants/` — shared fixed values and configuration
- `assets/` — images, icons, and other imported static files

Keep a file close to the feature that owns it when it is not shared. Promote it to a shared folder only when multiple parts of the app use it. Use `.jsx` for React components and `.js` for plain JavaScript modules.
