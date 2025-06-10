# Liquid Glass UI Kit (Phase 1)

This is a general-purpose UI kit based on a "Liquid Glass" design principle. It aims to provide a set of common web components with a unique, modern aesthetic.

This kit is currently in **Phase 1 of development**, including the following foundational components:
*   Buttons (Primary, Secondary, Text)
*   Input Fields (Text, Password, Textarea)
*   Cards

## Demo & Showcase

Open the `liquid-glass-kit.html` file in your web browser to see a live demonstration of the components.

## How to Use

1.  **Link the CSS:**
    Include the `liquid-glass-kit.css` file in the `<head>` of your HTML document:
    ```html
    <link rel="stylesheet" href="liquid-glass-kit.css">
    ```

2.  **Include SVG Filter:**
    The liquid glass effect relies on an SVG filter. You **must** include the following SVG block somewhere in your HTML body (e.g., right before the closing `</body>` tag). It is styled with `display: none;` so it won't be visually rendered.

    ```html
    <!-- SVG Filter Definition -->
    <svg style="display: none;">
        <filter id="liquid-glass-filter" x="0%" y="0%" width="100%" height="100%" filterUnits="objectBoundingBox">
            <feTurbulence type="fractalNoise" baseFrequency="0.01 0.01" numOctaves="1" seed="5" result="turbulenceBase"/>
            <feGaussianBlur in="turbulenceBase" stdDeviation="3" result="blurredTurbulence"/>
            <feSpecularLighting in="blurredTurbulence" surfaceScale="5" specularConstant="0.8" specularExponent="100" lighting-color="white" result="specularLight">
                <fePointLight x="-200" y="-200" z="300" />
            </feSpecularLighting>
            <feComposite in="specularLight" operator="in" in2="blurredTurbulence" result="specularMap"/>
            <feDisplacementMap in="SourceGraphic" in2="blurredTurbulence" scale="10" xChannelSelector="R" yChannelSelector="G" result="displaced"/>
            <feComposite in="displaced" in2="specularMap" operator="arithmetic" k1="0" k2="1" k3="1" k4="0.1" result="finalEffect"/>
        </filter>
    </svg>
    ```

3.  **Use Component Classes:**
    Refer to `liquid-glass-kit.html` for examples of how to structure the HTML for each component using the provided CSS classes (e.g., `.lg-button`, `.lg-input`, `.lg-card`, and their variations).

    **Example - Primary Button:**
    ```html
    <button class="lg-button lg-button-primary">Primary Button</button>
    ```

    **Example - Input Field:**
    ```html
    <div class="lg-input-group">
        <label for="my-input">My Input</label>
        <input type="text" id="my-input" class="lg-input" placeholder="Enter text...">
    </div>
    ```

    **Example - Card:**
    ```html
    <div class="lg-card">
        <div class="lg-card-header"><h3>Card Title</h3></div>
        <div class="lg-card-body"><p>Card content goes here.</p></div>
    </div>
    ```

## Customization Notes

*   The primary SVG filter is `id="liquid-glass-filter"`. You can try to adjust its parameters (`baseFrequency`, `stdDeviation`, `scale`, etc.) within the `<svg>` block to alter the intensity or characteristics of the effect.
*   CSS variables for filter parameters are not used in this version but could be a future enhancement for easier customization via CSS.

## Future Development (Phase 2 and beyond)

This UI kit will be expanded with more components, including:
*   Modals
*   Navigation Bars
*   Checkboxes & Radio Buttons
*   Dropdowns/Selects
*   And more.

Stay tuned for updates!

---
*This UI kit was developed based on a "liquid glass" design concept, inspired by various modern UI trends.*