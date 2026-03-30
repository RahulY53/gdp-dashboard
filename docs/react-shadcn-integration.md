# React/shadcn Integration Notes

This repository is currently a Python Streamlit app (`streamlit_app.py`) and does **not** yet include a React + TypeScript + Tailwind + shadcn/ui setup.

## What was added

- `components/ui/shader-background.tsx`
- `components/ui/demo.tsx`

These files match the requested `/components/ui` placement used by shadcn/ui projects.

## Why `/components/ui` matters

`/components/ui` is the standard default used by shadcn/ui generators and docs. Keeping UI primitives and reusable components in this path:

- aligns with shadcn CLI defaults,
- keeps import aliases predictable (`@/components/ui/...`),
- simplifies collaboration and future component installs.

## Suggested setup (from repo root)

1. Initialize a React app with TypeScript (example with Next.js):

```bash
npx create-next-app@latest web --typescript --tailwind --eslint --app --src-dir
```

2. Move into the React app and initialize shadcn/ui:

```bash
cd web
npx shadcn@latest init
```

3. During shadcn init, keep/choose defaults:

- Components: `components`
- Utilities: `lib/utils`
- CSS file: `app/globals.css` (App Router) or `src/index.css` (Vite)

4. Copy the new files into:

- `components/ui/shader-background.tsx`
- `components/ui/demo.tsx`

5. Ensure path alias supports `@/*` in `tsconfig.json`.

## Component integration checklist

- **Dependencies:** React only (WebGL API is browser-native).
- **Props/state:** No props currently; internal animation loop state only.
- **Providers/hooks:** No external provider needed.
- **Assets/icons:** No images, no icon package needed for this component.
- **Responsive behavior:** Canvas fills viewport (`fixed`, full width/height) and updates on resize.
- **Best placement:** Use once at root layout/page as a background layer behind app content.

## Questions to confirm before product use

- Should animation be optional based on user settings (e.g., reduced motion)?
- Should shader colors/speed be configurable via props?
- Should this render on all pages or only selected routes?
- Are there performance constraints for low-power devices?
