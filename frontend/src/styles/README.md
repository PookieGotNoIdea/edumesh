# Styles — Frontend

## 1. Folder Overview

The `styles/` folder contains global styling files used throughout the EduMesh frontend.

It establishes the visual foundation of the application and helps maintain a consistent user interface across different pages and feature modules.

EduMesh uses:

- Tailwind CSS for utility-based styling.
- Vanilla CSS for custom styling where required.

The purpose of this folder is to manage global styles and shared design rules.

Feature-specific styling should generally remain close to the components or feature modules that use it.

## 2. Planned Folder Structure

```text
styles/
│
├── README.md
│
├── index.css
├── global.css
├── variables.css
└── responsive.css
```

This is a proposed initial structure. Additional files may be introduced when required.

The actual structure should be coordinated with the Vite and Tailwind CSS setup.

## 3. Global Styling Files

### A. index.css

Purpose: Acts as the main stylesheet entry point.

Responsibilities:

- Import global stylesheets.
- Include the required Tailwind CSS directives or imports according to the installed Tailwind version.
- Establish the global styling foundation.

It should be imported through the frontend application entry point.

### B. global.css

Purpose: Contains global styles applied across the application.

Possible responsibilities:

- Basic page styling.
- Body and root element defaults.
- Default typography.
- Common element styling.
- Global spacing and layout defaults.

Avoid adding feature-specific styles here.

### C. variables.css

Purpose: Contains shared CSS custom properties.

Possible examples:

- Primary and secondary colours.
- Background colours.
- Text colours.
- Border colours.
- Spacing values.
- Border-radius values.
- Common shadow values.
- Typography settings.

Example:

```css
:root {
  --color-primary: #2563eb;
  --color-background: #ffffff;
  --color-text: #1f2937;
  --color-border: #e5e7eb;

  --radius-card: 12px;
}
```

These are illustrative values, not finalized EduMesh design decisions.

The final design tokens should follow the agreed visual design.

### D. responsive.css

Purpose: Contains shared responsive styling rules where required.

Possible responsibilities:

- Shared mobile layout adjustments.
- Responsive typography.
- Common breakpoint-specific styling.
- Global responsive behaviour.

Feature-specific responsive styling should remain near the relevant feature or component.

## 4. Tailwind CSS Usage

Tailwind CSS should be used for common utility-based styling.

Examples of its use include:

- Flexbox layouts.
- Grid layouts.
- Padding and margins.
- Typography.
- Background colours.
- Borders.
- Responsive visibility.
- Width and height.
- Alignment.

Tailwind CSS helps maintain consistent styling without writing separate CSS rules for every small layout adjustment.

The installed Tailwind version and its configuration must be followed during implementation.

## 5. Vanilla CSS Usage

Vanilla CSS should be used when custom styling is more appropriate than utility classes.

Possible use cases:

- Complex animations.
- Custom visual effects.
- Reusable CSS classes.
- Complex component-specific styling.
- Styling that becomes difficult to maintain through utility classes alone.

Avoid writing unnecessary custom CSS when an existing Tailwind utility provides a clear solution.

## 6. Global Design Consistency

EduMesh should maintain a consistent visual language across its pages.

Shared styling should help maintain consistency in:

- Colours.
- Typography.
- Spacing.
- Borders.
- Border radius.
- Shadows.
- Buttons.
- Form controls.
- Cards.
- Responsive behaviour.

Common visual elements should use shared design values wherever practical.

The final colour palette, typography and design tokens should be agreed during frontend UI development.

## 7. Responsive Design

The frontend should work across:

- Desktop screens.
- Laptop screens.
- Tablets.
- Mobile devices.

Expected behaviour:

- Layouts should adapt to different screen sizes.
- Content should remain readable.
- Navigation should adapt to smaller screens.
- Cards and grids should resize appropriately.
- Forms should remain usable.
- Horizontal overflow should be avoided unless intentionally required.

Tailwind responsive utilities and custom media queries may be used where appropriate.

## 8. Styling Separation

EduMesh should maintain a clear separation between global and feature-specific styles.

| Location | Responsibility |
|---|---|
| `src/styles/` | Global styles and shared design rules |
| `src/layouts/` | Overall page layout structure |
| `src/components/` | Shared component presentation |
| `src/features/` | Feature-specific presentation |

For example:

- Global typography belongs in shared styles.
- A shared button's presentation belongs with the shared component or its styling.
- Quiz-specific question styling belongs with the quizzes feature.
- Progress chart-specific styling belongs with the progress feature.

Avoid placing all application CSS inside one large global stylesheet.

## 9. Accessibility and Usability

Styling should support accessible and usable interfaces.

Expected practices:

- Maintain sufficient text contrast.
- Provide visible focus indicators.
- Avoid relying only on colour to communicate status.
- Keep interactive elements visually distinguishable.
- Ensure forms and controls remain readable.
- Support keyboard navigation.
- Avoid animations that unnecessarily interfere with usability.

## 10. Coding Conventions

- Use consistent CSS naming.
- Keep styles organized by responsibility.
- Use shared design variables where appropriate.
- Prefer Tailwind utilities for common styling.
- Use Vanilla CSS for justified custom requirements.
- Avoid duplicate style definitions.
- Avoid unnecessary `!important` declarations.
- Keep feature-specific styling out of global stylesheets.
- Ensure responsive behaviour is considered during implementation.

## 11. Testing Checklist

Before marking the styles folder complete, verify:

- [ ] Global styles load correctly.
- [ ] Tailwind CSS is configured correctly.
- [ ] Custom CSS loads correctly.
- [ ] Shared design variables are available.
- [ ] Typography remains consistent.
- [ ] Common colours and spacing are consistent.
- [ ] Responsive layouts work correctly.
- [ ] No unintended horizontal overflow occurs.
- [ ] Interactive elements have visible focus states.
- [ ] Feature-specific styling is kept separate.
- [ ] No unnecessary duplicate CSS rules exist.

## 12. Development Guidelines

During frontend development:

- Establish global styling before building many feature pages.
- Follow the agreed EduMesh visual design.
- Reuse shared design variables.
- Prefer Tailwind utilities for straightforward styling.
- Use Vanilla CSS when custom styling is necessary.
- Keep feature-specific CSS close to its relevant components.
- Test styles on different screen sizes.
- Avoid introducing unnecessary styling dependencies.

---

**Styles Folder Status:** Global styling responsibilities, Tailwind CSS and Vanilla CSS usage, design consistency, responsive behaviour and styling separation documented. Final design tokens, colour palette, typography and exact stylesheet configuration will be established during frontend implementation.
