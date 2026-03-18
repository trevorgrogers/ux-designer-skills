---
name: figma-ai-coding
description: Figma to code with AI — MCP server workflow, vibe coding, Code Connect, file preparation, design tokens, and plugin ecosystem. Use when going from Figma designs to production code with Claude Code, Cursor, or other AI coding tools.
---

# Figma + AI Coding Workflows

## When to Use This Skill

**Use when you need:**
- To implement a Figma design in code using Claude Code or Cursor
- To set up or configure the Figma MCP server
- To prepare Figma files so AI tools generate better code
- To map Figma components to codebase components (Code Connect)
- To export design tokens from Figma to Tailwind CSS / CSS custom properties
- To understand the "vibe coding" design-to-code landscape

---

## 1. Figma MCP Server — Complete Reference

### What It Is

The Figma MCP (Model Context Protocol) server is a universal bridge between AI coding tools and Figma. It lets AI agents read design data, extract tokens, capture screenshots, and even push code back to Figma as editable layers. It works with Claude Code, Cursor, VS Code, Windsurf, Codex, and others.

### Setup

**Claude Code (recommended):**
```bash
claude plugin install figma@claude-plugins-official
```

**Claude Code (manual):**
```bash
claude mcp add --transport http figma https://mcp.figma.com/mcp
```

**Cursor:**
```
/add-plugin figma
```
Or: Settings > MCP > Add new global MCP server > URL: `https://mcp.figma.com/mcp`

**VS Code:**
1. `Cmd+Shift+P` > "MCP: Add Server"
2. Select HTTP, paste `https://mcp.figma.com/mcp`, ID: `figma`
3. Open Agent mode with `Opt+Cmd+B`

**Any MCP-compatible editor:**
```json
{
  "mcpServers": {
    "figma": {
      "url": "https://mcp.figma.com/mcp"
    }
  }
}
```

**Verify:** In Claude Code, run `claude mcp list` to confirm the server is connected. Use `/mcp` to authenticate via OAuth.

### Complete Tool Reference

| Tool | Supported Files | Purpose |
|------|----------------|---------|
| `get_design_context` | Design, Make | Core tool. Returns structured React + Tailwind representation of your Figma selection |
| `get_screenshot` | Design, FigJam | Visual reference screenshot preserving layout fidelity |
| `get_metadata` | Design | Sparse XML with layer IDs, names, types, positions, sizes. Use for large designs |
| `get_variable_defs` | Design | Returns variables and styles (colors, spacing, typography tokens) |
| `get_code_connect_map` | Design | Returns mapping of Figma node IDs to code components |
| `add_code_connect_map` | Design | Creates new mappings between Figma nodes and code components |
| `get_code_connect_suggestions` | Design | AI-detects and suggests Code Connect mappings |
| `send_code_connect_mappings` | Design | Confirms and finalizes Code Connect mappings |
| `generate_figma_design` | Design | Captures live UI and sends to Figma as editable layers (Claude Code + Remote only) |
| `generate_diagram` | None | Creates FigJam diagrams from Mermaid syntax |
| `get_figjam` | FigJam | Returns FigJam diagram metadata as XML with screenshots |
| `create_design_system_rules` | None | Generates rule files for codebase-aware code generation |
| `whoami` | None | Returns user email, plan, seat info |

### Tool Details

**`get_design_context`** is the primary tool. It accepts a `fileKey` and `nodeId` (extracted from Figma URLs) and returns a structured representation defaulting to React + Tailwind. This output is translatable to any framework via prompting (e.g., "generate my Figma selection in Vue", "use Chakra UI for this layout", "generate plain HTML + CSS").

**`get_screenshot`** captures a pixel-accurate image of the selected frame. Keep this enabled unless you are managing token limits. It serves as the ground truth for visual validation.

**`get_metadata`** returns a lightweight XML representation. Use it when `get_design_context` returns truncated output on large designs — fetch metadata first, then re-fetch specific child nodes individually.

**`get_variable_defs`** extracts design tokens directly. Prompt examples: "list all tokens used", "what color and spacing variables are in my selection?"

**`generate_figma_design`** (code-to-canvas) captures rendered browser UI and converts it to fully editable Figma layers with real text, separate components, and auto layout. Currently Claude Code-only and Remote MCP-only. Announced February 2026.

