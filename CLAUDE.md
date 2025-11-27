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
- Implements a simple landing page with:
  - Navigation bar
  - Hero section
  - Features section (3 cards)
  - Showcase section
  - Footer
- All links should be dummy links (`href="#"`)

### Step 3: Create README.md
Create a simple `README.md` in the directory with:
- Title (e.g., "# Apple Design Rules")
- Demo link: `**[View Demo →](https://tsugumi-sys.github.io/design_rules/[directory-name]/)**`

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
