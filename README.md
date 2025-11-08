# Developer Portfolio

A modern, responsive developer portfolio built with React and Vite, designed to showcase developer expertise through a professional and engaging interface.

## Portfolio Features

### **Core Portfolio Sections**
- **Home**: Professional introduction with dynamic typing animation
- **About**: Comprehensive developer bio and personal branding
- **Skills**: Interactive technologies showcase with skill tags
- **Projects**: Project portfolio with GitHub repositories and live demos
- **Blog**: Technical articles demonstrating knowledge sharing
- **Contact**: Professional contact form with validation and feedback

### **Design & UX**
- **Modern Gradient Design**: Purple and blue gradient theme with professional styling
- **Smooth Animations**: Hover effects and transitions
- **Fully Responsive**: Mobile-first design optimized for all devices
- **Interactive Elements**: Engaging user interface with smooth scrolling navigation
- **Professional Presentation**: Clean, modern layout focused on showcasing developer work

## Table of Contents

- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Development](#development)
- [Project Structure](#project-structure)
- [Features](#features)
- [API Integration](#api-integration)
- [Customization](#customization)

---

## Tech Stack

- **Framework**: React 18.2
- **Build Tool**: Vite 7.1
- **Styling**: Pure CSS with CSS Variables
- **Icons**: Lucide React
- **Language**: JavaScript (ES6+)
- **Security**: HTTPS with SSL integration

---

## Prerequisites

Before you begin, ensure you have:

- **Node.js** (v16.0.0 or higher) - [Download here](https://nodejs.org/)
- **npm** package manager
- **Backend Server** running on `https://localhost:3000` (see backend README)

---

## Installation

### Step 1: Navigate to Frontend Directory

```bash
cd frontend
```

### Step 2: Install Dependencies

Using npm:
```bash
npm install
```

This will install:
- React and React DOM
- Vite and related plugins
- Lucide React (for icons)
- ESLint (for code quality)

---

## Development

### Start Development Server

```bash
npm run dev
```

The application will open automatically at `http://localhost:5173`


## Project Structure

```
frontend/
├── public/               # Static assets
│   └── dev_logo.png     # Portfolio logo
│   └── dev_logo.ico     # Portfolio icon
├── src/
│   ├── App.jsx          # Main application component
│   ├── main.jsx         # Application entry point
│   ├── index.css        # Global styles and variables
│   └── pages/           # Portfolio sections
│       ├── Home/        # Landing page with introduction
│       ├── About/       # Developer bio and personal brand
│       ├── Skills/      # Technologies and expertise showcase
│       ├── Projects/    # Project portfolio with GitHub links
│       ├── Blog/        # Technical articles and tutorials
│       └── Contact/     # Professional contact form
├── .env                 # Environment configuration
├── package.json         # Dependencies and scripts
└── vite.config.js       # HTTPS and SSL configuration
├── index.html           # HTML template
├── vite.config.js       # Vite configuration
├── .eslintrc.cjs        # ESLint configuration
└── README.md            # This file
```

## Portfolio Features

### **Professional Sections**
- **Home**: Dynamic introduction with typing animation and clear value proposition
- **About**: Comprehensive developer bio showcasing expertise and personal branding
- **Skills**: Interactive technology showcase with skill tags and expertise areas
- **Projects**: Project portfolio with descriptions, GitHub repos, and live demos
- **Blog**: Technical articles demonstrating knowledge sharing and industry insights
- **Contact**: Professional contact form 

### **Technical Implementation**
- **HTTPS Integration**: Secure communication with SSL-enabled backend
- **Responsive Design**: Mobile-first approach optimized for all devices
- **Modern UI**: Clean, professional design with gradient themes
- **Performance**: Optimized loading and smooth navigation
- **API Integration**: Dynamic content loading from secure backend
---

## Features

### 1. Hero Section
- Gradient text effects
- Social media links (GitHub, LinkedIn)
- Call-to-action button

### 2. About Section
- Skills showcase with animated tags
- Feature cards highlighting expertise
- Responsive grid layout

### 3. Projects Section
- Project cards with hover effects
- Technology tags
- Links to live demos and GitHub repos
- Glassmorphism card design

### 4. Blog Section
- Blog post previews
- Publication dates
- Tag system
- Smooth hover animations

### 5. Contact Section
- Contact form with validation
- Success/error status messages
- Secure API integration
- Form field validation

### 6. Navigation
- Navigation bar
- Active section highlighting
- Mobile-responsive hamburger menu

---

## API Integration

The frontend connects to the secure HTTPS backend at `https://localhost:3000`

### API Endpoints Used

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/profile` | GET | Fetch developer profile data |
| `/projects` | GET | Fetch all projects |
| `/posts` | GET | Fetch all blog posts |
| `/contact` | POST | Submit contact form |

### Handling Self-Signed Certificates

During development with self-signed SSL certificates, you may encounter CORS or certificate errors.

**Solutions**:

1. **Accept Certificate in Browser**:
   - Visit `https://localhost:3000` directly
   - Accept the security warning
   - Then use the frontend

2. **Use HTTPS Proxy** (Recommended):
   - Configure Vite proxy in `vite.config.js`:
   ```javascript
   server: {
     proxy: {
       '/api': {
         target: 'https://localhost:3000',
         secure: false,
         changeOrigin: true,
         rewrite: (path) => path.replace(/^\/api/, '')
       }
     }
   }
   ```

3. **Development Mode Fallback**:
   - The app includes fallback mock data
   - If API fails, mock data displays automatically

### CORS Configuration

Ensure your backend has CORS enabled for frontend origin:

```javascript
// In backend server.js
const cors = require('cors');
app.use(cors({
  origin: 'http://localhost:5173',
  credentials: true
}));
```

---

## Customization

### Modify Content

Edit `src/App.jsx` to change:
- Profile information
- Project details
- Blog posts
- Contact form fields

### Update Styles

Modify `src/index.css` for:
- Custom animations
- Global styles
- Font families

### Add New Sections

1. Create section in `App.jsx`:
```javascript
<section id="new-section" className="min-h-screen py-20 px-4">
  {/* Your content */}
</section>
```

2. Add to navigation array:
```javascript
{['home', 'about', 'projects', 'blog', 'contact'].map(...)}
```

---

## Security Considerations

### Content Security Policy

The `index.html` includes CSP meta tags. 

### API Security

- ✅ All API calls use HTTPS
- ✅ No sensitive data stored in frontend
- ✅ Contact form validates input
- ✅ CORS properly configured

### Best Practices Implemented

- Environment variables for API URLs (use `.env`)
- Input sanitization on contact form
- No inline JavaScript in HTML
- Secure external links (`rel="noopener noreferrer"`)

---

## Environment Variables

Create `.env`:
Update this to backend URL
```
VITE_API_BASE_URL=https://localhost:3000
```

Update API URL in `App.jsx`:
```javascript
const API_BASE_URL = import.meta.env.VITE_API_BASE_URL || 'https://localhost:3000';
```
Environment
VITE_ENV=development

---

## Testing & Troubleshooting

### API Connection Errors

**Problem**: `Failed to fetch` or CORS errors

**Solutions**:
1. Ensure backend server is running on `https://localhost:3000`
2. Accept the self-signed certificate in browser
3. Check CORS configuration in backend
4. Verify firewall isn't blocking port 3000


### Mobile Menu Not Working

**Problem**: Hamburger menu doesn't open

**Solution**: Check that JavaScript is enabled and no console errors exist. Clear browser cache and hard reload.

---

## Responsive Design Features

- Stack layout on mobile
- Grid layout on desktop
- Collapsible navigation menu
- Touch-friendly button sizes

---

## Accessibility Features

### Implemented Features

- ✅ Semantic HTML5 elements
- ✅ ARIA labels where needed
- ✅ Keyboard navigation support
- ✅ Focus indicators on interactive elements
- ✅ Color contrast meets WCAG AA standards
- ✅ Alt text for images (when applicable)
- ✅ Screen reader friendly navigation

---

## License

This project is created for educational purposes as part of Web Security Course - Phase 1.

---

## Author

**Developer Portfolio Project**  
Created as part of Web Security Course

---

## Design Choices Explained

### Color Palette

- **Primary Purple (#7c3aed)**: Modern, professional, tech-oriented
- **Accent Blue (#1d4ed8)**: Adds cool and visual interest
- **Dark Background (#0f172a)**: Reduces eye strain, looks premium
- **Gradient Effects**: Creates depth and modern aesthetic

### Typography

- System fonts for fast loading
- Large headings for impact
- Readable body text (16px+)
- Proper line height for readability

### Layout

- **Max-width containers**: Improves readability on large screens
- **Generous spacing**: Breathing room between sections
- **Grid layouts**: Organized, scannable content
- **Full-height sections**: Creates distinct content blocks

### Animations

- **Subtle hover effects**: Provides feedback without distraction
- **Smooth transitions**: Professional polish
- **Scale transforms**: Adds depth on interaction
- **Gradient animations**: Eye-catching hero section

---

## Quick Start Summary

```bash
# 1. Navigate to frontend directory
cd frontend

# 2. Install dependencies
npm install

# 3. Start development server
npm run dev

# 4. Open browser to http://localhost:5173

# 5. Ensure backend is running at https://localhost:3000

# 6. Accept self-signed certificate warnings

# 7. Enjoy your portfolio!
```

---

**Note** 

For backend setup, see the main project README.md in the parent directory.
