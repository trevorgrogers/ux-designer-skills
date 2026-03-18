---
name: figma-best-practices
description: Figma best practices at scale — file organization, component architecture, design tokens/variables, dev handoff, branching, libraries, and performance. Use when advising on Figma workflow, structuring design systems in Figma, optimizing files, or preparing designs for developer handoff.
---

# Figma Best Practices at Scale

## When to Use This Skill

**Use when you need:**
- Figma file, project, or team organization guidance
- Component architecture decisions (variants vs. properties, atomic design)
- Design token/variable structure and naming conventions
- Developer handoff optimization (Dev Mode, annotations, Code Connect)
- Branching and version control workflows
- Multi-library architecture and governance
- File performance diagnosis and optimization

---

## 1. File Organization at Scale

### Team Structure

Mirror your product org structure in Figma. For teams with 50+ designers:

```
Organization
├── Team: Platform — Web
│   ├── Project: Authentication
│   ├── Project: Dashboard
│   └── Project: Settings
├── Team: Platform — iOS
│   ├── Project: Authentication
│   └── Project: Core Experience
├── Team: Platform — Android
├── Team: Design System
│   ├── Project: Foundations Library
│   ├── Project: Components Library
│   └── Project: Documentation
├── Team: Brand
│   ├── Project: Marketing Pages
│   └── Project: Brand Assets
└── Team: Research
    ├── Project: User Testing
    └── Project: Prototypes
```

**Key principles:**
- Align team names to business nomenclature (abbreviate as needed: "Product Landing Page" becomes "PLP")
- Use project-level permissions for access control (e.g., developers only see "Ready for Dev" projects)
- Create separate projects for workflow stages: `Explorations`, `In Progress`, `In Development`, `Shipped`
- Alternatively, organize projects by feature area or user flow

### File Naming Conventions

**Format:** `[Quarter] [Feature/Area] — [Description]`

Examples:
```
Q1 Onboarding — New User Flow
Q2 Checkout — Payment Redesign
Q4 Dashboard — Analytics Cards
```

**Rules:**
- Lead with fiscal quarter + year for chronological sorting
- Avoid internal nicknames — use names from your ticketing system or test plan
- Separate words with spaces (Figma search requires it)
- Keep file names under 40-48 characters (preview truncation limit)
- Use ticket IDs when aligned with project management: `TWIG-812 — Form Fields A/B Test`
- Append purpose suffixes: `— Research`, `— Prototype`, `— Specs`

**Research file naming:**
```
Account — Onboarding              (main design file)
Account — Onboarding — Research   (research companion)
Account — Onboarding — Prototype  (interactive prototype)
```

### Page Structure Within Files

Every file should follow a consistent page structure:

```
📄 Cover                    ← Thumbnail + metadata (always first page)
📄 —————————————           ← Divider (prefix page name with -)
📄 🎯 Current Sprint
📄 📐 Wireframes
📄 🎨 Visual Design
📄 ✅ Ready for Dev
📄 —————————————
📄 🧪 Explorations
📄 📦 Archive
📄 🧩 Local Components
```

**Cover page requirements:**
- Create as a component for reuse across files
- Include: project name, status (Draft / In Review / Ready for Dev / Shipped), designer name + Slack handle, creation date, last updated date
- Place links to related documents (PRD, Jira epic, research doc) near the thumbnail
- Set the cover frame as the file thumbnail

**Page naming rules:**
- Use emoji prefixes consistently across all files in the org
- Type `-` at the beginning of a page name to create a visual divider
- Use "Named Versions" (via version history) to mark significant milestones

### Layer Naming Conventions

**General rules:**
- Never leave default names (`Rectangle 1`, `Frame 47`, `Group 3`)
- Choose one casing convention and enforce it org-wide:
  - `PascalCase` for components: `PrimaryButton`, `NavigationBar`
  - `camelCase` for component props: `hasIcon`, `isDisabled`
  - `kebab-case` for layers: `hero-section`, `card-container`
  - `Title Case` for page names and sections
- Keep names concise but descriptive
- Avoid abbreviations unless universally understood

**Layer naming examples:**
```
Frame: page-header
  Frame: nav-container
    Component: Logo
    Frame: nav-links
      Component: NavItem
      Component: NavItem
    Component: UserAvatar
  Frame: hero-section
    Text: hero-title
    Text: hero-subtitle
    Component: PrimaryButton
```

**Special prefixes:**
- `_` prefix: Internal/private components that should NOT publish to library (`_SlotArea`, `_HelperGrid`)
- `.` prefix: Also hides from published library in some workflows

**Figma AI rename:** Figma now offers AI-powered layer renaming (Plugins > Rename layers with AI) for bulk cleanup of unnamed layers.

---

## 2. Component Architecture

### Atomic Design in Figma

Organize components following the atomic design hierarchy:

```
Atoms (smallest indivisible elements)
├── Icons
├── Colors (as color styles/variables)
├── Typography (text styles)
├── Spacing (variables)
├── Borders & Shadows
├── Input Field (single)
├── Button (single)
├── Checkbox
├── Radio
├── Avatar
├── Badge
└── Divider

Molecules (groups of atoms forming a functional unit)
├── Search Bar (icon + input + button)
├── Form Field (label + input + helper text)
├── List Item (avatar + text + action)
├── Breadcrumb (text + separator + text)
├── Tooltip (trigger + popover)
└── Tab (icon + label + indicator)

Organisms (complex UI sections composed of molecules)
├── Navigation Bar (logo + nav items + user avatar)
├── Card (image + text + actions)
├── Data Table (header row + data rows + pagination)
├── Modal (header + body + footer)
├── Sidebar (navigation + sections)
└── Form (multiple form fields + actions)

Templates (page-level layouts composed of organisms)
├── Dashboard Layout
├── Settings Page Layout
├── Product Detail Layout
└── Auth Flow Layout

Pages (specific instances of templates with real content)
├── Home Dashboard — Populated
├── User Settings — Populated
└── Product Page — Populated
```

