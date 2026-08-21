# UI Assets Collection

A public collection of reusable React and frontend UI snippets. The repository gathers animated components, backgrounds, interactive controls, form patterns, layout ideas, and complete sections that can be adapted into product interfaces and prototypes.

Each asset is a self-contained source snippet, stored primarily as `.txt` so it can be browsed and copied without prescribing a framework build setup. The standalone `interactive_hover_button_demo.html` file provides a runnable browser demo.

## Repository Structure

Assets are grouped by the UI problem they solve:

| Directory | Contents |
| --- | --- |
| `backgrounds/` | Decorative backgrounds, ambient effects, and visual treatments. |
| `buttons-and-controls/` | Buttons, toggles, selectors, and other direct manipulation controls. |
| `cards-and-content/` | Cards, previews, badges, and content presentation patterns. |
| `carousels/` | Carousel and marquee interactions. |
| `data-display/` | File, keyboard, terminal, map, and timeline visualizations. |
| `forms-and-inputs/` | Form flows, uploads, input fields, and validation interactions. |
| `heroes-and-sections/` | Hero treatments, pricing, landing sections, and page-level compositions. |
| `layout-and-navigation/` | Navigation, menus, docks, grids, and expandable layouts. |
| `loaders/` | Loading indicators and progress feedback. |
| `overlays-and-feedback/` | Modals, tooltips, previews, and glass effects. |
| `text-effects/` | Animated and styled text treatments. |

## Using an Asset

1. Find a snippet that fits your interface.
2. Copy its source into the relevant component in your project.
3. Install or replace any dependencies referenced by the snippet.
4. Adapt styles, labels, and accessibility behavior to your design system.

The snippets are reference implementations, not a published package. Review each one before using it in production, especially its dependencies, responsive behavior, and keyboard interaction.

### LLM-assisted integration

This repository includes the [`integrate-ui-assets` skill](.github/skills/integrate-ui-assets/SKILL.md) for coding agents that support Agent Skills. It guides an agent through inspecting the target project, extracting every part of a snippet, adapting it to the existing architecture and design system, and validating the result instead of copying the example blindly.

Ask the agent to integrate a named asset into a specific project or screen, for example:

> Use the `integrate-ui-assets` skill to add `backgrounds/meteor_effect.txt` to the dashboard header.

## Contributing

Contributions are welcome. Please keep additions focused, reusable, and easy to evaluate.

1. Fork the repository and create a descriptive branch.
2. Add the asset to the most appropriate directory, using a clear lowercase filename with underscores.
3. Keep the snippet self-contained and include required imports, dependencies, and setup notes near the source when they are not obvious.
4. Preserve accessible semantics and keyboard behavior for interactive components.
5. Do not include secrets, proprietary assets, generated build output, or unrelated formatting changes.
6. Open a pull request that explains the component, dependencies, and how it was tested.

When updating an existing asset, explain the behavior that changed and avoid breaking API assumptions unless the pull request calls that out explicitly.

## License

This project is released under the [MIT License](LICENSE).
