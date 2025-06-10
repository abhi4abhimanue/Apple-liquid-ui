# Liquid Glass UI Effect

This repository contains the HTML and CSS to replicate a liquid glass/glassmorphism UI effect, inspired by the "liquid-glass-effect-macos" project by lucasromerodb.

## Effect Description

The effect simulates a frosted glass appearance with a liquid-like distortion. It uses:
- HTML for the structure.
- CSS for styling, including `backdrop-filter` for blur.
- An SVG filter (`<filter id="glass-distortion">`) embedded in the HTML for the turbulence, lighting, and displacement effects that create the "liquid" look.

## How to Use

1.  **HTML Structure:**
    Include the following structure in your HTML file:

    ```html
    <div class="liquidGlass-wrapper">
        <div class="liquidGlass-effect"></div>
        <div class="liquidGlass-tint"></div>
        <div class="liquidGlass-shine"></div>
        <div class="liquidGlass-text">
            <!-- Your content here (text, SVG, images) -->
            Example Content
        </div>
    </div>

    <!-- Place this SVG filter definition somewhere in your HTML (e.g., end of body) -->
    <svg style="display: none;">
        <filter id="glass-distortion" x="0%" y="0%" width="100%" height="100%" filterUnits="objectBoundingBox">
            <feTurbulence type="fractalNoise" baseFrequency="0.01 0.01" numOctaves="1" seed="5" result="turbulence"/>
            <feComponentTransfer in="turbulence" result="mapped">
                <feFuncR type="gamma" amplitude="1" exponent="10" offset="0.5" />
                <feFuncG type="gamma" amplitude="0" exponent="1" offset="0" />
                <feFuncB type="gamma" amplitude="0" exponent="1" offset="0.5" />
            </feComponentTransfer>
            <feGaussianBlur in="turbulence" stdDeviation="3" result="softMap" />
            <feSpecularLighting in="softMap" surfaceScale="5" specularConstant="1" specularExponent="100" lighting-color="white" result="specLight">
                <fePointLight x="-200" y="-200" z="300" />
            </feSpecularLighting>
            <feComposite in="specLight" operator="arithmetic" k1="0" k2="1" k3="1" k4="0" result="litImage"/>
            <feDisplacementMap in="SourceGraphic" in2="softMap" scale="150" xChannelSelector="R" yChannelSelector="G"/>
        </filter>
    </svg>
    ```

2.  **CSS Styling:**
    Link the `style.css` file (or copy the styles into your main stylesheet). The key classes are:
    - `.liquidGlass-wrapper`
    - `.liquidGlass-effect`
    - `.liquidGlass-tint`
    - `.liquidGlass-shine`
    - `.liquidGlass-text`

    You can customize the appearance by modifying these styles. For example, the `.liquidGlass-wrapper.button` class in the provided `style.css` gives a specific button look.

## Demonstration

Open the `index.html` file in this repository in a web browser to see a simple button demonstrating the effect.

## Credits

This effect is based on the work by **lucasromerodb**.
Original repository: [https://github.com/lucasromerodb/liquid-glass-effect-macos](https://github.com/lucasromerodb/liquid-glass-effect-macos)

Please ensure to credit the original author if you use or adapt this effect.