### Rate Limits

- **Starter plan / View+Collab seats:** 6 tool calls per month
- **Dev/Full seats on Pro/Org/Enterprise:** Per-minute limits matching Figma REST API Tier 1
- **Write tools** (generate_figma_design): Exempt from rate limits

---

## 2. The 7-Step Implementation Workflow

This is the canonical workflow for going from a Figma URL to production code.

### Step 1: Extract Node ID from URL
Parse the Figma URL to get `fileKey` and `nodeId`:
```
https://figma.com/design/kL9xQn2VwM8pYrTb4ZcHjF/DesignSystem?node-id=42-15
                          ^^^^^^^^^^^^^^^^^^^^^^^^                    ^^^^^
                          fileKey                                     nodeId
```

### Step 2: Fetch Design Context
```
get_design_context(fileKey="kL9xQn2VwM8pYrTb4ZcHjF", nodeId="42-15")
```
Returns layout properties, typography, colors, tokens, component structure, spacing. If truncated, use `get_metadata` first, then re-fetch individual child nodes.

### Step 3: Capture Visual Reference
```
get_screenshot(fileKey="kL9xQn2VwM8pYrTb4ZcHjF", nodeId="42-15")
```
Keep this screenshot accessible as the source of truth for visual validation throughout implementation.

### Step 4: Download Required Assets
Download images, icons, and SVGs from the Figma MCP server's built-in assets endpoint. Critical rules:
- **Use localhost sources returned by the server directly** — do not modify URLs
- **Do NOT import new icon packages** — all assets should come from the Figma payload
- **Do NOT create placeholder assets** if localhost sources are provided

### Step 5: Translate to Project Conventions
- Treat Figma MCP output as a design/behavior representation, NOT final code
- Replace generic Tailwind classes with project design system tokens
- Reuse existing components instead of duplicating
- Use project's color system, typography scale, spacing tokens
- Respect existing routing and state management patterns

### Step 6: Achieve 1:1 Visual Parity
- Match Figma designs exactly; prioritize visual fidelity
- Avoid hardcoded values; use design tokens
- When project tokens conflict with Figma specs: prefer tokens but adjust minimally for visual match
- Follow WCAG accessibility requirements
- Add component documentation

### Step 7: Validate Against Figma
Compare the implementation side-by-side with the Figma screenshot. Verify:
- Layout and spacing
- Typography (family, size, weight, line height)
- Colors and gradients
- Interactive states
- Responsive behavior
- Asset rendering
- Accessibility

### Common Issues

| Problem | Solution |
|---------|----------|
| Truncated output | Use `get_metadata` first, then fetch specific nodes individually |
| Visual mismatch | Compare side-by-side with screenshot; verify spacing, colors, typography |
| Assets not loading | Verify server's assets endpoint is accessible; use localhost URLs directly |
| Token value differences | Prefer project tokens but adjust spacing/sizing minimally for visual fidelity |

---

## 3. Custom Rules for AI Agents

### Claude Code (CLAUDE.md)
```markdown
# MCP Servers

## Figma MCP server rules

- The Figma MCP server provides an assets endpoint for images and SVG files
- IMPORTANT: Use localhost sources returned by the Figma MCP server directly
- IMPORTANT: Do NOT import/add new icon packages — all assets should be in the Figma payload
- IMPORTANT: Do NOT create placeholder images/icons when a localhost source is provided

## Figma Implementation Flow

1. Run get_design_context first for structured representation
2. If response is too large, run get_metadata then re-fetch specific nodes
3. Run get_screenshot for visual reference
4. Only after both context and screenshot, download assets and start implementation
5. Translate output (React + Tailwind default) to project conventions
6. Validate against Figma for 1:1 visual parity

## Implementation Rules

- Treat Figma MCP output as design/behavior representation, not final code
- Replace Tailwind utilities with project design-system tokens
- Reuse existing components — do not duplicate
- Use color system, typography, spacing tokens consistently
- Respect existing routing and state management patterns
- Achieve 1:1 visual parity; adjust minimally for tokens
- Validate final UI against Figma for look and behavior
```

