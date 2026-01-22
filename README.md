# GitHub Portfolio

A beautiful, responsive portfolio website that showcases all GitHub repositories for the user `harijaiswal29`.

## Features

- 🎨 Modern, gradient-based design
- 📱 Fully responsive (mobile, tablet, desktop)
- 🔍 Real-time search and filtering
- 📊 User profile statistics (repos, followers, following)
- ⭐ Repository details including stars, forks, watchers
- 🏷️ Language badges and topic tags
- 🌐 Direct links to repositories
- ⚡ Fast loading with pagination support
- 🎯 Powered by GitHub API

## Quick Start

Simply open `index.html` in your web browser to view the portfolio.

### Using a local server (recommended):

```bash
# Using Python 3
python -m http.server 8000

# Using Python 2
python -m SimpleHTTPServer 8000

# Using Node.js (if you have http-server installed)
npx http-server
```

Then navigate to `http://localhost:8000` in your browser.

## How It Works

The portfolio uses the GitHub REST API to:
1. Fetch user profile information
2. Retrieve all public repositories
3. Display repository metadata (stars, forks, languages, topics, etc.)
4. Enable real-time search and filtering

## Customization

To customize the portfolio for a different GitHub user, edit the `GITHUB_USERNAME` constant in `index.html`:

```javascript
const GITHUB_USERNAME = 'your-github-username';
```

## Technologies Used

- HTML5
- CSS3 (with modern gradients and flexbox/grid)
- Vanilla JavaScript (ES6+)
- GitHub REST API v3

## Browser Support

Works on all modern browsers:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Opera (latest)

## Live Demo

You can deploy this portfolio to:
- GitHub Pages
- Netlify
- Vercel
- Any static hosting service

## License

This project is open source and available for anyone to use.
