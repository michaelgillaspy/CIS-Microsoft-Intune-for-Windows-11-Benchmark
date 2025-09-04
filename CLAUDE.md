# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a CIS (Center for Internet Security) Benchmark compliance dashboard for Microsoft Intune Windows 11 configurations. The repository contains a static web-based dashboard that displays security recommendations, their implementation status, and detailed compliance information.

## Architecture

### Core Components
- **index.html**: Single-page application that serves as the main dashboard interface
- **Data.json**: Primary compliance data source containing CIS benchmark recommendations with implementation status
- **CIS_Windows_Intune.json**: Legacy data file (appears to be older version of compliance data)

### Data Structure
The JSON data files contain:
- `document_title` and `document_version`: Metadata about the CIS benchmark version
- `recommendations[]`: Array of security controls with fields:
  - `Number`: Control identifier (e.g., "1.1", "4.1.3.1")  
  - `Level`: Security level "(L1)" or "(L2)"
  - `Title`: Human-readable control description
  - `Compliance Status`: Implementation status ("Yes", "No", "Partial", "To Review", etc.)
  - `Reasoning`: Optional explanation for implementation decisions
  - `Description`, `Rationale`, `Impact`: Detailed control information
  - `Audit`, `Remediation`: Technical implementation steps with code blocks
  - `Default Value`, `References`: Additional metadata

### Key Features
- Interactive filtering by security level (L1/L2) and implementation status
- Search functionality across control numbers, titles, and descriptions  
- Modal dialogs showing detailed control information
- Code block copying functionality for audit/remediation steps
- Responsive design for mobile/desktop
- Progress tracking and statistics dashboard

## Development Workflow

This is a client-side only application with no build process:

### Local Development
- Open `index.html` directly in a browser or serve via local web server
- The application auto-detects environment and loads appropriate data source:
  - Local: Uses `./CIS_Windows_Intune.json`  
  - GitHub Pages: Uses `Data.json` from repository

### Data Updates
- Modify `Data.json` to update compliance status or add new recommendations
- Code blocks in audit/remediation steps should use `||CODE||content||CODE||` delimiter format
- Supported compliance statuses: "Yes", "No", "Partial"/"Partially", "To Review", or any other value (treated as "Unknown")

### Deployment
- Static hosting compatible (GitHub Pages, Netlify, etc.)
- No server-side dependencies or build process required
- Files can be opened directly as file:// URLs for local use

## Code Conventions

### JavaScript
- Vanilla JavaScript (no frameworks)
- Event-driven architecture with DOM manipulation
- Async/await for data loading
- Responsive design with CSS Grid/Flexbox

### Data Processing
- Case-insensitive search with punctuation normalization
- Flexible status matching handles variations ("Partial" vs "Partially")  
- Dynamic badge styling based on security levels and status

### Styling
- CSS custom properties for theming
- Component-based CSS organization
- Mobile-first responsive design
- Hover states and smooth transitions throughout