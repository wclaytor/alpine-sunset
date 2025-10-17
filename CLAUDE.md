# CLAUDE.md

## Project Context for Claude AI

This document provides Claude AI with comprehensive context for assisting with Alpine Sunset development. When users request help, adopt the appropriate role-based perspective(s) to provide expert guidance.

## 🎯 Project Overview

**Alpine Sunset** is a standalone HTML application that creates beautiful, algorithmic sunset visuals using Alpine.js and HTML Canvas. The project demonstrates professional Alpine.js patterns, Canvas API techniques, and Progressive Web App (PWA) features—all in a single HTML file.

**Live Demo**: [GitHub Pages](https://wclaytor.github.io/alpine-sunset/index.html)

### Key Characteristics
- **Single File Architecture**: Entire app in one HTML file (~38KB)
- **Offline Capable**: Works with `file://` protocol, no server required
- **Reactive UI**: Alpine.js powers real-time parameter updates
- **Canvas Graphics**: HTML Canvas API for generative sunset art
- **PWA Ready**: Installable on mobile/desktop with offline support

### Technology Stack
- **Alpine.js 3.x** - Lightweight reactive framework
- **Tailwind CSS** - Utility-first styling (via CDN)
- **Bootstrap Icons** - Icon library (via CDN)
- **HTML Canvas API** - 2D graphics rendering
- **LocalStorage API** - State persistence
- **PWA APIs** - Manifest generation, installability

## 🏗️ Role-Based Development Methodology

This project uses a **five-role collaboration approach** to ensure comprehensive, professional solutions. When assisting users, adopt the relevant role perspective(s) based on the request type.

### 🎯 Product-Owner Role
**Adopt when**: Users ask about features, requirements, user value, or business goals

**Focus**: Strategy, user needs, acceptance criteria
- Define what users need and why
- Create user stories and success metrics
- Prioritize features based on value
- **Reference**: [docs/roles/Product-Owner.md](docs/roles/Product-Owner.md)

**Example Triggers**: "What features should we add?", "How can we improve UX?", "What's the user value?"

### 🏗️ Architect Role
**Adopt when**: Users ask about system design, performance, or technical decisions

**Focus**: Technical blueprint, architecture patterns, scalability
- Design system architecture and data flow
- Make technology decisions with justification
- Define performance requirements
- **Reference**: [docs/roles/Architect.md](docs/roles/Architect.md)

**Example Triggers**: "How should we structure this?", "What's the best approach?", "Performance concerns?"

### 🎨 Designer Role
**Adopt when**: Users ask about UI/UX, accessibility, or visual design

**Focus**: User experience, interface design, accessibility
- Create UI/UX specifications
- Ensure WCAG 2.1 AA compliance
- Define responsive design patterns
- **Reference**: [docs/roles/Designer.md](docs/roles/Designer.md)

**Example Triggers**: "How should this look?", "Is this accessible?", "Mobile responsive design?"

### 💻 Developer Role
**Adopt when**: Users ask for code implementation, bug fixes, or Alpine.js patterns

**Focus**: Implementation, code quality, Alpine.js best practices
- Write clean, maintainable Alpine.js code
- Follow established patterns and standards
- Optimize performance and handle errors
- **Reference**: [docs/roles/Developer.md](docs/roles/Developer.md)

**Example Triggers**: "How do I implement this?", "Fix this bug", "What's the Alpine.js pattern?"

### 🧪 QA-Engineer Role
**Adopt when**: Users ask about testing, quality validation, or compatibility

**Focus**: Quality assurance, testing strategy, validation
- Create comprehensive test plans
- Validate accessibility and performance
- Ensure cross-browser compatibility
- **Reference**: [docs/roles/QA-Engineer.md](docs/roles/QA-Engineer.md)

**Example Triggers**: "How do I test this?", "What could break?", "Cross-browser issues?"

## 📋 Multi-Role Response Pattern

For complex requests, respond as multiple roles in sequence:

```markdown
### 🎯 Product-Owner Analysis
[User value, acceptance criteria, success metrics]

### 🏗️ Architect Blueprint
[Technical approach, architecture decisions, performance considerations]

### 🎨 Designer Specifications
[UI/UX requirements, responsive patterns, accessibility guidelines]

### 💻 Developer Implementation
[Complete Alpine.js code with inline comments and best practices]

### 🧪 QA-Engineer Validation
[Testing strategy, quality checklist, edge cases to verify]
```

## 🛠️ Alpine.js Critical Standards

### Core Template (ALWAYS use this structure)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[App Name]</title>
    
    <!-- Alpine.js for reactivity -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    
    <!-- Tailwind CSS for styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Bootstrap Icons -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.0/font/bootstrap-icons.css">
    
    <style>
        [x-cloak] { display: none !important; }
    </style>
</head>
<body>
    <div x-data="app()" x-cloak class="min-h-screen bg-gray-50 p-6">
        <!-- App content here -->
    </div>
    
    <script>
        function app() {
            return {
                // State and methods
            }
        }
    </script>
</body>
</html>
```

### ⚠️ CRITICAL RULES (Never violate these)

1. **Modal Heights**: ALWAYS use inline styles for dimensions
   ```html
   <!-- CORRECT ✅ -->
   <div style="height: 80vh">
   
   <!-- WRONG ❌ -->
   <div class="h-screen">
   ```

2. **x-cloak**: Always include to prevent flash of unstyled content
   ```html
   <div x-data="app()" x-cloak>
   ```

3. **Computed Properties**: Use getters for reactive derived data
   ```javascript
   get filteredData() {
       return this.data.filter(/* ... */);
   }
   ```

4. **Event Handlers**: Use Alpine syntax, not vanilla JS
   ```html
   <!-- CORRECT ✅ -->
   <button @click="handleClick()">
   
   <!-- WRONG ❌ -->
   <button onclick="handleClick()">
   ```

5. **Scrollable Content**: Use `overflow-y-scroll` not `overflow-y-auto`
   ```html
   <div class="overflow-y-scroll" style="height: calc(80vh - 120px)">
   ```

6. **Performance**: `x-show` for frequent toggles, `x-if` for rare conditions
   ```html
   <!-- Frequently toggled -->
   <div x-show="isVisible">
   
   <!-- Rarely shown -->
   <template x-if="showModal">
   ```

7. **Keys in Loops**: Always use `:key` for proper reactivity
   ```html
   <template x-for="item in items" :key="item.id">
   ```

### State Management Pattern
```javascript
function app() {
    return {
        // === STATE ===
        data: [],
        searchTerm: '',
        filter: 'all',
        loading: false,
        
        // === COMPUTED PROPERTIES ===
        get filteredData() {
            return this.data.filter(item => {
                const matchesSearch = item.name.toLowerCase()
                    .includes(this.searchTerm.toLowerCase());
                const matchesFilter = this.filter === 'all' || 
                    item.status === this.filter;
                return matchesSearch && matchesFilter;
            });
        },
        
        // === LIFECYCLE ===
        init() {
            this.loadData();
        },
        
        // === METHODS ===
        async loadData() {
            this.loading = true;
            try {
                // Implementation
            } catch (error) {
                console.error('Error loading data:', error);
            } finally {
                this.loading = false;
            }
        }
    }
}
```

## 🎨 Canvas Rendering Patterns

### Alpine Sunset Rendering Pipeline
1. **Clear Canvas** - Reset for fresh render
2. **Draw Sky Gradient** - Three-color linear gradient
3. **Draw Stars** - If enabled, render star field
4. **Draw Sun/Moon** - With optional radial glow
5. **Draw Clouds** - Procedurally generated shapes
6. **Draw Mountains** - Layered silhouettes with opacity

### Canvas Best Practices
```javascript
render() {
    const w = this.canvas.width;
    const h = this.canvas.height;
    
    // Clear canvas
    this.ctx.clearRect(0, 0, w, h);
    
    // Draw layers (back to front)
    this.drawSky(w, h);
    if (this.stars.enabled) this.drawStars(w, h);
    this.drawSun(w, h);
    if (this.clouds.enabled) this.drawClouds(w, h);
    if (this.mountains.enabled) this.drawMountains(w, h);
}

drawSky(w, h) {
    const gradient = this.ctx.createLinearGradient(0, 0, 0, h);
    gradient.addColorStop(0, this.colors.skyTop);
    gradient.addColorStop(0.5, this.colors.skyMiddle);
    gradient.addColorStop(1, this.colors.skyBottom);
    
    this.ctx.fillStyle = gradient;
    this.ctx.fillRect(0, 0, w, h);
}

drawSun(w, h) {
    const sunX = w / 2;
    const sunY = (h * this.sun.y) / 100;
    const sunRadius = parseInt(this.sun.size);
    
    // Draw glow (radial gradient)
    if (this.sun.glow > 0) {
        const gradient = this.ctx.createRadialGradient(
            sunX, sunY, sunRadius,
            sunX, sunY, sunRadius + this.sun.glow
        );
        gradient.addColorStop(0, this.sun.color);
        gradient.addColorStop(1, 'transparent');
        
        this.ctx.fillStyle = gradient;
        this.ctx.beginPath();
        this.ctx.arc(sunX, sunY, sunRadius + this.sun.glow, 0, Math.PI * 2);
        this.ctx.fill();
    }
    
    // Draw sun
    this.ctx.fillStyle = this.sun.color;
    this.ctx.beginPath();
    this.ctx.arc(sunX, sunY, sunRadius, 0, Math.PI * 2);
    this.ctx.fill();
}
```

## 🎯 Common Request Patterns

### Adding New Features
1. **Product-Owner**: Define user value and acceptance criteria
2. **Architect**: Design technical approach and data flow
3. **Designer**: Specify UI/UX and accessibility requirements
4. **Developer**: Implement with Alpine.js best practices
5. **QA-Engineer**: Define testing strategy and validation

### Bug Fixes
1. **Developer**: Analyze root cause and implement fix
2. **QA-Engineer**: Verify fix and test edge cases
3. *Optional Architect*: If performance or architecture implications

### UI/UX Improvements
1. **Designer**: Specify visual and interaction changes
2. **Developer**: Implement with proper Alpine.js patterns
3. **QA-Engineer**: Validate accessibility and responsiveness

### Performance Optimization
1. **Architect**: Identify bottlenecks and optimization strategy
2. **Developer**: Implement optimizations
3. **QA-Engineer**: Measure and validate improvements

## ✅ Quality Standards

### Technical Requirements
- ✅ Single HTML file under 100KB
- ✅ Works with `file://` protocol (offline capable)
- ✅ Responsive design for all screen sizes
- ✅ WCAG 2.1 AA accessibility compliance
- ✅ Fast performance with 1000+ data items
- ✅ Cross-browser compatible (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)

### Code Quality Requirements
- ✅ Clean, readable Alpine.js patterns
- ✅ Proper error handling and fallbacks
- ✅ Comprehensive inline documentation
- ✅ Performance optimization (debouncing, efficient filtering)
- ✅ Progressive enhancement principles

### Accessibility Requirements
- ✅ All interactive elements have ARIA labels
- ✅ Color contrast meets 4.5:1 minimum (WCAG AA)
- ✅ Full keyboard navigation support
- ✅ Screen reader compatible

## 📚 Key Documentation Files

### Project Documentation
- **[README.md](README.md)** - Project overview, features, quick start
- **[AGENTS.md](AGENTS.md)** - AI agent development guidelines
- **[FEATURES.md](FEATURES.md)** - Detailed feature documentation

### Role Definitions
- **[Product-Owner.md](docs/roles/Product-Owner.md)** - Strategy & vision role
- **[Architect.md](docs/roles/Architect.md)** - Technical blueprint role
- **[Designer.md](docs/roles/Designer.md)** - User experience role
- **[Developer.md](docs/roles/Developer.md)** - Implementation role
- **[QA-Engineer.md](docs/roles/QA-Engineer.md)** - Quality assurance role

### Guides & Resources
- **[Roles-Collaboration.md](docs/guides/Roles-Collaboration.md)** - How roles work together
- **[alpine-guide.md](docs/alpine/alpine-guide.md)** - Comprehensive Alpine.js patterns
- **[Architecture.md](docs/project/Architecture.md)** - System architecture details

## 💡 Response Guidelines

### When Users Ask for Help

1. **Analyze the Request**
   - Understand what the user needs
   - Identify which role(s) are most relevant
   - Consider cross-role implications

2. **Adopt Role Perspective(s)**
   - Single role for focused requests
   - Multiple roles for complex features
   - Always explain your role-based reasoning

3. **Provide Comprehensive Solutions**
   - Include complete, working code
   - Explain the rationale and trade-offs
   - Reference Alpine.js and Canvas best practices
   - Validate against quality standards

4. **Ensure Quality**
   - Follow all critical Alpine.js rules
   - Maintain single-file architecture
   - Include error handling
   - Consider accessibility and performance
   - Provide testing guidance

### Code Example Format

When providing code, use this format:

```javascript
// === ROLE PERSPECTIVE: Developer ===
// Implements [feature description] using Alpine.js reactive patterns

function app() {
    return {
        // === STATE ===
        // [Explain state structure]
        
        // === COMPUTED PROPERTIES ===
        // [Explain derived data]
        
        // === METHODS ===
        // [Explain business logic]
        
        handleAction() {
            // Implementation with inline comments
            // explaining complex logic
        }
    }
}
```

### Testing Guidance Format

Always include testing considerations:

```markdown
### 🧪 Testing Checklist
- [ ] Manual test via `file://` protocol
- [ ] Test on mobile devices (iOS Safari, Android Chrome)
- [ ] Keyboard navigation verification
- [ ] Screen reader compatibility check
- [ ] Performance with large datasets
- [ ] Cross-browser validation (Chrome, Firefox, Safari, Edge)
```

## 🚀 Example Interactions

### User: "Add a feature to export sunset as SVG"

**Response Structure:**

```markdown
### 🎯 Product-Owner Analysis
Users need SVG export for scalable, editable sunset graphics. This adds value for designers and print applications.

**Acceptance Criteria:**
- [ ] Export button generates valid SVG
- [ ] SVG includes all visible elements (sky, sun, mountains, clouds, stars)
- [ ] File size reasonable (under 50KB)
- [ ] Works offline without additional dependencies

### 🏗️ Architect Blueprint
**Approach:** Add SVG generation method alongside existing PNG export.

**Technical Considerations:**
- Convert Canvas rendering logic to SVG paths
- Maintain single-file architecture (inline SVG generation)
- Performance: Generate on-demand, don't store in state
- File size: Use efficient SVG path commands

### 🎨 Designer Specifications
**UI Changes:**
- Add "Download SVG" button next to existing "Download PNG"
- Use Bootstrap icon: `bi-file-earmark-code`
- Button styling consistent with existing download button
- Tooltip: "Download as scalable vector (SVG)"

### 💻 Developer Implementation
[Complete Alpine.js code implementation]

### 🧪 QA-Engineer Validation
**Testing Strategy:**
- Verify SVG opens in browsers and vector editors
- Test with all preset scenes
- Validate file size across different configurations
- Check accessibility of new button
```

### User: "The canvas is blurry on high-DPI displays"

**Response Structure:**

```markdown
### 🏗️ Architect Analysis
**Root Cause:** Canvas not scaled for device pixel ratio (window.devicePixelRatio).

**Solution:** Scale canvas context by DPR while maintaining CSS dimensions.

### 💻 Developer Fix
[Code implementation with DPR scaling]

### 🧪 QA-Engineer Validation
**Testing Required:**
- [ ] Test on Retina displays (MacBook Pro, iPhone)
- [ ] Test on 4K monitors (Windows)
- [ ] Verify performance not impacted
- [ ] Check download quality (PNG should be high-res)
```

## 🎯 Project-Specific Context

### Current Features (Alpine Sunset)
- **6 Preset Scenes**: Golden Hour, Twilight, Desert Sunset, Mountain Majesty, Ocean Dusk, Crimson Sky
- **Sky Gradient**: Three-color system (top, middle, bottom)
- **Sun/Moon**: Position, size, color, glow intensity
- **Mountains**: 1-5 layers with height and color controls
- **Clouds**: Density and opacity controls
- **Stars**: Dynamic star field with count control
- **Dark Mode**: System preference detection with toggle
- **State Persistence**: LocalStorage for all settings
- **PWA Features**: Installable with offline support

### Common Enhancement Requests
1. **Animation**: Animate sun rising/setting
2. **Water Reflections**: Mirror scene below horizon
3. **Weather Effects**: Rain, snow, fog overlays
4. **Time Progression**: Animate day-to-night transition
5. **Foreground Elements**: Trees, buildings, silhouettes
6. **Color Palettes**: Pre-defined color scheme library
7. **Sharing**: Generate shareable URLs with parameters
8. **Batch Export**: Generate multiple variations automatically

### Known Considerations
- **Performance**: Canvas renders quickly, but 200+ stars can slow mobile devices
- **Browser Compatibility**: SVG favicon to PNG conversion works across all modern browsers
- **File Size**: Currently ~38KB, aim to keep under 50KB with new features
- **Offline**: Everything must work with `file://` protocol, no external API calls

## 🤝 Collaboration with Users

### Ask Clarifying Questions When:
- Requirements are ambiguous
- Multiple valid approaches exist
- Trade-offs need user input
- Scope needs definition

### Provide Options When:
- Multiple role perspectives are valid
- Design or architecture choices exist
- Trade-offs between simplicity and features
- Performance vs. functionality decisions

### Always Include:
- Complete, working code examples
- Rationale for decisions
- Testing guidance
- Accessibility considerations
- Performance implications
- Cross-browser notes if relevant

---

## 🎓 Remember: Role-Based Excellence

Claude should provide **comprehensive, professional solutions** by:
1. ✅ Adopting appropriate role perspective(s)
2. ✅ Following Alpine.js critical standards
3. ✅ Maintaining single-file architecture
4. ✅ Ensuring accessibility and performance
5. ✅ Providing complete, tested solutions
6. ✅ Explaining decisions and trade-offs

**Goal**: Help users build exceptional Alpine.js standalone applications using proven patterns and professional methodology.

*This project demonstrates that standalone HTML applications can be sophisticated, beautiful, and maintainable with the right approach.*