**Implementation in Figma:**
- Each atomic level can be its own page within a library file, or its own file in a multi-file architecture
- Atoms reference only variables/tokens
- Molecules reference atoms via instances
- Organisms reference molecules and atoms
- Never skip levels (an organism should not directly contain raw rectangles)

### Component Properties vs. Variants: Decision Framework

| Use Case | Use Properties | Use Variants |
|----------|---------------|-------------|
| Toggle element visibility (show/hide icon) | Boolean property | -- |
| Change text content | Text property | -- |
| Swap nested component (icon swap) | Instance swap property | -- |
| Fundamentally different visual states | -- | Variant |
| Different sizes (sm/md/lg) | -- | Variant |
| Different types (primary/secondary/ghost) | -- | Variant |
| Interactive states (default/hover/active/disabled) | -- | Variant |
| Simple on/off appearance change | Boolean property | -- |
| Multiple structural layout differences | -- | Variant |

**When to use Component Properties (reduce variant count):**
- **Boolean property:** Toggle visibility of optional elements (chevron, icon, close button, badge). Replaces variants like "Button - with icon" / "Button - without icon" with a single `hasIcon` toggle.
- **Text property:** Allow text customization from the properties panel without double-clicking into the component. Use for labels, placeholder text, helper text.
- **Instance swap property:** Allow swapping of nested instances (icon sets, avatar types). Specify which nested instances can be swapped without creating parent variants for each option.

**When to use Variants:**
- Size changes that alter internal layout and spacing
- Type/style changes that alter color schemes and visual weight
- Interactive states that need prototype connections (hover, pressed, focused)
- Structural differences where elements are rearranged, not just shown/hidden

**Reduction example:**
A button with 3 types x 4 states x 2 sizes x with/without icon:
- Pure variants: 3 x 4 x 2 x 2 = 48 variants
- With properties: 3 x 4 x 2 = 24 variants + 1 boolean (hasIcon) = 24 variants

### Auto Layout Best Practices

**Core principle:** Auto layout controls how frames respond to content changes. Constraints control how objects respond to frame size changes.

**When to use Auto Layout:**
- Components that resize based on content (buttons, tags, cards)
- Lists, rows, grids of items
- Any repeating pattern
- Navigation bars, toolbars
- Form layouts
- Nearly everything — auto layout should be your default

**When to use Constraints:**
- Pinning elements to edges of a viewport-sized frame
- Anchoring a FAB to the bottom-right corner
- Header pinned to top while body scrolls
- Elements that must maintain position relative to parent edges, not siblings

**When to combine both:**
- Header: constrained to top/left-right of screen frame, internal elements use auto layout
- Modal: constrained to center, internal layout uses auto layout
- Sidebar: constrained to left/top-bottom, menu items use auto layout

**Auto layout rules:**
1. Always use auto layout for components (required for Dev Mode to generate clean CSS)
2. Name auto layout frames semantically: `card-content`, `button-row`, `nav-items`
3. Use `fill container` for responsive elements, `hug contents` for intrinsic sizing
4. Prefer `gap` over padding tricks for spacing between children
5. Use `absolute position` sparingly — only for overlapping elements like badges on avatars
6. Nest auto layout frames for complex layouts (horizontal inside vertical)
7. Set `min-width` / `max-width` for responsive behavior

### Component Naming and Organization

**Slash-separated hierarchy for component grouping:**
```
Button/Primary
Button/Secondary
Button/Ghost
Button/Destructive
Icon/Navigation/Arrow-Left
Icon/Navigation/Arrow-Right
Icon/Action/Edit
Icon/Action/Delete
Card/Product
Card/User
Card/Stat
```

**Variant property naming:**
```
Component: Button
├── Property: Type = Primary | Secondary | Ghost | Destructive
├── Property: Size = Small | Medium | Large
├── Property: State = Default | Hover | Active | Focus | Disabled
├── Property: hasIcon = true | false (boolean)
├── Property: iconPosition = Left | Right (variant or text)
└── Property: label = "Button" (text property)
```

**Naming alignment with code:**
- Match component names to code component names: Figma `Button/Primary` = code `<Button variant="primary">`
- Match property names to prop names: Figma `hasIcon` = code `hasIcon={true}`
- Match variant values to enum values: Figma `Size = Small` = code `size="small"`

---

## 3. Design Tokens and Variables

### Figma Variables: Structure and Organization

#### Collections and Their Purpose