### Cursor (.cursorrules)
```yaml
---
description: Figma MCP server rules
globs:
alwaysApply: true
---
- The Figma MCP server provides an assets endpoint for images/SVGs
- IMPORTANT: Use localhost sources returned by Figma MCP directly
- IMPORTANT: DO NOT import new icon packages
- IMPORTANT: Do NOT create placeholders if localhost source provided
- Always use design system components when available
- Prioritize Figma visual fidelity
- Avoid hardcoded values; use design tokens
```

### Generating Rules Automatically
Use the `create_design_system_rules` tool with no file context. It analyzes your codebase and generates a rule file covering token definitions, component architecture, frameworks, asset management, styling approaches, and project structure. Save the output to your `rules/` or `instructions/` directory.

---

## 4. Code Connect

### What It Is

Code Connect is Figma's bridge between your codebase and Figma Dev Mode. It maps design components to actual code implementations, so when the MCP server processes frames containing Code Connect-mapped components, it generates `<CodeConnectSnippet>` wrappers containing:
- Current property values from the Figma component
- Import statements showing how to access the component
- Actual usage code from your implementation
- Custom guidance instructions for AI agents

Code Connect is the single most impactful thing you can do to improve AI code generation quality from Figma.

### Two Setup Methods

**Code Connect UI (visual, in-Figma):**
- Runs entirely inside Figma
- Language-agnostic
- Quick to set up
- Ideal for teams wanting simple visual linking
- Supports one-to-many mappings (one design component to React, SwiftUI, Vue, etc.)

**Code Connect CLI (terminal, in-codebase):**
- Runs from terminal within your local codebase
- Publishes connections to Figma
- Provides richer implementation details: explicit imports, user-defined code snippets, direct prop mappings
- Supports React, React Native, Storybook, HTML (Web Components, Angular, Vue), SwiftUI, Jetpack Compose

### MCP Integration

The MCP tools for Code Connect:
- `get_code_connect_map` — retrieves existing mappings as `{nodeId: {codeConnectSrc, codeConnectName}}`
- `add_code_connect_map` — creates new mappings between Figma nodes and code components
- `get_code_connect_suggestions` — AI detects and suggests mappings between design and code components
- `send_code_connect_mappings` — confirms and finalizes suggested mappings

### Best Practices
1. Connect frequently-used design system components first (buttons, inputs, cards, nav items)
2. Use "Add instructions for MCP" to document patterns, accessibility requirements, and usage guidelines
3. Keep mappings synchronized with codebase changes
4. Test instructions using the Code Connect UI preview tool

---

## 5. Preparing Figma Files for AI Consumption

How you structure your Figma file directly determines the quality of AI-generated code. These practices make the biggest difference.

### Semantic Layer Naming

**Bad:** `Frame 1268`, `Group 5`, `Rectangle 42`
**Good:** `CardContainer`, `ProductImage`, `CTA_Button`, `NavBar`

Use names like `Button/Primary`, `Input/Email`, `Card/Product`. Semantic naming helps AI generate the right HTML tags (`<button>`, `<label>`, `<input>`) and understand component hierarchy.

Figma has a built-in "Rename layers with AI" feature that can batch-rename layers to semantic names. Use it.

### Auto Layout (maps to Flexbox/Grid)

Auto Layout is not optional for AI workflows. It maps directly to CSS Flexbox and Grid. Without it, AI tools guess at structure and produce absolute-positioned spaghetti code.

Apply auto layout to:
- Vertical lists (flex-direction: column)
- Horizontal rows (flex-direction: row)
- Grid layouts
- Card layouts with spacing
- Navigation bars

Test frame resizing before code generation to ensure expected responsive behavior.

### Use Components for Everything Repeated

Buttons, cards, inputs, nav items, avatars — anything used more than once should be a Figma component. This enables:
- Reusable code generation
- Code Connect mapping
- Consistent implementation

### Apply Figma Variables for Design Tokens

Set variables for:
- **Colors** (brand, semantic, neutral, surface)
- **Spacing** (4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px)
- **Border radius** (sm, md, lg, full)
- **Typography** (font family, size scale, weight, line height)

Variables with modes (light/dark) map directly to CSS custom properties with theme switching.

### Keep Hierarchy Flat

