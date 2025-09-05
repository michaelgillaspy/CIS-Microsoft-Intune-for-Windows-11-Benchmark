# CIS Microsoft Intune for Windows 11 Benchmark Dashboard

A web-based compliance dashboard for tracking and monitoring CIS (Center for Internet Security) benchmark implementation status for Microsoft Intune Windows 11 configurations.

## Overview

This repository provides an interactive, single-page dashboard that displays CIS benchmark security recommendations, their implementation status, and detailed compliance information. The dashboard automatically pulls data from the repository and provides real-time filtering and search capabilities.

## Features

- **Interactive Dashboard**: Visual representation of compliance status with color-coded indicators
- **Dual-Level Tracking**: Separate tracking for Level 1 (L1) and Level 2 (L2) security controls
- **Real-Time Filtering**: Filter by security level and implementation status
- **Search Functionality**: Search across control numbers, titles, and descriptions
- **Detailed Views**: Modal dialogs with comprehensive control information including:
  - Description and rationale
  - Implementation impact
  - Audit procedures with code blocks
  - Remediation steps
- **Export Capability**: Export compliance data to CSV format
- **Responsive Design**: Mobile and desktop compatible interface
- **Auto-Configuration**: Automatically detects GitHub repository information from URL

## Live Demo

Access the dashboard at: `https://[username].github.io/[repository-name]/`

Example: https://michaelgillaspy.github.io/CIS-Microsoft-Intune-for-Windows-11-Benchmark/

## Implementation Status Categories

- **Implemented** (Green): Control is fully implemented
- **Not Implemented** (Red): Control is not implemented  
- **Partially Implemented** (Orange): Control is partially implemented
- **To Review** (Yellow): Control needs review
- **Unknown** (Gray): Implementation status is unclear or not documented

## Data Structure

The dashboard reads from `Data.json` which contains:

```json
{
  "document_title": "CIS Benchmark Title",
  "document_version": "Version Number",
  "recommendations": [
    {
      "Number": "1.1",
      "Level": "(L1)",
      "Title": "Control Title",
      "Compliance Status": "Implemented/Not Implemented/Partially Implemented/To Review",
      "Reasoning": "Optional explanation",
      "Description": "Detailed description",
      "Rationale": "Security rationale", 
      "Impact": "Implementation impact",
      "Audit": "Audit procedures with ||CODE||code blocks||CODE||",
      "Remediation": "Remediation steps",
      "Default Value": "Default configuration",
      "References": "Additional references"
    }
  ]
}
```

## Setup and Deployment

### Quick Start

1. **Fork or Clone** this repository
2. **Update Data**: Modify `Data.json` with your compliance data
3. **Enable GitHub Pages**: 
   - Go to Settings → Pages
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Save

### Local Development

```bash
# Clone the repository
git clone https://github.com/[username]/CIS-Microsoft-Intune-for-Windows-11-Benchmark.git

# Navigate to directory
cd CIS-Microsoft-Intune-for-Windows-11-Benchmark

# Open in browser (no build process required)
open index.html

# Or serve with a local web server
python -m http.server 8000
# Then navigate to http://localhost:8000
```

## Creating Additional Benchmark Dashboards

This dashboard is designed to be easily reusable for other CIS benchmarks:

1. **Create a new repository** for each benchmark (e.g., `CIS-Microsoft-365-Benchmark`)
2. **Copy `index.html`** to the new repository
3. **Add your `Data.json`** with the specific benchmark data
4. **Enable GitHub Pages** - the dashboard auto-detects repository information

No configuration changes needed - the dashboard automatically detects:
- GitHub username from the URL
- Repository name from the URL
- Builds the correct data source URL

## Data Format Notes

### Code Blocks
Use the delimiter format for code blocks in audit/remediation sections:
```
||CODE||Your code here||CODE||
```

### Compliance Status Values
Supported values:
- "Yes" or "Implemented" → Shows as Implemented
- "No" or "Not Implemented" → Shows as Not Implemented
- "Partial", "Partially", or "Partially Implemented" → Shows as Partially Implemented
- "To Review" → Shows as To Review
- Any other value → Shows as Unknown

## Browser Compatibility

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Technologies Used

- Pure HTML/CSS/JavaScript (no framework dependencies)
- No build process required
- No server-side dependencies
- GitHub Pages compatible

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- CIS (Center for Internet Security) for benchmark standards
- Microsoft for Intune documentation and guidelines

## Support

For issues, questions, or suggestions, please [open an issue](https://github.com/michaelgillaspy/CIS-Microsoft-Intune-for-Windows-11-Benchmark/issues) in the repository.