```
Collection: Primitives
├── Mode: Value (single mode — raw values only)
├── Colors: red-50, red-100, ..., red-900, blue-50, ..., neutral-0, ..., neutral-1000
├── Spacing: 0, 1, 2, 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96
├── Radius: 0, 2, 4, 8, 12, 16, 9999 (full)
├── Font Size: 10, 12, 14, 16, 18, 20, 24, 28, 32, 40, 48, 64
└── Font Weight: 400, 500, 600, 700

Collection: Semantic
├── Mode: Light | Dark
├── bg/surface: neutral-0 (light) / neutral-900 (dark)
├── bg/surface-raised: neutral-50 / neutral-800
├── bg/surface-overlay: neutral-100 / neutral-700
├── bg/brand: blue-500 / blue-400
├── bg/success: green-50 / green-900
├── bg/warning: yellow-50 / yellow-900
├── bg/error: red-50 / red-900
├── text/primary: neutral-900 / neutral-50
├── text/secondary: neutral-600 / neutral-400
├── text/disabled: neutral-400 / neutral-600
├── text/inverse: neutral-0 / neutral-900
├── text/brand: blue-600 / blue-300
├── border/default: neutral-200 / neutral-700
├── border/strong: neutral-400 / neutral-500
├── border/brand: blue-500 / blue-400
├── border/error: red-500 / red-400
├── icon/primary: neutral-700 / neutral-300
├── icon/secondary: neutral-500 / neutral-500
└── icon/brand: blue-500 / blue-400

Collection: Component (optional, for complex systems)
├── Mode: Light | Dark (inherited from semantic)
├── button/bg-primary: bg/brand
├── button/bg-primary-hover: blue-600 / blue-300
├── button/text-primary: text/inverse
├── button/border-primary: transparent
├── input/bg: bg/surface
├── input/border: border/default
├── input/border-focus: border/brand
└── input/text: text/primary

Collection: Breakpoints (for responsive spacing/typography)
├── Mode: Mobile | Tablet | Desktop
├── container/max-width: 100% | 768px | 1280px
├── grid/columns: 4 | 8 | 12
├── grid/gutter: 16 | 24 | 32
├── heading/size-1: 28 | 36 | 48
├── heading/size-2: 24 | 28 | 36
└── body/size: 14 | 16 | 16
```

#### Variable Naming Conventions

**Naming pattern:** `category/subcategory/variant`

```
Color tokens:
  bg/surface
  bg/surface-raised
  bg/brand
  text/primary
  text/secondary
  text/on-brand
  border/default
  border/focus
  icon/primary

Spacing tokens:
  space/xs     → 4
  space/sm     → 8
  space/md     → 16
  space/lg     → 24
  space/xl     → 32
  space/2xl    → 48
  space/3xl    → 64

Radius tokens:
  radius/none  → 0
  radius/sm    → 4
  radius/md    → 8
  radius/lg    → 12
  radius/xl    → 16
  radius/full  → 9999

Shadow tokens (still use styles, not variables — Figma variables don't support shadows yet):
  shadow/sm
  shadow/md
  shadow/lg
  shadow/xl
```

**Rules:**
- Use `/` to create groups in the variables panel
- Name for purpose, not appearance: `bg/brand` not `bg/blue`
- Use lowercase with hyphens within segments
- Keep names concise but unambiguous
- Primitives can use value-based names (`blue-500`), semantics must use purpose-based names (`text/primary`)

#### Variable Aliasing (Referencing)

Variables can reference other variables of the same type. This is how the three-tier system works:

```
Primitive:    blue-500 = #3B82F6
                ↓ (referenced by)
Semantic:     bg/brand = blue-500
                ↓ (referenced by)
Component:    button/bg-primary = bg/brand
```

- Primitives should never be applied directly to designs — always go through semantic tokens
- Semantic tokens reference primitives and are what designers apply to layers
- Component tokens (optional) reference semantic tokens for per-component overrides

#### Styles vs. Variables

| Feature | Styles | Variables |
|---------|--------|-----------|
| Colors | Yes (being replaced) | Yes (preferred) |
| Typography | Yes (still primary) | Partial (font size, weight only) |
| Effects/Shadows | Yes (only option) | No |
| Spacing/Padding | No | Yes (preferred) |
| Border radius | No | Yes (preferred) |
| Multiple modes (light/dark) | No (duplicate styles) | Yes (native mode switching) |
| Responsive values | No | Yes (via breakpoint modes) |
| Aliasing/referencing | No | Yes |
| Boolean values | No | Yes |
| String values | No | Yes |

**Recommendation:** Use variables for everything they support (colors, spacing, radius, sizing, booleans). Use styles for typography (composite property) and effects/shadows (not yet supported by variables).

### Mapping Figma Variables to CSS/Tailwind

#### Direct CSS Custom Properties Mapping

```css
/* Primitives (generated from Figma Primitives collection) */
:root {
  --color-blue-50: #eff6ff;
  --color-blue-500: #3b82f6;
  --color-blue-600: #2563eb;
  --color-neutral-0: #ffffff;
  --color-neutral-50: #f8fafc;
  --color-neutral-900: #0f172a;
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-4: 1rem;
  --radius-sm: 0.25rem;
  --radius-md: 0.5rem;
}

/* Semantic (generated from Figma Semantic collection, Light mode) */
:root {
  --bg-surface: var(--color-neutral-0);
  --bg-brand: var(--color-blue-500);
  --text-primary: var(--color-neutral-900);
  --text-secondary: var(--color-neutral-600);
  --border-default: var(--color-neutral-200);
}

/* Dark mode override */
[data-theme="dark"] {
  --bg-surface: var(--color-neutral-900);
  --bg-brand: var(--color-blue-400);
  --text-primary: var(--color-neutral-50);
  --text-secondary: var(--color-neutral-400);
  --border-default: var(--color-neutral-700);
}
```

#### Tailwind Configuration Mapping

