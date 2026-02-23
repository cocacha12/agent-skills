---
name: Monday Expert
description: Expertise in Monday.com Vibe Design System, UI/UX patterns, and technical architecture for cloning purposes.
---

# Monday Expert Skill

This skill provides instructions for creating "pixel-perfect" or "identity-accurate" clones of Monday.com features.

## Design Principles (Monday Vibe)

### 1. Color Palette
Monday uses a specific set of colors for groups and statuses.
- **Success/Done**: `#00c875`
- **Working on it**: `#fdab3d`
- **Stuck**: `#df2f4a`
- **Not Started/Empty**: `#c4c4c4`
- **Primary Blue**: `#007eb5`

### 2. Spacing & Typography
- **Font**: Monday uses "Figtree" or "Inter" as fallbacks.
- **Density**: Use "Compact" spacing by default. Items are typically `32px` to `40px` high.
- **Borders**: Soft borders (`1px solid #e1e4e8`) with subtle shadows.

### 3. Component Hierarchy
- **Board**: The top-level container.
- **Group**: Collapsible sections. Always has a color-coded left border.
- **Item**: A row in the table.
- **Pulse**: The "name" cell of an item.

## Interaction Patterns

### 1. Inline Editing
- Clicking on a cell should focus an input.
- `Tab` navigates through cells.
- `Enter` saves and moves down.

### 2. Optimistic UI
- State should update locally before the server responds.
- Use `useBoard` or similar context providers for global state.

### 3. Progressive Disclosure
- Show "Add Item" inputs at the top of each group.
- Reveal "Delete" and "Management" buttons only on hover.

## Technical Architecture
- **Context API**: Centralized state for the board, items, and columns.
- **Local Storage**: Persistence for "backend-less" demos.
- **Shadcn UI**: Base components (Table, Dropdown, Button) customized to match Monday's look.

## Reference
- Official Design System: [style.monday.com](https://style.monday.com/)
