## 🌟 Transition Animation Highlight

The core of this project is a custom, high-performance **Staggered Blinds Transition** engine built entirely with Vanilla JavaScript, CSS transitions, and Tailwind utility classes. 

### How It Works:
1. **Multi-Blind Architecture**: 
   The transition overlay is split into 5 horizontal strips (`.blind-slice`), creating a window-blind effect that covers the viewport.

2. **Initial Load Sequence**:
   - Upon loading, the blinds are initialized in a fully closed state (`scaleY(1)`).
   - A short timeout triggers the exit sequence, sequentially scaling each strip down to `scaleY(0)` with a staggered delay (`i * 60ms`), smoothly revealing the initial page.

3. **Page Navigation & Dynamic Coloring**:
   - When a user clicks a navigation link, the JavaScript intercepts the routing event.
   - It instantly determines the destination page's designated theme color (e.g., `#eaeaf0` for Home, `#d4f83a` for About, `#111111` for Work/Services).
   - All blind strips dynamically update their background color to match the target page.

4. **Two-Step Staggered Curtain Effect (In & Out)**:
   - **Cover Phase**: The blinds animate upwards/downwards (`scaleY(0)` to `scaleY(1)`) sequentially with staggered timing (`i * 50ms`), completely masking the screen.
   - **Content Swap**: While the screen is fully obscured, the active DOM content is swapped instantly behind the scenes.
   - **Reveal Phase**: The blinds reverse their animation (`scaleY(1)` to `scaleY(0)`), peeling away layer-by-layer to unveil the new page content and its matching aesthetic.

### Key CSS Properties Involved:
- `transform: scaleY(0)` / `scaleY(1)` for smooth GPU-accelerated scaling.
- `transform-origin: top` / `bottom` to control the sliding direction of alternating blinds.
- `transition: transform 0.6s cubic-bezier(0.77, 0, 0.175, 1)` for an organic, premium easing curve.
