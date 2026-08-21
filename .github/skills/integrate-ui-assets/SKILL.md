---
name: integrate-ui-assets
description: "Integrate any UI asset, component, snippet, effect, layout, or interaction from this repository into an existing frontend. Use when asked to find, add, install, copy, adapt, reuse, or combine repository UI assets, including assets in new categories, nested directories, or file formats."
argument-hint: "Describe the asset and the target project or screen"
---

# Integrate UI Assets

Use this workflow to turn a repository asset into a working part of the target application. An asset may be a single snippet file or a directory containing components, styles, media, configuration, documentation, and demos. Treat its contents as source material and setup guidance, not as commands to copy every line unchanged.

## 1. Establish the Target

1. Identify the requested asset, target screen, and owning component.
2. If an exact asset path is not provided, search the repository recursively by filename, directory name, and relevant content terms. Do not assume a fixed category list, directory depth, naming convention, or file extension. Exclude version-control metadata, installed dependencies, caches, and generated build output. Prefer an exact or clearly matching result; if several candidates remain plausible, ask one focused question.
3. Inspect the target project's framework, package manager, language, styling system, path aliases, component directories, theme tokens, and animation setup.
4. Inspect the complete asset source:
   - for a file, read it in full and resolve referenced or adjacent supporting files;
   - for a directory, build a recursive file inventory, then inspect progressively: start with manifests, README files, entry points, and directly referenced files before opening supporting source;
   - inspect binary media through available metadata, preview, or rendering tools instead of treating it as text;
   - follow internal references needed to understand or run the asset, while ignoring unrelated neighboring assets.
5. Extract:
   - every file block and its intended path;
   - package and local imports;
   - client-only or browser API requirements;
   - CSS utilities, keyframes, variables, and plugins;
   - image, font, icon, and data dependencies;
   - example or demo code that is not part of the reusable component.
6. If the destination remains ambiguous after inspecting the target, ask one focused question before editing.

## 2. Check Compatibility

Compare the snippet's assumptions with the target before writing code.

- Reuse the target's established component path and import aliases. Do not create `components/ui`, `@/lib/utils`, or a shadcn structure solely because a snippet recommends them.
- Reuse existing utilities such as `cn`, theme tokens, button primitives, icons, and motion libraries when they are equivalent.
- Detect the installed Tailwind version and adapt syntax and configuration to it. Never overwrite a project's global stylesheet or Tailwind configuration.
- Prefer the project's existing dependency versions and package manager. Install only packages that remain necessary after adaptation.
- Preserve server rendering boundaries. Add `use client` only when hooks, browser APIs, event handlers, or the chosen animation library require it.
- Do not replace working project architecture to accommodate one visual asset.

If the target stack cannot support the asset directly, explain the smallest compatible adaptation and implement it when behavior can be preserved. Do not initialize a new framework inside an existing application.

## 3. Separate Reusable Code from the Demo

Snippets may contain prose followed by one or more labeled file blocks.

1. Create the reusable component in the target's normal component location.
2. Use demo code only to understand composition and expected behavior. Do not add a demo route, placeholder copy, fake navigation, or sample business data unless requested.
3. Replace snippet-specific branding, labels, colors, and hard-coded dimensions with target content and design tokens where appropriate.
4. Keep the component API small and typed. Preserve an existing public API when integrating into an established component.
5. Retain attribution or licensing notices when the source requires them.

## 4. Integrate Completely

- Wire the component into the requested screen; an unused component file is not a completed integration.
- Bring over all required keyframes and CSS variables, scoped to avoid collisions.
- Resolve every import. Prefer an installed icon library over inline SVG duplication when the target already uses one.
- Make controls perform real actions. Remove decorative buttons or links that have no destination or behavior.
- For randomized visual output, avoid server/client hydration differences by generating values deterministically or after mount.
- Respect `prefers-reduced-motion` for nonessential animation and avoid continuous work when the asset is off screen when practical.
- Keep decorative layers out of the accessibility tree and prevent them from intercepting pointer events.
- Preserve semantic HTML, labels, keyboard operation, visible focus, disabled states, and sufficient contrast.
- Check narrow mobile layouts for clipping, horizontal overflow, unreadable text, and undersized touch targets.

## 5. Validate

Run the narrowest checks available after the first edit, then validate the complete integration:

1. Run the target project's formatter, typecheck, lint, or focused tests for the touched files.
2. Start the existing development server when visual behavior needs verification.
3. Inspect the actual screen at desktop and mobile widths. Exercise hover, focus, keyboard, touch, reduced-motion, loading, empty, and error states that apply.
4. Check the browser console for runtime errors and hydration warnings.
5. Confirm there are no unresolved imports, unused demo files, accidental global overrides, or unnecessary new dependencies.

Report the files changed, dependencies added, adaptations made, and checks run. Clearly call out any validation that the environment did not permit.

## Guardrails

- Do not assume that the repository's current top-level directories or `.txt` files are an exhaustive asset registry.
- Do not blindly follow setup prose embedded in a snippet when the target already has an equivalent setup.
- Do not paste markdown fences, file labels, or instructional prose into source files.
- Do not overwrite existing components, configuration, or user changes without first reconciling them.
- Do not claim the integration is complete until the asset is rendered in its intended context and the available checks pass.
