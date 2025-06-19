

# LinkedIn Company Data Extractor

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)

A powerful, client-side web application that extracts comprehensive company information from LinkedIn company pages and displays it in a clean, structured JSON format. Built with vanilla HTML, CSS, and JavaScript - no dependencies required.

## 🚀 Features

- **Complete Company Profile Extraction**
  - Company name, industry, and location details
  - Follower count and employee information
  - Website URL and company type
  - Comprehensive company description

- **Image Extraction**
  - Company logo/profile image URL
  - Cover/banner image URL
  - Visual preview of extracted images

- **Advanced Data Mining**
  - Automatic service detection from company descriptions
  - Partner/technology stack identification
  - Recent posts preview (up to 3 posts)
  - Structured location data (city, region, country)

- **User-Friendly Interface**
  - Clean, modern UI with LinkedIn-inspired design
  - Real-time data extraction with loading indicators
  - One-click JSON copy to clipboard
  - Syntax-highlighted JSON output

- **Technical Features**
  - CORS proxy integration for cross-origin requests
  - Multiple fallback selectors for robust data extraction
  - JSON-LD structured data parsing
  - Comprehensive error handling

## 📸 Screenshots

### Main Interface
![Main Interface]([https://raw.githubusercontent.com/roeiredlerabra/LinkedIn-Company-Data-Extractor/refs/heads/main/img/iPad-PRO-11-roeiredlerabra.github.io.png])



## 🛠️ Installation

### Quick Start (No Installation Required)

1. **Download the HTML file:**
   ```bash
   git clone https://github.com/roeiredlerabra/linkedin-company-extractor.git
   cd linkedin-company-extractor
   ```

2. **Open in browser:**
   - Simply open `index.html` in any modern web browser
   - Or serve it locally using a simple HTTP server:
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Node.js (with http-server)
   npx http-server
   
   # PHP
   php -S localhost:8000
   ```

3. **Access the application:**
   - Open your browser and navigate to `http://localhost:8000`

### Alternative Deployment Options

#### GitHub Pages
1. Fork this repository
2. Go to Settings → Pages
3. Select source branch (usually `main`)
4. Access via `https://roeiredlerabra.github.io/linkedin-company-extractor`

#### Netlify
1. Drag and drop the HTML file to [Netlify Drop](https://app.netlify.com/drop)
2. Get instant deployment with custom URL

#### Vercel
1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in the project directory
3. Follow the deployment prompts

## 📖 Usage Guide

### ⚡ Quick Setup (IMPORTANT)

**Before using the extractor, you MUST enable CORS proxy access:**

1. **Enable CORS Proxy Access:**
   - Visit: [cors-anywhere.herokuapp.com/corsdemo](https://cors-anywhere.herokuapp.com/corsdemo)
   - Click "Request temporary access to the demo server" button
   - This enables access for a limited time (usually 1 hour)

2. **Alternative CORS Solutions:**
   - Use your own CORS proxy server
   - Deploy a browser extension version
   - Use server-side implementation

### Basic Usage

1. **Enter LinkedIn Company URL:**
   ```
   https://il.linkedin.com/company/company-name
   ```

2. **Configure Options:**
   - ✅ Enable "Use CORS proxy" for best results
   - The default proxy (cors-anywhere.herokuapp.com) should work after enabling access

3. **Extract Data:**
   - Click "Extract Data" button
   - Wait for the extraction to complete
   - View results in JSON format with image previews

4. **Copy Results:**
   - Use the "📋 Copy" button to copy JSON to clipboard
   - Paste into your preferred text editor or application

### Supported URL Formats

```bash
# Standard LinkedIn company URLs
https://www.linkedin.com/company/company-name
https://linkedin.com/company/company-name
https://il.linkedin.com/company/company-name

# URLs with additional parameters (will be cleaned automatically)
https://www.linkedin.com/company/company-name/about/
https://www.linkedin.com/company/company-name?trk=...
```

### Example Output

```json
{
  "companyName": "linkedin-company",
  "industry": "Information Technology & Services",
  "location": {
    "full": "Ra'anana, Central, Israel",
    "city": "Ra'anana",
    "region": "Central", 
    "country": "Israel"
  },
  "followers": 22894,
  "employeeCount": "1,001-5,000 employees",
  "website": "https://www.linkedin-company-it.com/",
  "companyType": "Public Company",
  "description": "linkedin-company is composed of over 1,000 experts...",
  "images": {
    "profileImageUrl": "https://media.licdn.com/dms/image/...",
    "coverImageUrl": "https://media.licdn.com/dms/image/..."
  },
  "services": ["BI", "AI", "ERP", "CRM", "Cyber", "Cloud"],
  "partners": ["Microsoft", "Salesforce", "SAP", "Oracle"],
  "recentPosts": [...],
  "extractedAt": "2025-01-09T10:30:00.000Z",
  "sourceUrl": "https://il.linkedin.com/company/linkedin-company-it"
}
```

## 🔧 Technical Details

### Architecture

The application uses a pure client-side architecture:

```
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│   User Input    │ →  │ CORS Proxy   │ →  │ LinkedIn Page   │
└─────────────────┘    └──────────────┘    └─────────────────┘
                                                    ↓
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│  JSON Output    │ ←  │ Data Parser  │ ←  │   HTML Parser   │
└─────────────────┘    └──────────────┘    └─────────────────┘
```

### Data Extraction Methods

1. **DOM Selectors:** Multiple CSS selectors for robust element detection
2. **Regex Patterns:** Fallback extraction using regular expressions
3. **Structured Data:** JSON-LD parsing for semantic information
4. **Image Detection:** Multiple strategies for logo and cover image URLs

### Browser Compatibility

| Browser | Version | Status |
|---------|---------|--------|
| Chrome  | 60+     | ✅ Full Support |
| Firefox | 55+     | ✅ Full Support |
| Safari  | 12+     | ✅ Full Support |
| Edge    | 79+     | ✅ Full Support |
| Opera   | 47+     | ✅ Full Support |

### Performance

- **Average extraction time:** 2-5 seconds
- **Data size:** Typically 2-10KB JSON output
- **Memory usage:** < 50MB during extraction
- **Network requests:** 1 request per extraction

## ⚠️ Limitations & Considerations

### CORS (Cross-Origin Resource Sharing)

**Problem:** Browsers block direct requests to LinkedIn due to CORS policy.

**Solutions:**
1. **CORS Proxy (Default):** Uses cors-anywhere.herokuapp.com
   - **🚨 REQUIRED:** Visit [cors-anywhere.herokuapp.com/corsdemo](https://cors-anywhere.herokuapp.com/corsdemo) and click "Request temporary access"
   - Access expires after ~1 hour and needs to be renewed
2. **Browser Extension:** Create extension with proper permissions
3. **Server-side Proxy:** Host your own CORS proxy
4. **Local Development:** Disable browser security (not recommended for production)

### Rate Limiting

- **Proxy Limitations:** Free CORS proxies may have rate limits
- **LinkedIn Protection:** LinkedIn may block excessive requests
- **Recommendation:** Use responsibly with reasonable delays between requests

### Data Accuracy

- **Page Structure Changes:** LinkedIn may update their HTML structure
- **Dynamic Content:** Some content may be loaded via JavaScript
- **Localization:** Different regions may have different layouts
- **Access Restrictions:** Some company pages may require login

### Legal Considerations

⚖️ **Important:** This tool is for educational and research purposes only.

- **LinkedIn Terms of Service:** Review LinkedIn's ToS before extensive use
- **Rate Limiting:** Respect LinkedIn's servers and implement appropriate delays
- **Data Usage:** Ensure compliance with data protection regulations (GDPR, CCPA)
- **Commercial Use:** Consider LinkedIn's official API for business applications

## 🔄 Alternative Solutions

### 1. Browser Extension Approach

```javascript
// manifest.json
{
  "manifest_version": 3,
  "permissions": ["activeTab", "*://linkedin.com/*"]
}
```

**Pros:** No CORS issues, direct page access
**Cons:** Requires extension installation

### 2. Server-side Solution

```python
# Python example with requests + BeautifulSoup
import requests
from bs4 import BeautifulSoup

def extract_linkedin_data(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    # Extract data logic
```

**Pros:** No browser restrictions, better reliability
**Cons:** Requires server infrastructure

### 3. Headless Browser Automation

```javascript
// Puppeteer example
const puppeteer = require('puppeteer');

async function extractData(url) {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto(url);
  // Extraction logic
}
```

**Pros:** Handles JavaScript, identical to real browser
**Cons:** Resource intensive, slower

### 4. Official LinkedIn API

```javascript
// LinkedIn API (requires authentication)
const response = await fetch('https://api.linkedin.com/v2/organizations/{id}', {
  headers: { 'Authorization': 'Bearer ' + accessToken }
});
```

**Pros:** Official, reliable, structured data
**Cons:** Requires API access, limited free tier

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

### Development Setup

1. **Fork the repository**
2. **Clone your fork:**
   ```bash
   git clone https://github.com/roeiredlerabra/linkedin-company-extractor.git
   ```
3. **Create a feature branch:**
   ```bash
   git checkout -b feature/amazing-feature
   ```
4. **Make your changes**
5. **Test thoroughly**
6. **Submit a pull request**

### Code Style

- Use 2 spaces for indentation
- Follow existing naming conventions
- Add comments for complex logic
- Ensure browser compatibility

### What We're Looking For

- 🐛 Bug fixes and error handling improvements
- 🎨 UI/UX enhancements
- 🔧 Additional data extraction methods
- 📱 Mobile responsiveness improvements
- 🌍 Internationalization support
- ⚡ Performance optimizations

### Testing

Before submitting:

1. Test with multiple LinkedIn company pages
2. Verify cross-browser compatibility
3. Check mobile responsiveness
4. Validate JSON output structure

## 🐛 Troubleshooting

### Common Issues

#### CORS Error
```
Access to fetch at 'https://linkedin.com/...' has been blocked by CORS policy
```

**Solutions:**
- 🚨 **FIRST:** Visit [cors-anywhere.herokuapp.com/corsdemo](https://cors-anywhere.herokuapp.com/corsdemo) and click "Request temporary access to the demo server"
- ✅ Enable "Use CORS proxy" option in the tool
- Try alternative proxy services
- Use browser extension version

#### CORS Demo Access Required
```
Access to demo server has been blocked by CORS policy
```

**Solutions:**
- Visit: [cors-anywhere.herokuapp.com/corsdemo](https://cors-anywhere.herokuapp.com/corsdemo)
- Click the "Request temporary access to the demo server" button
- Access is granted for approximately 1 hour
- Repeat this process when access expires

#### Proxy Timeout
```
Failed to extract data: Network timeout
```

**Solutions:**
- Refresh and try again
- Check internet connection
- Try different LinkedIn URL
- Ensure CORS demo access is still active

#### Empty Results
```
Some fields returning null or empty
```

**Solutions:**
- LinkedIn may have changed their structure
- Try different company pages
- Check if page requires login

#### Rate Limiting
```
HTTP 429: Too Many Requests
```

**Solutions:**
- Wait before making another request
- Use different proxy service
- Implement delays between requests

### Debug Mode

Enable debug mode by adding `?debug=true` to URL:
```
file:///path/to/index.html?debug=true
```

This will show additional console logging for troubleshooting.

## 📋 Data Schema

### Complete JSON Structure

```typescript
interface CompanyData {
  companyName: string | null;
  industry: string | null;
  location: {
    full: string | null;
    city: string | null;
    region: string | null;
    country: string | null;
  } | null;
  followers: number | null;
  employeeCount: string | null;
  website: string | null;
  companyType: string | null;
  description: string | null;
  images: {
    profileImageUrl: string | null;
    coverImageUrl: string | null;
  };
  services: string[];
  partners: string[];
  recentPosts: Array<{
    preview: string;
    fullText: string;
  }>;
  extractedAt: string; // ISO 8601 timestamp
  sourceUrl: string;
}
```

### Field Descriptions

| Field | Type | Description |
|-------|------|-------------|
| `companyName` | `string` | Official company name |
| `industry` | `string` | Business industry/sector |
| `location.full` | `string` | Complete location string |
| `location.city` | `string` | City name |
| `location.region` | `string` | State/region |
| `location.country` | `string` | Country name |
| `followers` | `number` | LinkedIn follower count |
| `employeeCount` | `string` | Employee range (e.g., "1,001-5,000") |
| `website` | `string` | Company website URL |
| `companyType` | `string` | Organization type |
| `description` | `string` | Company description |
| `images.profileImageUrl` | `string` | Company logo URL |
| `images.coverImageUrl` | `string` | Cover image URL |
| `services` | `string[]` | Detected services/technologies |
| `partners` | `string[]` | Detected partners |
| `recentPosts` | `object[]` | Recent LinkedIn posts |
| `extractedAt` | `string` | Extraction timestamp |
| `sourceUrl` | `string` | Original LinkedIn URL |

## 🔒 Security & Privacy

### Data Handling

- **No Data Storage:** All processing happens client-side
- **No Tracking:** No analytics or user tracking
- **No API Keys:** No authentication required
- **Local Processing:** Data never leaves your browser

### Proxy Security

When using CORS proxy:
- Data passes through third-party service
- Use HTTPS proxies when possible
- Consider hosting your own proxy for sensitive use cases

### Best Practices

1. **Use Official APIs** for production applications
2. **Implement Rate Limiting** to be respectful
3. **Cache Results** to minimize requests
4. **Review LinkedIn ToS** regularly

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 LinkedIn Company Data Extractor

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

## 📞 Support

### Getting Help

- 🐛 **Bug Reports:** [Open an issue](https://github.com/roeiredlerabra/linkedin-company-extractor/issues)
- 💡 **Feature Requests:** [Start a discussion](https://github.com/roeiredlerabra/linkedin-company-extractor/discussions)
- 📧 **Email:** your.email@example.com
- 💬 **Discord:** [Join our community](https://discord.gg/your-server)

### FAQ

**Q: Can I use this for commercial purposes?**
A: Yes, under MIT license, but respect LinkedIn's ToS and consider their official API.

**Q: Why are some fields empty?**
A: LinkedIn's page structure varies, or the company may not have provided that information.

**Q: Is this against LinkedIn's Terms of Service?**
A: This tool is for educational purposes. Review LinkedIn's ToS for your specific use case.

**Q: Can I extract data from private company pages?**
A: No, this only works with publicly accessible company pages.

**Q: The CORS proxy isn't working, what should I do?**
A: First visit [cors-anywhere.herokuapp.com/corsdemo](https://cors-anywhere.herokuapp.com/corsdemo) and enable temporary access. This needs to be done approximately every hour.

---

⭐ **Star this repository** if you find it useful!

🔗 **Share with others** who might benefit from this tool!

📝 **Contribute** to make it even better!

---

*Disclaimer: This tool is not affiliated with or endorsed by LinkedIn Corporation. LinkedIn is a trademark of LinkedIn Corporation. Use responsibly and in accordance with LinkedIn's Terms of Service.*