Aim for 2-3 levels max. Deep nesting produces deeply nested code. Flat hierarchies produce clean, maintainable component trees.

### Add Annotations

Use Figma annotations to communicate:
- Behavioral expectations (hover states, animations, transitions)
- Responsive breakpoint behavior
- Conditional rendering logic
- Accessibility requirements (ARIA labels, keyboard navigation)

### Add Dev Resources

Link relevant documentation, API endpoints, or specifications to layers in Dev Mode. These show up as actionable references in the MCP output.

---

## 6. Design Tokens: Figma Variables to Tailwind CSS

### The Token Pipeline

```
Figma Variables → Export Plugin → CSS Custom Properties / Tailwind Config → Code
```

### Figma Plugins for Token Export

| Plugin | Direction | Features |
|--------|-----------|----------|
| **Tailwind Tokens** | Bidirectional | Bridge between Tailwind CSS and Figma variables/styles. Auto-converts tokens. Free. |
| **TokenFlow** | Figma to Code | Extracts Figma variables, paste directly into Tailwind v4 config |
| **Figtail** | Code to Figma | Imports Tailwind v4 and custom CSS tokens as native Figma variables. Supports `@theme`, `:root`, `oklch`, `color-mix()`, `var()` chains, dark mode |
| **Layout (Tailwind CSS V4)** | Bidirectional | Full Tailwind v4 import/export for design tokens |
| **Export Variables** | Figma to Code | Exports to CSS, SCSS, and Tailwind |
| **Tokens Studio** | Bidirectional | Manages tokens in Figma, syncs to Git as JSON, transforms into CSS vars or Tailwind config |
| **Figma Design Tokens Exporter** | Figma to Code | Exports to CSS, JSON, and Tailwind |

### Tailwind v4 Integration

Tailwind v4 uses CSS-native `@theme` for configuration, making Figma variable mapping more direct:

```css
@theme {
  --color-primary: oklch(0.6 0.2 260);
  --color-surface: oklch(0.98 0.01 260);
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --radius-sm: 0.25rem;
  --radius-md: 0.5rem;
  --font-heading: "American Grotesk", sans-serif;
}
```

Figma variables with modes (light/dark) map to:
```css
:root {
  --color-background: oklch(0.98 0.01 260);
  --color-text: oklch(0.15 0.01 260);
}

[data-theme="dark"] {
  --color-background: oklch(0.15 0.01 260);
  --color-text: oklch(0.95 0.01 260);
}
```

Components always reference `var(--color-background)` — the value changes based on the active theme.

### MCP Token Extraction

Use `get_variable_defs` to extract tokens directly from a Figma selection:
- "List all tokens used in this frame"
- "What color and spacing variables are in my selection?"
- "Get the variable names and their values"

This returns structured token data you can map to your Tailwind config or CSS custom properties.

---

## 7. Vibe Coding

### What It Is

Vibe coding is the practice of using AI to generate code from natural language descriptions, design files, or visual references — where you describe the "vibe" (tone, look, emotional impact) and the function (layout, behavior, interactivity), and AI produces working code. Coined by Andrej Karpathy in early 2025.

The key distinction: you focus on the *what* and *why*, not the *how*. You evaluate the output visually and functionally rather than reading every line of code.

### Best Practices

1. **Create wireframes before prompting.** A quick wireframe or workflow map helps you (and the AI) understand how everything connects. Figma wireframes fed through the MCP server outperform text-only prompts.

2. **Set up data structure first.** If your app connects to structured data (databases, APIs, Airtable, Supabase), establish the schema before the AI writes logic around it.

3. **Start with a single component, not a whole page.** Break large screens into smaller components — generate cards, headers, and sidebars separately. This reduces errors and keeps context manageable.

4. **Iterate rapidly.** Get something testable quickly, even if rough. Use AI to spin up several versions, experiment with interactions, and iterate based on feedback.

5. **Treat AI as a collaborator, not magic.** Structure and specificity produce better results than vague prompts. The best vibe coding comes from clear design intent, not shortcuts.

6. **Use design system inheritance.** When possible, generate from an existing design system so AI applies your brand colors, typography, and spacing automatically.

### Figma Make