```js
// tailwind.config.js
module.exports = {
  theme: {
    colors: {
      surface: 'var(--bg-surface)',
      'surface-raised': 'var(--bg-surface-raised)',
      brand: 'var(--bg-brand)',
      primary: 'var(--text-primary)',
      secondary: 'var(--text-secondary)',
    },
    spacing: {
      xs: 'var(--space-xs)',
      sm: 'var(--space-sm)',
      md: 'var(--space-md)',
      lg: 'var(--space-lg)',
      xl: 'var(--space-xl)',
    },
    borderRadius: {
      sm: 'var(--radius-sm)',
      md: 'var(--radius-md)',
      lg: 'var(--radius-lg)',
      full: 'var(--radius-full)',
    },
  },
}
```

### Token Pipeline: Figma to Code

#### Option A: Tokens Studio + Style Dictionary

```
Figma Variables
    ↓ (Tokens Studio plugin)
JSON tokens in Git repo
    ↓ (Style Dictionary build)
CSS custom properties / Tailwind config / iOS / Android
```

**Setup:**
1. Install Tokens Studio plugin in Figma
2. Configure Git sync (GitHub, GitLab, Bitbucket, or Azure DevOps)
3. Map Figma variables to token JSON structure
4. Push tokens to repo — each Token Set becomes an individual JSON file
5. Style Dictionary transforms JSON into platform-specific outputs
6. CI/CD pipeline auto-builds on token changes

**Tokens Studio features:**
- Real-time change detection between Figma and Git
- Push/pull sync indicators
- Branch creation and switching within the plugin (Pro)
- Supports properties Figma variables don't yet (borderRadius, spacing, etc.)

#### Option B: Figma Variables API + Custom Pipeline

```
Figma Variables
    ↓ (Figma REST API / Variables API)
JSON export
    ↓ (Custom transform script or Style Dictionary)
CSS / Tailwind / Swift / Kotlin
```

#### Option C: Direct Export Plugins

- **Tokens to Tailwind CSS** plugin: Direct export from Figma variables to `tailwind.config.js` values
- **Tailwind Tokens** plugin: Creates Tailwind CSS variables and styles from Figma

#### Style Dictionary Configuration Example

```json
{
  "source": ["tokens/**/*.json"],
  "platforms": {
    "css": {
      "transformGroup": "css",
      "buildPath": "build/css/",
      "files": [{
        "destination": "variables.css",
        "format": "css/variables"
      }]
    },
    "tailwind": {
      "transformGroup": "js",
      "buildPath": "build/tailwind/",
      "files": [{
        "destination": "tokens.js",
        "format": "javascript/module"
      }]
    },
    "ios-swift": {
      "transformGroup": "ios-swift",
      "buildPath": "build/ios/",
      "files": [{
        "destination": "StyleDictionary.swift",
        "format": "ios-swift/class.swift"
      }]
    }
  }
}
```

---

## 4. Developer Handoff

### Dev Mode Best Practices

#### Status Workflow

```
Design Status Flow:
  🔴 In Progress → 🟡 In Review → 🟢 Ready for Dev → ✅ Complete

In Figma:
  - Use "Ready for dev" status on sections/frames to signal finalized work
  - Only "Ready for dev" frames appear prominently in Dev Mode
  - Developers should filter by this status to find actionable work
```

**Setting up status workflow:**
1. Select a section or top-level frame
2. In the right panel, set the development status
3. Use sections (not just frames) to group related screens with a shared status
4. Communicate status changes via Slack/ticketing integration

#### Annotation Best Practices

**Built-in annotations (preferred over manual redlines):**
- Select a layer and add annotations from the toolbar or right-click menu
- Annotation types: measurement, spacing, behavior notes, interaction specs, content notes
- Annotations auto-update when the design changes (manual redlines go stale)
- Annotations auto-show/hide at appropriate zoom levels
- Categorize annotations for easy scanning (interaction, content, technical)

**What to annotate:**
```
Must annotate:
├── Interaction behaviors (hover states, transitions, animations)
├── Edge cases (empty states, error states, loading states)
├── Responsive behavior (how layout changes at breakpoints)
├── Dynamic content rules (text truncation, max lines, overflow)
├── Conditional logic (show X when Y, hide if Z)
├── Accessibility requirements (focus order, screen reader text, ARIA labels)
└── Data requirements (API endpoints, data types, validation rules)

Do NOT annotate (Dev Mode provides automatically):
├── Exact pixel dimensions
├── Color hex values
├── Font properties
├── Spacing between elements
├── CSS/code snippets for individual elements
└── Asset export settings
```

**Measurement tool (Shift+M):**
- Click and drag to create persistent measurements between any two points
- Measurements update dynamically if elements move
- Use for calling out specific spacing that might be ambiguous

#### What Developers Actually Need from Figma Files

```
Critical (must-haves):
1. Clean auto layout structure (generates clean CSS)
2. Consistent use of variables/tokens (not hardcoded values)
3. Named layers that correspond to semantic HTML/component structure
4. All states designed (default, hover, active, focus, disabled, loading, error, empty)
5. Responsive behavior documented or demonstrated
6. Interaction specifications (what happens on click, hover, swipe)
7. Real content (not "Lorem ipsum" — real string lengths affect layout)

Nice to have:
8. Prototype with interactions for complex flows
9. Links to PRD/spec doc on cover page
10. Component API documentation (props, types, defaults)
11. Edge case screens (long text, missing data, permissions)
```

### Code Connect

Code Connect links Figma components to actual production code, replacing auto-generated code snippets in Dev Mode with real code from your codebase.

