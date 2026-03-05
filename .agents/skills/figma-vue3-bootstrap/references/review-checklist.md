# Local Review Checklist

## A. Functional

1. Confirm all required sections/components from Figma node are present.
2. Confirm primary interactive states are implemented (default/hover/active/disabled).
3. Confirm no console errors in local preview.

## B. Visual

1. Compare screenshot against local page at equivalent viewport.
2. Verify typography: font size, line height, weight.
3. Verify spacing: margin, padding, gap, alignment.
4. Verify colors and border radius against tokens.

## C. Responsive

1. Validate desktop and mobile breakpoints.
2. Confirm no clipped text or overflow in narrow screens.

## D. Code Quality

1. Run `npm run lint` successfully.
2. Run `npm run build` successfully.
3. Confirm no unrelated file modifications in `git status`.

## E. PR Hygiene

1. Include implementation scope and constraints in PR description.
2. Include validation commands and outcomes.
3. Include intentional deviations from Figma (if any).
4. Post PR comment: `@codex review`.