Figma Make (launched May 2025) is Figma's vibe coding tool. Key features:
- Generates interactive React applications from text prompts, images, or design frames
- Reads existing style libraries, component sets, and design tokens
- Automatically applies brand colors, typography scales, and spacing systems
- Available on all paid Figma seats (Full seats, starting at $16/month annually)
- Powered by Anthropic's Claude 3.7 Sonnet
- Supports `get_design_context` from the MCP server (designs built in Make can be implemented via MCP)

---

## 8. Figma-to-Code Plugin Ecosystem

### First-Party (Figma)

| Tool | What It Does |
|------|-------------|
| **Figma MCP Server** | Feeds design tokens, variants, and component properties directly to AI coding assistants |
| **Figma Make** | Generates working React apps from prompts, images, or design frames with design system inheritance |
| **Figma Sites** | Design and publish responsive websites directly from Figma |
| **Code Connect** | Maps Figma components to codebase components for consistent AI code generation |

### Third-Party Plugins

| Plugin | Frameworks | Key Strength |
|--------|-----------|-------------|
| **Anima** | React, Vue, HTML, Tailwind, shadcn, Next.js, TypeScript | 1.5M+ installs. Most-installed design-to-code plugin. Playground for vibe coding from Figma prototypes. Full design system import. |
| **Locofy.ai** | React, Next.js, React Native, HTML/CSS, Flutter, Vue, Angular | Large Design Models (LDMs) for accurate conversion. Smart GitHub merge preserves developer code. Two modes: Lightning (one-click) and Classic (step-by-step). |
| **Builder.io Visual Copilot** | React, Vue, Svelte, Angular, Tailwind, Emotion, Styled Components | AI-powered with CLI for granular control. Deep Cursor integration. Maps to existing codebase components. |
| **TeleportHQ** | HTML, React, Vue, WordPress | Exports responsive code builds. Good for marketing/landing pages. |

### Which to Use When

- **MCP Server + Code Connect** — Best for teams with established design systems and AI coding workflows (Claude Code, Cursor). Zero plugin overhead, works natively.
- **Anima** — Best for rapid prototyping and vibe coding. Import full Figma prototypes (multi-screen flows) and get working apps. Strong design system support.
- **Locofy** — Best for production handoff with ongoing design iteration. GitHub merge feature preserves developer-added business logic across design updates.
- **Builder.io Visual Copilot** — Best for teams already using Builder.io CMS. Strong Cursor integration. CLI gives developers fine-grained control.

---

## 9. Claude Code + Figma: Complete Workflow

### Bidirectional Integration (as of Feb 2026)

Claude Code and Figma now support two-way communication:
1. **Design to Code:** Read Figma design data via MCP, generate production code
2. **Code to Design:** Push UIs built in Claude Code back to Figma as editable layers via `generate_figma_design`

### Workflow: Design to Code

```
1. Designer creates/updates design in Figma
2. Designer shares Figma URL with developer
3. Developer pastes URL into Claude Code
4. Claude Code calls get_design_context → gets structured representation
5. Claude Code calls get_screenshot → gets visual reference
6. Claude Code downloads assets from MCP assets endpoint
7. Claude Code generates code using project conventions
8. Developer reviews and iterates
```

### Workflow: Code to Design

```
1. Developer builds UI with Claude Code (local dev server)
2. Developer prompts: "Send this to Figma"
3. Claude Code calls generate_figma_design
4. Browser state is captured and converted to Figma layers
5. Designer receives editable Figma file with:
   - Real editable text
   - Separate component layers
   - Auto layout applied
6. Designer iterates on the design
```

### Practical Prompts for Claude Code

**Implementing a design:**
```
Implement this Figma design: [paste Figma URL]
Use components from src/components/ui
Use our Tailwind design tokens
```

**Framework translation:**
```
Generate this Figma selection in Vue 3 with Composition API
Generate iOS SwiftUI code from this frame
Generate plain HTML + CSS, no framework
```

**Targeted implementation:**
```
Add this to src/components/marketing/PricingCard.tsx
Use our Stack layout component for the grid
Match the Figma spacing exactly using our spacing tokens
```

**Token extraction:**
```
Get the variables used in my Figma selection
List all color and spacing tokens in this frame
Map these Figma tokens to our existing Tailwind theme
```