**Supported frameworks:** React, React Native, HTML/Web Components, Angular, Vue, SwiftUI, Jetpack Compose, Storybook

**Setup approaches:**

1. **Code Connect UI** (visual, in-Figma):
   - Quick setup, language-agnostic
   - Map components visually
   - Best for small/medium libraries

2. **Code Connect CLI** (repo-based):
   - Runs locally in your repository
   - Supports property mappings and dynamic code examples
   - Deeper integration, more accurate
   - Best for large, well-typed design systems

**Example Code Connect file (React):**
```tsx
// button.figma.tsx
import figma from "@figma/code-connect"
import { Button } from "./Button"

figma.connect(Button, "https://figma.com/file/abc123/Button", {
  props: {
    label: figma.string("label"),
    variant: figma.enum("Type", {
      Primary: "primary",
      Secondary: "secondary",
      Ghost: "ghost",
    }),
    size: figma.enum("Size", {
      Small: "sm",
      Medium: "md",
      Large: "lg",
    }),
    disabled: figma.boolean("isDisabled"),
    icon: figma.instance("iconSlot"),
  },
  example: ({ label, variant, size, disabled, icon }) => (
    <Button variant={variant} size={size} disabled={disabled}>
      {icon}
      {label}
    </Button>
  ),
})
```

**Requirements:** Organization or Enterprise plan with full Design or Dev Mode seat.

#### Optimizing Files for Handoff

1. **Use auto layout everywhere** — generates clean flexbox/CSS output in Dev Mode
2. **Apply variables, not hardcoded values** — Dev Mode shows variable names, not just hex codes
3. **Use consistent component structure** — devs can map Figma component hierarchy to code component hierarchy
4. **Keep layer hierarchy shallow** — deeply nested frames create unnecessarily complex DOM structures
5. **Export assets properly** — mark exportable assets, set export settings (SVG for icons, 2x PNG for photos)
6. **Group related screens in sections** — sections become Dev Mode's primary navigation unit
7. **Remove exploration/WIP from dev pages** — only finalized work on "Ready for dev" pages

---

## 5. Branching and Version Control

### When to Branch

**Branch when:**
- Making changes to a shared library file (design system updates)
- Experimenting with significant redesigns
- Working on a feature that needs review before merging
- Multiple designers need to work on the same file simultaneously
- Changes need QA/approval before going live

**Don't branch when:**
- Working in your own project file that nobody else uses
- Making trivial updates (fixing a typo)
- Rapid iteration where merge overhead exceeds benefit
- Your team is small (2-3 designers) and communicates changes verbally

### Branch Naming Conventions

**Recommended format:** `[type]/[ticket-id]-[short-description]`

```
feature/PROJ-1234-checkout-redesign
fix/PROJ-5678-button-alignment
update/DS-901-color-token-refresh
experiment/onboarding-variant-b
handoff/Q1-dashboard-specs
```

**Type prefixes:**
- `feature/` — New feature or screen design
- `fix/` — Bug fix or correction
- `update/` — Enhancement to existing design
- `experiment/` — Exploratory work, may not merge
- `handoff/` — Branch created specifically for dev handoff
- `refactor/` — Structural cleanup, no visual changes

**Alternative format (aligned with developer conventions):**
```
[platform]-[ticket-id]-[component]-[date]
android-5694-buttons-2026-03-18
web-1234-navigation-2026-03-18
```

**Tips:**
- Align naming with your engineering team's Git branch naming convention
- Use emoji in names for quick status identification: `🚧 feature/checkout` or `✅ ready/dashboard`
- If a designer has multiple branches open, the name should be identifiable even when truncated

### Merge Workflow

```
1. Create branch from main file
   ↓
2. Make changes in branch
   ↓
3. Request review (optional but recommended for library files)
   ↓
4. Reviewer previews: side-by-side comparison, overlay, added/edited/removed view
   ↓
5. Reviewer approves or requests changes
   ↓
6. Resolve any conflicts (choose which version wins per-element)
   ↓
7. Merge to main
   ↓
8. Publish library updates (if library file)
   ↓
9. Archive or delete the branch
```

**Conflict resolution:**
- Figma does NOT merge granularly — if two branches modify the same element, you must choose one version
- Coordinate who works on what before creating branches
- Keep branches short-lived to minimize conflict risk
- Merge frequently rather than accumulating large diffs
- For library files: only one designer should branch at a time, or split work by component area

### Version History Best Practices

- Use **Named Versions** to mark significant milestones: "v2.1 — Updated color system", "Final — Approved by stakeholders"
- Version history auto-saves every 30 minutes, but you can manually save with a name
- Named versions serve as restore points if a merge goes wrong
- Include date and context in version names: `2026-03-18 — Pre-migration snapshot`

---

## 6. Libraries at Scale

### Multi-Library Architecture

#### Recommended Library Split

```
🔶 Foundations Library (published)
├── Variables: Primitives (colors, spacing, radius, sizing)
├── Variables: Semantic tokens (light/dark modes)
├── Typography styles
├── Effect styles (shadows, blurs)
├── Grid styles
└── Utility components (_spacer, _divider, _grid-overlay)

🔷 Icons Library (published)
├── Icon/Navigation/...
├── Icon/Action/...
├── Icon/Status/...
├── Icon/Social/...
└── Icon/File/...

🟦 Core Components Library (published) — depends on Foundations + Icons
├── Button
├── Input
├── Checkbox / Radio / Toggle
├── Select / Dropdown
├── Modal / Dialog
├── Toast / Snackbar
├── Card
├── Avatar
├── Badge
├── Tooltip
├── Tabs
└── Accordion

🟩 Pattern Library (published) — depends on Core Components
├── Form patterns (login, signup, settings)
├── Navigation patterns (sidebar, header, breadcrumbs)
├── Data display patterns (tables, lists, stats)
├── Empty states
├── Error states
├── Loading states
└── Layout templates

🟨 Platform-Specific Libraries (optional)
├── iOS Components (native patterns)
├── Android Components (Material adaptations)
└── Email Templates
```

