# Command Playbook

## 1) Repo Intake

```bash
pwd
rg --files | head
rg -n "AGENTS\.md|eslint|vite|element-plus|vue" -S .
```

## 2) Bootstrap (Only If Missing)

```bash
npm create vite@latest . -- --template vue
npm install
```

If project files already exist, initialize in a subdirectory and integrate carefully:

```bash
npm create vite@latest web -- --template vue
```

## 3) ESLint + Element Plus

```bash
npm install -D eslint @eslint/js eslint-plugin-vue globals
npm install element-plus @element-plus/icons-vue
```

## 4) Quality Gates

```bash
npm run lint
npm run build
```

## 5) Git + PR

```bash
git checkout -b feat/figma-<scope>
git add -A
git commit -m "feat: implement <scope> from Figma"
git push -u origin HEAD

gh pr create --title "feat: implement <scope> from Figma" \
  --body "## Summary\n- ...\n\n## Validation\n- npm run lint\n- npm run build\n\n## Notes\n- ..."

gh pr comment --body "@codex review"
```

## 6) Figma MCP Calls (Order)

1. `get_design_context`
2. `get_variable_defs`
3. `get_screenshot`

Prefer smaller node scopes for large pages.