**Code to Figma:**
```
Start a local server for my app and capture the homepage UI in a new Figma file
Capture this component in its hover state and send to Figma
```

### Selection Size Management

Break large screens into smaller components for best results:
- Generate `Header`, `Sidebar`, `ProductCard`, `Footer` separately
- Reduces errors, slow responses, and truncated output
- Keeps context manageable for the model
- Combine generated components in your codebase, not in a single MCP call

### Limitations (as of March 2026)

- Code-to-Figma is one-directional for business logic: visual layers transfer, but event handlers, state management, and routing do not survive the round trip
- `generate_figma_design` is Claude Code-only and Remote MCP-only
- Starter plan users get only 6 MCP tool calls per month
- Very large designs may truncate `get_design_context` output (use `get_metadata` + targeted fetches)

---

## Sources

- [Guide to the Figma MCP Server — Figma Help Center](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server)
- [Figma MCP Server Guide — GitHub](https://github.com/figma/mcp-server-guide)
- [Tools and Prompts — Figma Developer Docs](https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts/)
- [Structure Your Figma File for Better Code — Figma Developer Docs](https://developers.figma.com/docs/figma-mcp-server/structure-figma-file/)
- [Code Connect Integration — Figma Developer Docs](https://developers.figma.com/docs/figma-mcp-server/code-connect-integration/)
- [Add Custom Rules — Figma Developer Docs](https://developers.figma.com/docs/figma-mcp-server/add-custom-rules/)
- [Implement Design Skill — Figma MCP Server Guide](https://github.com/figma/mcp-server-guide/blob/main/skills/implement-design/SKILL.md)
- [Introducing Our Dev Mode MCP Server — Figma Blog](https://www.figma.com/blog/introducing-figma-mcp-server/)
- [From Claude Code to Figma — Figma Blog](https://www.figma.com/blog/introducing-claude-code-to-figma/)
- [Claude Code + Figma MCP Server — Builder.io](https://www.builder.io/blog/claude-code-figma-mcp-server)
- [Figma to Cursor for Designers — Builder.io](https://www.builder.io/blog/figma-to-cursor-for-designers)
- [Figma to Code with Cursor and Visual Copilot — Builder.io](https://www.builder.io/blog/figma-to-cursor)
- [Code Connect — Figma Help Center](https://help.figma.com/hc/en-us/articles/23920389749655-Code-Connect)
- [Code Connect Introduction — Figma Developer Docs](https://developers.figma.com/docs/code-connect/)
- [What is Vibe Coding? — Figma Resource Library](https://www.figma.com/resource-library/what-is-vibe-coding/)
- [Vibe Coding Tool — Figma Make](https://www.figma.com/solutions/vibe-coding-tool/)
- [8 Vibe Coding Best Practices (2026) — Softr](https://www.softr.io/blog/vibe-coding-best-practices)
- [How to Structure Figma Files for MCP — LogRocket](https://blog.logrocket.com/ux-design/design-to-code-with-figma-mcp/)
- [Figma Variables to Code: Tokens to Tailwind & CSS Vars — Figmafy](https://figmafy.com/figma-variables-to-code-tokens-to-tailwind-css-vars/)
- [Tailwind Tokens Plugin — Figma Community](https://www.figma.com/community/plugin/1513618945140968492/tailwind-tokens-create-tailwind-css-variables-styles)
- [TokenFlow: Figma Variables to Tailwind 4 — Figma Community](https://www.figma.com/community/plugin/1605970848776920025/tokenflow-figma-variables-to-tailwind-4)
- [Figtail: Import Tailwind & Custom CSS as Figma Variables — Figma Community](https://www.figma.com/community/plugin/1605825399470035343/figtail-import-tailwind-custom-css-as-figma-variables)
- [Anima — Figma to Code](https://www.animaapp.com/figma)
- [Locofy.ai — Design to Code](https://www.locofy.ai/)
- [Figma to Code Tool Comparisons — Locofy](https://www.locofy.ai/figma-to-code-tool-comparison)
- [Rename Layers with AI — Figma Help Center](https://help.figma.com/hc/en-us/articles/24004711129879-Rename-layers-with-AI)