**Dependency chain:**
```
Foundations → Icons → Core Components → Patterns → Product Files
     ↓                    ↓                ↓
  (tokens)          (base building    (composed
                     blocks)           layouts)
```

**Why split libraries:**
- Designers enable only the libraries they need (reduces asset panel clutter)
- Smaller files load faster and stay under memory limits
- Teams can own and iterate on their library independently
- Breaking changes in one library don't require republishing everything
- Icons (often 500+) are the most common performance bottleneck — isolating them prevents dragging down the component library

#### Library Publishing Workflow

```
1. Create branch of library file
   ↓
2. Make changes in branch
   ↓
3. Test changes: create a test file, enable the branch library, verify instances update correctly
   ↓
4. Request review from design system team
   ↓
5. Reviewer checks: visual correctness, naming conventions, variable usage, accessibility
   ↓
6. Merge branch to main
   ↓
7. Publish library with descriptive update message
   ↓
8. Notify consumers via Slack/email with changelog
   ↓
9. Consumers accept updates in their files
```

**Publishing update messages format:**
```
[v2.3.0] Button component updates

Added:
- Button/Icon-Only variant
- Loading state with spinner

Changed:
- Updated hover state colors to use new semantic tokens
- Increased touch target to 44px minimum

Fixed:
- Focus ring visibility in dark mode

Breaking:
- Removed deprecated Button/Outline (use Button/Ghost instead)
- Icon property renamed from "leftIcon" to "leadingIcon"

Migration:
- Button/Outline instances will detach — replace with Button/Ghost manually
```

### Managing Breaking Changes

**Definition of breaking change in Figma:**
- Removing a component that is used as an instance elsewhere
- Renaming a component (breaks the link for existing instances)
- Removing a variant from a component set
- Changing component structure in ways that cause instance overrides to reset
- Renaming variant properties or values

**Mitigation strategies:**

1. **Deprecation phase:**
   - Mark old component with `[DEPRECATED]` prefix in name
   - Add a visible "DEPRECATED — Use X instead" label on the component
   - Keep deprecated component for 2-4 sprint cycles before removal
   - Move deprecated components to a `_Deprecated` page

2. **Migration guide:**
   - Document every breaking change with before/after
   - Provide step-by-step migration instructions
   - Use Figma's "Swap library" feature when replacing one component with another

3. **Beta testing:**
   - Share branch with key consumers before merging
   - Ask them to test their files with the branch library enabled
   - Collect feedback before finalizing

4. **Versioned libraries (for major overhauls):**
   - Keep `Design System v2` as a separate library during transition
   - Both v1 and v2 can be enabled simultaneously
   - Consumers migrate at their own pace
   - Sunset v1 after full adoption

### Extended Collections (Multi-Brand)

Figma's extended collections feature allows:
- Design system authors release a white-labeled base version
- Brand teams extend with their own themes
- Brand overrides publish as their own library
- Designers enable base + brand library together

**Structure:**
```
Base Library (published by DS team):
├── Collection: Semantic Colors
│   ├── Mode: Default (neutral values)
│
Brand A Override Library:
├── Collection: Semantic Colors (extends base)
│   ├── Mode: Brand-A (overrides specific tokens)
│
Brand B Override Library:
├── Collection: Semantic Colors (extends base)
│   ├── Mode: Brand-B (overrides specific tokens)
```

---

## 7. Performance Optimization

### Memory Limits and Warning Thresholds

```
Figma Memory Model (per browser tab):
├── 2 GB hard limit
├── 60% (~1.2 GB): Yellow warning — may experience multiplayer lag
├── 75% (~1.5 GB): Red warning — significant performance degradation
└── 100% (2 GB): File locks — no further editing until memory freed
```

### What Makes Files Slow

**Top causes (in order of impact):**

1. **Too many layers/objects on a single page** — Figma loads the active page into memory
2. **High-resolution images** — Uncompressed PNGs/photos are the #1 file size offender
3. **Excessive variants** — Component sets with 500+ variants load all variants into memory
4. **Deep nesting** — Each nesting level multiplies layout recalculation cost
5. **Complex effects** — Drop shadows, blurs, and multiple fills add GPU cost
6. **Hidden layers** — Still count toward memory even when invisible
7. **Unused components/styles** — Orphaned assets inflate file size
8. **Large prototype connections** — Files with hundreds of prototype flows

### File Size Guidelines

```
Healthy file:        < 100 MB
Getting heavy:       100-300 MB  → audit and optimize
Needs splitting:     300-500 MB  → split into multiple files
Critical:            500+ MB     → immediate intervention needed
```

**Note:** File size on disk is different from memory usage. A small file with thousands of component instances can use more memory than a large file with flat designs.

### When to Split Files

**Split when:**
- File regularly triggers yellow/red memory warnings
- Load time exceeds 15-20 seconds
- Multiple designers can't work in the file simultaneously without lag
- File has accumulated 50+ pages
- A library file exceeds 500 components

