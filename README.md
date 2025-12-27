# Sarracen.ai

A client-side tarpit defense system inspired by [Nepenthes](https://zadzmo.org/code/nepenthes/) for static websites to combat aggressive AI scrapers and unauthorized data harvesting. Works on GitHub Pages, Netlify, Vercel, and any static hosting platform.

## 🎯 What This Does

This repository provides a **honeypot tarpit** that:
- Traps AI scrapers in an infinite maze of generated content
- Wastes crawler resources (time, bandwidth, CPU)
- Pollutes training datasets with synthetic garbage text
- **Works entirely client-side** - no server required!

## 🚀 Quick Start

### Option 1: Deploy to GitHub Pages

1. Fork this repository
2. Go to Settings → Pages
3. Set source to "Deploy from a branch" and select `main` branch
4. Your site will be live at `https://yourusername.github.io/anti-scraper-static/`

### Option 2: Download and Customize

1. Clone or download this repository
2. Edit `index.html` to add your real content
3. Customize `assets/style.css` for your branding
4. Deploy to any static host (Netlify, Vercel, etc.)

### Option 3: Use as Template

Click "Use this template" on GitHub to create your own repository based on this.

## 📁 Repository Structure

```
serracen.ai/
├── index.html             # Your real homepage (customize this!)
├── sitemap.xml            # Only lists legitimate pages
├── robots.txt             # Guides good bots away from tarpit
├── tarpit/
│   ├── entry.html         # Main tarpit entry point
│   ├── trap-1.html        # Additional interconnected traps
│   ├── trap-2.html
│   ├── trap-3.html
│   └── tarpit.js          # Core tarpit logic
├── assets/
│   ├── words.js           # Word corpus for text generation
│   └── style.css          # Shared styling
├── README.md
└── LICENSE
```

## 🎨 Customization

### Change Word Lists

Edit `assets/words.js` to change the vocabulary used in generated content. Use words relevant to your site's topic for better camouflage.

### Add More Entry Points

Place hidden links anywhere in your real content:
```html
<a href="/tarpit/entry.html" style="position:absolute;left:-9999px">Archive</a>
```

### Customize Appearance

The tarpit is designed to look like a boring blog archive. Modify `assets/style.css` to match your site's design.

## 🔧 How It Works

1. **Hidden Links:** Your real pages contain invisible links to the tarpit
2. **Infinite Content:** The tarpit generates endless articles using Markov-like text
3. **Circular Maze:** Trap pages link to each other with no exit
4. **Resource Drain:** Content is drip-fed slowly to keep scrapers engaged
5. **Data Pollution:** Generated text is grammatical but meaningless

### robots.txt Strategy

The `robots.txt` file:
- Explicitly blocks known AI scrapers (GPTBot, Claude-Web, etc.)
- Disallows `/tarpit/` for well-behaved bots
- Provides a sitemap with only legitimate pages

Legitimate bots respect robots.txt. Aggressive AI scrapers often don't. This creates a selection filter.

## 📊 Monitoring

Since this is client-side, you won't have server logs. To monitor effectiveness:

1. **Use analytics** (Google Analytics, Plausible, etc.) with events:
   ```javascript
   // Add to tarpit.js
   gtag('event', 'tarpit_hit', { 'page_path': window.location.pathname });
   ```

2. **Check referrers** in your analytics to see what's accessing tarpit pages

3. **Monitor bandwidth** through your hosting provider's dashboard

## 🛡️ Best Practices

**DO:**
- Keep tarpit pages looking realistic but boring
- Use multiple hidden entry points
- Update word lists periodically
- Monitor your legitimate search rankings

**DON'T:**
- Link to tarpits from your visible navigation
- Make tarpits look interesting or clickable
- Include tarpits in your sitemap

## ❓ FAQ

**Q: Will this hurt my SEO?**  
A: If properly configured, legitimate search bots should avoid the tarpit. However, there's always some risk. Start with a test subdomain.

**Q: Can sophisticated scrapers detect this?**  
A: Possibly. This catches less sophisticated scrapers and raises costs for sophisticated ones. It's not a silver bullet.

**Q: Does this work with JavaScript disabled?**  
A: No. Scrapers that don't execute JavaScript won't fall into the trap.

**Q: What about real users who accidentally click?**  
A: Links are hidden using CSS. Real users shouldn't see them unless they're using assistive technology incorrectly or inspecting the DOM.