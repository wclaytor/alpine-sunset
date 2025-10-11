# 🌅 Alpine Sunset

**Create beautiful, algorithmic sunset visuals with real-time parameter controls** - A stunning demonstration of Alpine.js + HTML Canvas for generative art.

![Alpine Sunset](https://img.shields.io/badge/Alpine.js-3.x-blue) ![HTML Canvas](https://img.shields.io/badge/Canvas-API-orange) ![Progressive Web App](https://img.shields.io/badge/PWA-Ready-green)

[GitHub Pages Live Preview](https://wclaytor.github.io/alpine-sunset/index.html)

## ✨ What is Alpine Sunset?

Alpine Sunset is an interactive web application that generates beautiful sunset scenes using HTML Canvas and Alpine.js. Experiment with colors, mountains, clouds, and celestial bodies to create your perfect sunset visualization.

Built entirely as a standalone HTML file using the [Alpine.js Template](https://github.com/wclaytor/alpine-pwa-template), this app demonstrates the power of combining reactive frameworks with canvas-based generative art.

## 🎨 Features

### 🌄 Sunset Elements
- **Sky Gradients** - Three-color gradient system for realistic skies
- **Sun/Moon** - Adjustable position, size, color, and glow effects
- **Mountains** - 1-5 layers with opacity and height controls
- **Clouds** - Procedurally generated with density and opacity settings
- **Stars** - Dynamic star field for twilight and night scenes

### 🎛️ Interactive Controls
- **6 Preset Scenes** - Golden Hour, Twilight, Desert Sunset, Mountain Majesty, Ocean Dusk, Crimson Sky
- **Real-time Updates** - See changes instantly as you adjust parameters
- **Randomize Button** - Generate unique sunsets with one click
- **Download Feature** - Export your creations as PNG images
- **Persistent State** - Your settings are saved automatically

### 📱 Progressive Web App
- **Install on Mobile/Desktop** - Add to home screen like a native app
- **Works Offline** - No internet required after initial load
- **Single File** - Entire app in one HTML file (~38KB)
- **Responsive Design** - Beautiful on all screen sizes

## 🚀 Quick Start

### Try It Now!
1. **Clone this repository** or download `index.html`
2. **Open index.html** in your web browser
3. **Start creating!** Adjust controls to design your sunset

### Use the App
1. **Select a Preset** - Choose from 6 curated sunset scenes
2. **Adjust Colors** - Fine-tune sky gradient, sun, and mountain colors
3. **Tweak Parameters** - Control sun position, mountain layers, cloud density, etc.
4. **Randomize** - Generate unexpected combinations
5. **Download** - Save your creation as a PNG image

## 🎯 How It Works

Alpine Sunset combines three powerful web technologies:

### Alpine.js for Reactivity
```javascript
// Reactive state management
colors: {
    skyTop: '#1a1a3e',
    skyMiddle: '#ff6b35',
    skyBottom: '#ffd700'
}

// Instant re-rendering on change
@change="render()"

```

### HTML Canvas for Graphics
```javascript
// Render sky with gradient
drawSky(w, h) {
    const gradient = this.ctx.createLinearGradient(0, 0, 0, h);
    gradient.addColorStop(0, this.colors.skyTop);
    gradient.addColorStop(0.5, this.colors.skyMiddle);
    gradient.addColorStop(1, this.colors.skyBottom);
    this.ctx.fillStyle = gradient;
    this.ctx.fillRect(0, 0, w, h);
}
```

### Tailwind CSS for UI
```html
<!-- Beautiful, responsive controls -->
<div class="bg-white rounded-lg shadow-lg p-4">
    <input type="color" x-model="colors.skyTop" @change="render()" 
           class="w-full h-10 rounded border">
</div>
```

## 🎨 Preset Scenes

Alpine Sunset includes 6 carefully crafted preset scenes:

| Preset | Description | Best For |
|--------|-------------|----------|
| **Golden Hour** | Classic warm sunset with orange and gold tones | Traditional sunset vibes |
| **Twilight** | Purple and pink hues with emerging stars | Evening/night transitions |
| **Desert Sunset** | Vibrant oranges and yellows, minimal clouds | Dramatic, high-contrast scenes |
| **Mountain Majesty** | Deep reds with prominent mountain layers | Landscape-focused compositions |
| **Ocean Dusk** | Purple and blue tones, no mountains | Coastal or minimalist scenes |
| **Crimson Sky** | Deep reds and dramatic lighting | Intense, moody atmospheres |

## 📚 Documentation & Resources

- **[index-starter-demo.html](index-starter-demo.html)** - Original Alpine.js template demo
- **[Alpine.js Documentation](https://alpinejs.dev/)** - Official Alpine.js reference
- **[Complete Alpine.js Guide](docs/alpine-guide.md)** - Comprehensive Alpine.js patterns
- **[Copilot Instructions](.github/copilot-instructions.md)** - AI-assisted development guide

## 🛠️ Technical Implementation

### State Management
```javascript
// All parameters stored in reactive Alpine.js state
colors: { skyTop, skyMiddle, skyBottom },
sun: { y, size, color, glow },
mountains: { enabled, layers, height, color },
clouds: { enabled, density, opacity },
stars: { enabled, count }
```

### Rendering Pipeline
1. **Clear Canvas** - Reset the canvas for fresh render
2. **Draw Sky** - Apply three-color gradient
3. **Draw Stars** - If enabled, render star field
4. **Draw Sun** - Render sun/moon with glow effect
5. **Draw Clouds** - Procedurally generate cloud shapes
6. **Draw Mountains** - Layer mountain silhouettes with opacity

### Canvas Techniques Used
- **Linear Gradients** - For sky transitions
- **Radial Gradients** - For sun glow effects
- **Path Drawing** - For mountain ranges
- **Arc Drawing** - For sun, moon, stars, and clouds
- **Global Alpha** - For transparency effects
- **Procedural Generation** - Deterministic cloud positioning

## 💡 Use Cases

### Perfect For
- **Art & Design** - Generate reference images for artists
- **Mood Boards** - Create atmosphere references for projects
- **Screensavers** - Beautiful visuals for displays
- **Education** - Teach canvas programming and color theory
- **Relaxation** - Meditative sunset generation
- **Wallpapers** - Generate custom desktop/mobile backgrounds

### Technical Learning
- **Alpine.js Patterns** - See reactive state management in action
- **Canvas API** - Learn gradient, path, and arc drawing
- **PWA Development** - Understand Progressive Web App setup
- **Color Theory** - Experiment with color combinations
- **Procedural Generation** - Study algorithmic visual creation

## 🔧 Customization

Want to extend Alpine Sunset? Here are some ideas:

### Add New Features
- **Animated Sunsets** - Use `requestAnimationFrame` for moving sun
- **Water Reflections** - Mirror the scene below the horizon
- **Weather Effects** - Rain, snow, or fog layers
- **Foreground Elements** - Trees, buildings, or silhouettes
- **Time Progression** - Animate from day to night

### Modify Rendering
```javascript
// Example: Add a custom gradient
drawCustomGradient(w, h) {
    const gradient = this.ctx.createRadialGradient(
        w/2, h/2, 0,  // Start point
        w/2, h/2, Math.max(w, h)/2  // End point
    );
    gradient.addColorStop(0, this.colors.center);
    gradient.addColorStop(1, this.colors.outer);
    this.ctx.fillStyle = gradient;
    this.ctx.fillRect(0, 0, w, h);
}
```

### Create New Presets
```javascript
'aurora-borealis': {
    colors: {
        skyTop: '#001a33',
        skyMiddle: '#00ff88',
        skyBottom: '#0066ff'
    },
    sun: { y: 70, size: 50, color: '#ffffff', glow: 20 },
    mountains: { enabled: true, layers: 2, height: 30, color: '#001122' },
    clouds: { enabled: false, density: 0, opacity: 0 },
    stars: { enabled: true, count: 200 }
}
```

## 📊 Performance

Alpine Sunset is optimized for smooth performance:

- **Canvas Size**: 1200x800px (scales responsively)
- **File Size**: ~38KB (single HTML file)
- **Load Time**: Instant (all code inline)
- **Render Speed**: < 16ms per frame (60+ FPS capable)
- **Memory Usage**: Minimal (no external dependencies loaded)
- **Browser Support**: All modern browsers (Chrome, Firefox, Safari, Edge)

## 🎓 Learning from Alpine Sunset

This project demonstrates several professional web development patterns:

### Alpine.js Patterns
✅ **Reactive State Management** - All parameters update canvas in real-time  
✅ **Computed Properties** - (Could add for derived values)  
✅ **Event Handling** - `@change`, `@click`, `@input` listeners  
✅ **Lifecycle Hooks** - `x-init` for setup  
✅ **Conditional Rendering** - `x-show` for control visibility  

### Canvas Best Practices
✅ **Clear Before Draw** - Prevent visual artifacts  
✅ **Layered Rendering** - Sky → Stars → Sun → Clouds → Mountains  
✅ **Context State Management** - `.save()` and `.restore()`  
✅ **Gradient Techniques** - Linear and radial gradients  
✅ **Path-based Drawing** - Efficient shape creation  

### PWA Features
✅ **Manifest Generation** - Dynamic manifest creation  
✅ **Icon Conversion** - SVG to PNG for compatibility  
✅ **Offline Support** - Works without internet  
✅ **Mobile Ready** - Responsive and installable  

## 🚀 Deployment

### Option 1: Direct File Access
Simply open `index.html` in any web browser. No server required!

### Option 2: GitHub Pages
1. Fork this repository
2. Enable GitHub Pages in Settings
3. Access at `https://yourusername.github.io/alpine-sunset`

### Option 3: Self-Hosted
Upload `index.html` to any web server. That's it!

## 🎮 Controls Reference

### Preset Scenes Dropdown
Select from 6 pre-configured sunset scenes

### Sky Colors
- **Top Color** - Upper atmosphere color
- **Middle Color** - Horizon/sunset zone color  
- **Horizon Color** - Lower sky/ground color

### Sun/Moon Controls
- **Position Y** (10-70%) - Vertical position on canvas
- **Size** (40-150px) - Diameter of the sun/moon
- **Color** - Sun/moon base color
- **Glow Intensity** (0-100) - Radial glow strength

### Mountains
- **Show Mountains** - Toggle mountain layer visibility
- **Layers** (1-5) - Number of mountain layers
- **Height** (20-60%) - Maximum mountain height
- **Base Color** - Mountain silhouette color

### Clouds
- **Show Clouds** - Toggle cloud layer visibility
- **Density** (5-20) - Number of clouds rendered
- **Opacity** (10-80%) - Cloud transparency

### Stars
- **Show Stars** - Toggle star field visibility
- **Count** (0-200) - Number of stars rendered

### Action Buttons
- **Randomize** - Generate random parameters
- **Download** - Export current scene as PNG

## 🛠️ Built With

- **[Alpine.js 3.x](https://alpinejs.dev/)** - Lightweight reactive framework
- **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **[Bootstrap Icons](https://icons.getbootstrap.com/)** - Open source icon library
- **HTML Canvas API** - 2D graphics rendering
- **LocalStorage API** - State persistence
- **Progressive Web App APIs** - Installable app features

## 🤝 Contributing

Contributions are welcome! Here are some ways you can help:

- 🎨 **Add New Presets** - Create and submit new sunset scenes
- 🐛 **Report Bugs** - Found an issue? Let us know
- 💡 **Suggest Features** - Have an idea? Open an issue
- 📖 **Improve Docs** - Help others understand the code
- 🎓 **Share Use Cases** - Tell us how you're using Alpine Sunset

### How to Contribute
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-preset`)
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📝 Credits

Created using the [Alpine PWA Template](https://github.com/wclaytor/alpine-pwa-template) - a comprehensive template for building standalone Alpine.js applications.

Inspired by the beauty of real sunsets and the power of algorithmic art.

## 📄 License

This project is open source and available for any purpose. No attribution required.

---

**Enjoy creating beautiful sunsets!** 🌅 

*Built with Alpine.js • Powered by Canvas • Designed for Joy*
