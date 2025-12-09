# Lean Canvas Project - AI Coding Instructions

## Project Overview
This is a static HTML presentation system for Lean Canvas business models. The project contains multiple themed directories (currently `gastronomía/` and `joyería/`) with interactive, animated business planning documents.

## Architecture & Structure

### Directory Organization
- Each business vertical has its own directory (e.g., `gastronomía/`, `joyería/`)
- Within each directory: `index.html` (main Lean Canvas), `jobs-to-be-done.html`, `prueba-deseabilidad.html`, `roadmap.html`
- No build system, CSS/JS frameworks, or package.json - pure HTML/CSS/JS

### Navigation Pattern
All HTML files share a consistent fixed navigation bar in the top-right:
```html
<nav class="navbar">
    <a href="index.html" class="nav-link">🏠 Lean Canvas</a>
    <a href="roadmap.html" class="nav-link">🗺️ Roadmap</a>
    <a href="jobs-to-be-done.html" class="nav-link">👤 Cliente</a>
    <a href="prueba-deseabilidad.html" class="nav-link">✨ Deseabilidad</a>
</nav>
```
Mark the current page with `class="nav-link active"`.

## Design System

### Visual Theme
- Dark futuristic aesthetic: background `#0f0f23`, radial gradient to `#1a1a3e`
- Primary gradient: `linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%)`
- Glass-morphism: `rgba(30, 30, 60, 0.6)` with `backdrop-filter: blur(10px)`
- Animated particle background (50 floating dots)

### Typography
- Font stack: `'Inter', 'Segoe UI', system-ui, sans-serif`
- Main headings: 3.5-4em, gradient text fill, letter-spacing -1 to -2px
- Body text: 1.15em, `#cbd5e0`, line-height 1.7-2

### Animation Standards
- Entry animations: `fadeInDown`, `fadeInUp`, `scaleIn` with staggered delays (0.2s increments)
- Hover effects: `transform: translateY(-2px)` + glow shadow
- Timing: `cubic-bezier(0.175, 0.885, 0.32, 1.275)` for bounce effects

### Component Patterns
**Cards/Sections:**
```css
background: rgba(30, 30, 60, 0.6);
backdrop-filter: blur(10px);
border: 2px solid rgba(102, 126, 234, 0.3);
border-radius: 20px;
padding: 40px;
```

**Buttons/Links:**
```css
background: rgba(102, 126, 234, 0.9);
padding: 12px 24px;
border-radius: 25px;
border: 2px solid rgba(102, 126, 234, 0.5);
transition: all 0.3s ease;
```

**Metrics/Tags:**
```css
background: linear-gradient(135deg, #667eea, #764ba2);
padding: 5px 15px;
border-radius: 15px;
```

## Content Structure

### index.html Specifics
- Uses CSS Grid: `grid-template-columns: repeat(5, 1fr); grid-template-rows: repeat(3, auto);`
- 10 Lean Canvas blocks with specific grid positions (`.block-problema`, `.block-solucion`, etc.)
- Each block includes: icon (3em), title (1.3em uppercase), content, and optional metrics
- Includes modal system for pitch deck (`.pitch-modal`, toggled with `.active` class)

### Content Template Pattern
All pages follow this structure:
1. Particle background (`<div class="particles" id="particles"></div>`)
2. Fixed navbar
3. Container with header (title + subtitle/goal-box)
4. Main content sections
5. Optional copy-paste card at bottom
6. Inline JavaScript for particles and interactions

## Development Workflows

### Creating New Pages
1. Copy structure from existing page in the same directory
2. Update navigation active state
3. Adjust title, subtitle, and section count
4. Maintain consistent spacing: `padding: 100px 20px 40px 20px` on container
5. Ensure particle system JavaScript is included at bottom

### Adding New Business Verticals
1. Create new directory at root level
2. Copy all 4 HTML files from `gastronomía/` as templates
3. Update content while preserving all styling and structure
4. Navigation links remain relative (`index.html`, not `../`)

### Copy-Paste Cards
When adding plain-text versions for user copying (as mentioned in `prompt` file):
- Place at end of content, before `</div>` closing container
- No emojis, no formatting, just plain text wrapped in selectable box
- Use `white-space: pre-wrap; user-select: all;` on content paragraph

## JavaScript Conventions
- All JavaScript is inline in `<script>` tags at end of `<body>`
- Particle generation: 50 particles, random sizes 2-6px, 10-30s animation duration
- Modal controls: Add/remove `.active` class, close on ESC or outside click
- No external libraries or frameworks

## Language & Content
- All content is in Spanish
- Use emoji icons consistently (🏠, 🗺️, 👤, ✨, 💰, 🎯, 🚀, etc.)
- Metric displays use `<span class="metric">` with specific values

## When Adding Features
- Maintain visual consistency across all pages in a directory
- Test responsive behavior (though current focus is desktop)
- Keep animations performant (transform/opacity only)
- Preserve the futuristic, high-energy design aesthetic
- Always include navigation updates across all related pages