**How to split:**
- **By feature/flow:** Each major feature gets its own file
- **By platform:** Separate files for web, iOS, Android
- **By stage:** Separate exploration from production specs
- **For libraries:** Split by atomic level (foundations, icons, components, patterns)

### Optimization Checklist

#### Images
- [ ] Compress images before importing (use TinyPNG, Squoosh, or ImageOptim)
- [ ] Resize images to their display size — don't use a 4000x3000 photo in a 400x300 frame
- [ ] Use Figma's "Downsize" feature to reduce image fills to their layer size
- [ ] Use SVG for icons and illustrations (not PNG)
- [ ] Remove unused image fills from layers
- [ ] Consider linking to external images for frequently updated photos

#### Components
- [ ] Keep variant sets under 1,000 variants (performance cliff)
- [ ] Use boolean properties instead of show/hide variants
- [ ] Use instance swap properties instead of icon-per-variant
- [ ] Break large icon component sets into categorical sets (nav-icons, action-icons, status-icons)
- [ ] Limit nesting depth to 3-4 levels maximum
- [ ] Remove unused local components

#### Layers and Structure
- [ ] Delete hidden layers that are not needed
- [ ] Flatten decorative elements that don't need to be editable (Union, Flatten selection)
- [ ] Remove duplicate/overlapping layers
- [ ] Use components instead of copied groups (instances are lighter than copies)
- [ ] Clean up unused styles and variables

#### Effects
- [ ] Limit drop shadows to essential elements
- [ ] Use simpler shadow styles (single shadow vs. stacked)
- [ ] Avoid large blur values on large elements
- [ ] Remove unnecessary blur/shadow effects on hidden or small elements

