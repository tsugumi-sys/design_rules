# Design Rules for Agents

A collection of design rules from famous applications to help AI agents generate consistent, high-quality landing pages.

## Overview

This project collects and documents design rules from well-known applications and brands. Each design rule set includes:

- Color systems (palettes, hex codes)
- Typography (fonts, sizes, weights)
- Spacing systems (margins, padding)
- Border radius guidelines
- Component specifications (buttons, cards, forms)
- Contrast and accessibility rules

## Current Design Rules

- **Apple** (`apple/DESIGN_RULES.md`) - Based on Apple's Human Interface Guidelines

## Usage

To generate a sample landing page from a design rule set:

```
Please create a sample landing page based on the [brand]/DESIGN_RULES.md in a single HTML file.
```

The generated HTML file will include inline CSS and follow all the design specifications from the chosen design rule set.

## Project Structure

```
design_rules/
├── README.md
├── index.html                    # Sample landing page
├── apple/
│   └── DESIGN_RULES.md          # Apple design guidelines
└── [future brands]/
    └── DESIGN_RULES.md          # Additional design systems
```

## Goals

- Collect design rules from multiple famous applications
- Create reproducible design systems for AI agents
- Generate single HTML file landing pages with consistent design
- Enable rapid prototyping with established design patterns

## Contributing

Feel free to add new design rule sets for other famous applications and brands.
