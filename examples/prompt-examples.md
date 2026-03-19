# Stitch Prompt Examples

Real-world prompt examples for common UI generation scenarios.

---

## Example 1: Mobile Fitness App Home Page

```
Platform: iOS (iPhone 15 Pro, 393x852)
Screen: Home / Dashboard
Style: Modern minimalist, dark mode, glassmorphism cards, subtle gradients
Layout: Vertical scroll, hero section at top, card grid below
Components:
  - Top: greeting text with user avatar (left), notification bell (right)
  - Hero: large card with today's summary stats, soft gradient background
  - Grid: 2-column card grid for quick actions (rounded corners, blur backdrop)
  - Bottom: tab bar with 4 items (Home / Explore / Activity / Profile)
Colors: primary #6C5CE7, accent #A29BFE, background #1A1A2E, card #2D2D44
Typography: SF Pro Display for headers, SF Pro Text for body
Constraints: iOS status bar reserved, bottom safe area for home indicator
```

---

## Example 2: Recipe Sharing App Detail Page

```
Platform: iOS (iPhone 15 Pro, 393x852)
Screen: Recipe Detail
Style: Warm editorial, clean white background, food photography focus
Layout: Full-screen hero image at top, scrollable content below
Components:
  - Top: full-width hero image of the dish (16:9 ratio)
  - Below image: recipe title (large serif), author avatar + name, rating stars
  - Info row: prep time / cook time / servings as icon + label pairs
  - Ingredients section: numbered list with checkbox toggles
  - Steps section: numbered cards with step photos
  - Bottom: floating "Start Cooking" button
Colors: primary #E85D3A, secondary #F4A261, background #FEFCFB, text #2D2D2D
Typography: Playfair Display for titles, Inter for body text
Constraints: iOS status bar, home indicator safe area
```

---

## Example 3: Desktop SaaS Analytics Dashboard

```
Platform: Web Desktop (1440x900)
Screen: Analytics Dashboard
Style: Clean professional, light theme, data-dense but readable
Layout: Left sidebar navigation (240px), top header bar, main content area with chart grid
Components:
  - Sidebar: logo, nav items with icons (Dashboard / Users / Revenue / Settings), user avatar at bottom
  - Header: page title "Analytics", date range picker, export button
  - Main: 4-column KPI cards at top (Users / Revenue / Conversion / Churn)
  - Main: large line chart (60% width), donut chart (40% width) on same row
  - Main: data table below charts with sortable columns
Colors: primary #2563EB, success #10B981, warning #F59E0B, background #F8FAFC, sidebar #1E293B
Typography: Inter for all text, monospace for data values
Constraints: None (desktop only)
```

---

## Example 4: Iteration Prompt (Single Fix)

After initial generation, fix ONE issue at a time:

```
On the Recipe Detail screen, make the "Start Cooking" button larger:
- Current: small text button at bottom
- Target: full-width floating button, height 56px, rounded corners 28px,
  background #E85D3A, white bold text 18px, subtle drop shadow
```

---

## Example 5: Consistency Patch

When Screen 3's buttons don't match Screen 1:

```
Redesign the navigation tab bar on this page to exactly match Screen 1:
- Pill-shaped active indicator with 8px border-radius
- Active icon: #6C5CE7, inactive icon: #8E8E93
- Background: rgba(45,45,68,0.95) with backdrop blur
- Height: 56px, evenly spaced 4 items
```

---

## Example 6: Language Patch

```
Switch all UI text on this screen to Simplified Chinese:
- "Dashboard" -> "仪表盘"
- "Analytics" -> "数据分析"
- "Users" -> "用户"
- "Revenue" -> "营收"
- "Export" -> "导出"
- "Settings" -> "设置"
```