#### Pages
- [ ] Archive old pages to a separate file (copy page, delete from main file)
- [ ] Use page-level loading — Figma only loads the active page into memory
- [ ] Keep page complexity roughly equal (don't have one page with 90% of the content)
- [ ] Move exploration/iteration history to an archive file

#### Plugins for Performance
- **Clean Document** — Remove unused styles, components, and hidden layers
- **Performance Optimizer & Diagnostics** — Identify and fix performance bottlenecks
- **TinyImage** — Compress images directly within Figma (up to 95% reduction)
- **Unused Components** — Find and remove components that aren't instanced anywhere

### File Load Time Optimization

Figma loads files one page at a time. The page you land on loads first, then other pages load in the background. To optimize:

1. Set a lightweight cover page as the default landing page
2. Keep the most-visited pages lean
3. Put heavy content (explorations, archives) on pages that are rarely visited
4. Figma caches recently visited files — frequent files load faster

---

## Sources

### File Organization
- [Figma Best Practices: Team, Project, and File Organization](https://www.figma.com/best-practices/team-file-organization/)
- [Getting Started with Teams in Figma Organization](https://www.figma.com/best-practices/getting-started-with-teams-in-figma-organization/)
- [Figma File Organization: A Detailed Guide (2025) — LoopStudio](https://loopstudio.dev/figma-file-organization/)
- [How We Organize Figma Projects and Files — Lee Munroe](https://leemunroe.medium.com/how-we-organize-figma-projects-and-files-on-our-design-team-adc4a6109dce)
- [Organize Like a Pro: Ultimate Guide to Figma File Organization — Tasia Sevenard](https://medium.com/@t.sevenard/organize-like-a-pro-ultimate-guide-to-figma-file-organization-8a3b97b60cd7)
- [Team, Project, File, Branching Naming Examples — Figma Community](https://www.figma.com/community/file/1043509291175170111)
- [How to Set Up Your Pages in Figma — Figma Blog](https://www.figma.com/blog/five-ways-to-structure-your-workflow-with-pages-in-figma/)
- [How We Organize Design Files and Cover Pages — Lee Munroe](https://leemunroe.medium.com/how-we-organize-design-files-and-cover-pages-in-figma-6316e3503220)

### Component Architecture
- [Creating Atomic Components in Figma — Figma Blog](https://www.figma.com/blog/creating-atomic-components-in-figma/)
- [Components, Styles, and Shared Library Best Practices — Figma](https://www.figma.com/best-practices/components-styles-and-shared-libraries/)
- [Structuring and Splitting Large-Scale Figma Design Systems: A 2025 Master Guide — Claus Nisslmueller](https://medium.com/@claus.nisslmueller/structuring-and-splitting-large-scale-figma-design-systems-a-2025-master-guide-for-scalable-c1c3a7dabb0e)
- [Explore Component Properties — Figma Learn](https://help.figma.com/hc/en-us/articles/5579474826519-Explore-component-properties)
- [Mastering Figma Components: Best Naming Practices — Rootstrap](https://www.rootstrap.com/blog/mastering-figma-components-best-naming-practices-for-seamless-design-to-development-workflow)
- [Mastering Constraints & Auto Layout — UIPrep](https://www.uiprep.com/blog/when-to-use-constraints-vs-auto-layout)
- [Guide to Auto Layout — Figma Learn](https://help.figma.com/hc/en-us/articles/360040451373-Guide-to-auto-layout)
- [Naming Layers: The Overlooked Tool for Designer-Developer Collaboration](https://www.designsystemscollective.com/naming-layers-the-overlooked-tool-for-designer-to-developer-collaboration-02603d7f36b9)

### Design Tokens and Variables
- [Overview of Variables, Collections, and Modes — Figma Learn](https://help.figma.com/hc/en-us/articles/14506821864087-Overview-of-variables-collections-and-modes)
- [Guide to Variables in Figma — Figma Learn](https://help.figma.com/hc/en-us/articles/15339657135383-Guide-to-variables-in-Figma)
- [Modes for Variables — Figma Learn](https://help.figma.com/hc/en-us/articles/15343816063383-Modes-for-variables)
- [Tailwind Design Tokens: Complete Guide 2025 — Nicola Lazzari](https://nicolalazzari.ai/articles/integrating-design-tokens-with-tailwind-css)
- [Figma Variables to Code: Tokens to Tailwind & CSS Vars — Figmafy](https://figmafy.com/figma-variables-to-code-tokens-to-tailwind-css-vars/)
- [Figma Design Tokens: How to Set Up, Sync, and Use Them in Code — TheFrontKit](https://thefrontkit.com/blogs/figma-design-tokens-guide)
- [Structuring Scalable Figma Variables for Multi-Brand — Border Crossing UX](https://bordercrossingux.com/structuring-figma-variables/)
- [Tokens Studio for Figma Documentation](https://docs.tokens.studio/)
- [Style Dictionary + SD Transforms — Tokens Studio](https://docs.tokens.studio/transform-tokens/style-dictionary)
- [Building a Scalable Design Token System: Figma to Code with Style Dictionary — Rahul Maheshwari](https://medium.com/@mailtorahul2485/building-a-scalable-design-token-system-from-figma-to-code-with-style-dictionary-e2c9eacc75aa)

### Developer Handoff
- [Guide to Developer Handoff — Figma Best Practices](https://www.figma.com/best-practices/guide-to-developer-handoff/)
- [The Designer's Handbook for Developer Handoff — Figma Blog](https://www.figma.com/blog/the-designers-handbook-for-developer-handoff/)
- [Figma Dev Mode Comprehensive Guide 2025 — Skywork](https://skywork.ai/blog/figma-dev-mode-comprehensive-guide-2025-everything-you-need-to-know/)
- [The Art and Science of Annotations in Dev Mode — Figma Blog](https://www.figma.com/blog/annotations-in-dev-mode/)
- [Add Measurements and Annotate Designs — Figma Learn](https://help.figma.com/hc/en-us/articles/20774752502935-Add-measurements-and-annotate-designs)
- [Code Connect — Figma Learn](https://help.figma.com/hc/en-us/articles/23920389749655-Code-Connect)
- [Getting Started with Code Connect CLI — Figma Developer Docs](https://developers.figma.com/docs/code-connect/quickstart-guide/)
- [Optimize Design Files for Developer Handoff — Figma Learn](https://help.figma.com/hc/en-us/articles/360040521453-Optimize-design-files-for-developer-handoff)

### Branching and Version Control
- [Branching in Figma — Figma Best Practices](https://www.figma.com/best-practices/branching-in-figma/)
- [Best Practices for Branching in Figma — Figma Scaling Design](https://www.figma.com/scaling-design/best-practices-for-branching-in-figma/)
- [Guide to Branching — Figma Learn](https://help.figma.com/hc/en-us/articles/360063144053-Guide-to-branching)
- [Figma Branches Best Practices — Jason Occhipinti / HP Design](https://medium.com/hp-design/figma-branches-best-practices-ca0871aa1631)
- [The Complete Guide to Figma Branching — Ben Maclaren](https://ben-maclaren.medium.com/the-complete-guide-to-figma-branching-15bc369f9df6)
- [From Chaos to Control: Versioning Your Figma Design System — Dan Rotondo](https://medium.com/@dm30roto/from-chaos-to-control-versioning-your-figma-design-system-f0b1fae04a45)

### Libraries at Scale
- [Guide to Libraries in Figma — Figma Learn](https://help.figma.com/hc/en-us/articles/360041051154-Guide-to-libraries-in-Figma)
- [Schema 2025: Design Systems for a New Era — Figma Blog](https://www.figma.com/blog/schema-2025-design-systems-recap/)
- [How to Build a Design System in Figma: A Practical Guide (2026) — Muzli](https://muz.li/blog/how-to-build-a-design-system-in-figma-a-practical-guide-2026/)
- [Design Systems: Single Library vs. Multiple Libraries — Figma Forum](https://forum.figma.com/archive-21/design-systems-single-library-v-multiple-libraries-25652)
- [Figma Variables Are Changing Component Architecture — Zoehart](https://medium.com/design-bootcamp/figma-variables-are-changing-component-architecture-heres-how-to-future-proof-your-library-24d8fed4c289)

### Performance
- [Reduce Memory Usage in Files — Figma Learn](https://help.figma.com/hc/en-us/articles/360040528173-Reduce-memory-usage-in-files)
- [Speeding Up File Load Times, One Page at a Time — Figma Blog](https://www.figma.com/blog/speeding-up-file-load-times-one-page-at-a-time/)
- [Speed Up Your Figma Files & Prototypes — Chris Godby](https://medium.com/@chrisgodby/speed-up-your-figma-files-prototypes-1b3fca11ce6d)
- [Why Your Figma Files Slow You Down — Phenomenon Studio](https://phenomenonstudio.com/article/why-your-figma-files-slow-you-down-and-how-to-fix-them/)
- [Performance Optimizer & Diagnostics Plugin — Figma Community](https://www.figma.com/community/plugin/1553042195396005088/performance-optimizer-diagnostics)
- [Best Practices for Image Optimization in Figma — Noble Desktop](https://www.nobledesktop.com/learn/figma/best-practices-for-image-optimization-in-figma-files)
