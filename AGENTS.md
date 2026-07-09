# AGENTS.md

## Cursor Cloud specific instructions

This repo is the **Tongsuo (铜锁) documentation website**, a static site built with [Docusaurus](https://docusaurus.io/) 3.x. There is a single service: the docs site itself.

### Commands (see `package.json` scripts)
- Dev server: `yarn start` (defaults to port 3000). Use `yarn start --host 0.0.0.0 --port 3000` when it must be reachable outside localhost. Supports hot reload.
- Build: `yarn build` (this is what CI runs; output goes to `build/`).
- Serve built output: `yarn serve`.
- Typecheck: `yarn typecheck` (runs `tsc`).

### Non-obvious notes
- Package manager is **yarn** (matches `yarn.lock` and CI). A stray `package-lock.json` also exists; ignore its yarn warning and do not mix npm.
- `yarn typecheck` currently FAILS on a pre-existing error in `src/components/OtherFeaturesView/components/Cards/index.tsx` (`preventDefaultTouchmoveEvent` prop from `react-swipeable`). This is unrelated to environment setup. CI does not run typecheck — only `yarn build`.
- `yarn build` succeeds but prints benign warnings (broken anchors, KaTeX/LaTeX "unicode in math mode", browserslist outdated). These do not fail the build.
- Content is bilingual (i18n `en` + default `zh`). Docs live in `docs/`, blog in `blog/`, custom React components in `src/`.
- Search (`@easyops-cn/docusaurus-search-local`) is only indexed in production builds. It does NOT work under `yarn start`; to test search, run `yarn build` then `yarn serve`.
