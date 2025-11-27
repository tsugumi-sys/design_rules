# Instructions for Claude

## When User Creates a New Design Rule Directory

When the user creates a new directory with `DESIGN_RULES.md`, follow these steps:

### Step 1: Read the Design Rules
```
Read the DESIGN_RULES.md file in the directory
```

### Step 2: Generate index.html
Create a single HTML file (`index.html`) in the same directory that:
- Includes all CSS inline (no external stylesheets)
- Follows all design specifications from DESIGN_RULES.md
- Implements a comprehensive demo page with the following sections:

#### Required Sections:

- please use image sources;
  - avatar image (using `https://i.pravatar.cc/150?img=N`)
  - normal images: lorem picsum
- All links should be dummy links (`href="#"`)
- Use lorem ipsum for all text content (minimum 150 words total)
- Include at least 1 different dummy images from picsum.photos
- Include various UI elements: buttons (primary, secondary, outline), cards, badges, input fields
- Demonstrate responsive design principles (mobile-friendly)
- Include a table somewhere (e.g., feature comparison or data table)
- Use semantic HTML5 elements (header, nav, main, section, article, footer)
- Ensure all interactive elements have hover states

---

## Product-Specific UI Components

To make each design system's demo page distinctive and recognizable, include these product-specific components and patterns:

### Apple Design (apple/)
Add these Apple-specific UI patterns:

1. **Large Product Showcase**
   - Full-width product image with floating text overlay
   - Clean, minimalist presentation with lots of white space
   - Centered content with generous padding

2. **Segmented Control** (in Features or Pricing section)
   - iOS-style segmented button group
   - Pills/tabs for switching between options
   - Example: "Monthly / Yearly" pricing toggle

3. **App Icon Grid**
   - Section showing app-style icons in a grid (3x3 or 4x4)
   - Rounded square icons with labels
   - Similar to iOS home screen layout

4. **Notification/Alert Card**
   - iOS-style notification banner or card
   - Rounded corners with subtle shadow
   - Icon, title, and message

5. **Product Card with Specs**
   - Card showing product with technical specifications
   - Clean list format similar to Apple product pages
   - "From $X" pricing display

6. **Hero with Gradient Background**
   - Use subtle gradients (light gray to white)
   - Large, bold typography
   - Minimal content, maximum impact

### Google/Material Design (google/)
Add these Material Design-specific UI patterns:

1. **Floating Action Button (FAB)**
   - Circular button fixed to bottom-right corner
   - Elevated with prominent shadow
   - Primary color with icon (use emoji like ➕ or ✏️)

2. **Material Cards with Actions**
   - Cards with header, content, and action buttons at bottom
   - "SHARE" and "LEARN MORE" text buttons
   - Proper Material elevation and ripple effects (via :active states)

3. **Chips Section**
   - Row of Material chips (pill-shaped buttons)
   - Categories or tags
   - Example: "Design", "Development", "Marketing", "Analytics"

4. **Navigation Rail** (optional, for desktop)
   - Vertical navigation on the left side
   - Icons with labels
   - Material elevation

5. **Snackbar/Toast Notification**
   - Bottom notification bar
   - Dark background with action button
   - Example: "Settings saved" with "UNDO" action

6. **List with Dividers**
   - Material-style list items
   - Avatar/icon on left, text on right, action on far right
   - 1px dividers between items

7. **Top App Bar with Tabs**
   - Material top bar with tabs underneath
   - Tab indicator (underline) showing active tab
   - Example tabs: "Overview", "Features", "Pricing"

### Microsoft/Fluent Design (microsoft/)
Add these Fluent Design-specific UI patterns:

1. **Acrylic Cards**
   - Translucent/frosted glass effect cards
   - Subtle blur background
   - Light border with shadow

2. **Command Bar**
   - Horizontal toolbar with icon buttons
   - Fluent icons and labels
   - Example: Edit, Share, Delete, More actions

3. **People Cards**
   - Profile cards with circular avatars
   - Microsoft Teams-style layout
   - Status indicator (green dot for online)

4. **Reveal Highlight**
   - Cards that light up on hover
   - Subtle glow/highlight effect
   - Border highlight animation

5. **Pivot Navigation**
   - Horizontal tab navigation
   - Underline moves on selection
   - Similar to Office 365 ribbon tabs

6. **Info Bar**
   - Colored banner for notifications
   - Icon, message, and close button
   - Info (blue), Success (green), Warning (yellow), Error (red)

### IBM Carbon Design (ibm/)
Add these Carbon Design-specific UI patterns:

1. **Data Table**
   - Comprehensive sortable table
   - Zebra striping (alternating row colors)
   - Checkbox column, action column
   - Pagination controls

2. **Progress Indicator**
   - Multi-step progress bar
   - Numbered steps with connecting lines
   - Completed, current, and upcoming states

3. **Tile Component**
   - Square or rectangular tiles in a grid
   - Clickable cards with hover effects
   - Icon, title, and description

4. **Breadcrumb Navigation**
   - Path navigation at top
   - Example: "Home > Products > Features > Details"

5. **Tag System**
   - IBM-style tags for categorization
   - Removable tags with × icon
   - Different colors for different types

6. **Notification Panel**
   - Left-aligned notification list
   - Icon, timestamp, message
   - Unread indicator

### Ant Design (ant/)
Add these Ant Design-specific UI patterns:

1. **Steps Component**
   - Horizontal or vertical step indicator
   - Icons, titles, and descriptions
   - Example: "Sign up → Verify → Complete"

2. **Timeline**
   - Vertical timeline with events
   - Dots connected by line
   - Timestamps and descriptions

3. **Collapse/Accordion**
   - Expandable panels with + / - icons
   - FAQ section format
   - One or multiple panels open

4. **Badge/Tag Collection**
   - Colored badges for status
   - Count indicators
   - Example: "New" badge, "3" notification count

5. **Rate/Review Component**
   - Star rating display
   - Example: ★★★★☆ (4.5/5)

6. **Result Page**
   - Success/error result screen
   - Large icon, title, description, action buttons
   - Example: "✓ Payment Successful"

---

### Implementation Notes:
- Choose 3-4 product-specific components from the list above for each design system
- These components should be IN ADDITION to the required sections
- Place them strategically throughout the page to showcase the design system's unique patterns
- Ensure components follow the exact specifications from DESIGN_RULES.md
- Use appropriate colors, spacing, and typography from the design system
- Make sure the product-specific components are visually distinct and recognizable

### Step 3: Create README.md
Create a simple `README.md` in the directory with:
- Title (e.g., "# Apple Design Rules")
- Demo link: `**[View Demo →](https://htmlpreview.github.io/?https://github.com/tsugumi-sys/design_rules/blob/main/[directory-name]/index.html)**`

### Example Prompt from User:
```
Please generate index.html for [directory-name] based on DESIGN_RULES.md
```

### Directory Structure After Generation:
```
[directory-name]/
├── DESIGN_RULES.md    # User creates this
├── index.html         # Claude generates this
└── README.md          # Claude generates this
```
