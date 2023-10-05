# Enhancing Web Components Using the Decorator Pattern

Here's an indicative solution for the exercise on enhancing web components using the Decorator pattern.

## 1. Define the Component (`ButtonComponent`)

```javascript
class ButtonComponent {
    constructor(label) {
        this.label = label;
    }

    render() {
        return `<button>${this.label}</button>`;
    }
}
```

## 2. Create the Decorator Base (`ButtonDecorator`)

```javascript
class ButtonDecorator extends ButtonComponent {
    constructor(button) {
        super();
        this.button = button;
    }

    render() {
        return this.button.render();
    }
}
```

## 3. Implement Specific Decorators

### TooltipDecorator

```javascript
class TooltipDecorator extends ButtonDecorator {
    constructor(button, tooltipText) {
        super(button);
        this.tooltipText = tooltipText;
    }

    render() {
        return `<div class="tooltip">${super.render()}<span class="tooltiptext">${this.tooltipText}</span></div>`;
    }
}
```

### ColorChangeOnHoverDecorator

```javascript
class ColorChangeOnHoverDecorator extends ButtonDecorator {
    constructor(button, hoverColor) {
        super(button);
        this.hoverColor = hoverColor;
    }

    render() {
        const buttonHTML = super.render();
        const style = `
        <style>
            button:hover {
                background-color: ${this.hoverColor};
            }
        </style>
        `;
        return style + buttonHTML;
    }
}
```

### IconDecorator

```javascript
class IconDecorator extends ButtonDecorator {
    constructor(button, iconClass) {
        super(button);
        this.iconClass = iconClass;
    }

    render() {
        return super.render().replace('<button>', `<button><i class="${this.iconClass}"></i> `);
    }
}
```

## 4. Use the Decorators

```javascript
let simpleButton = new ButtonComponent("Click me!");

// Enhance the button with a tooltip
let tooltipButton = new TooltipDecorator(simpleButton, "I'm a tooltip!");

// Further enhance by changing color on hover
let coloredTooltipButton = new ColorChangeOnHoverDecorator(tooltipButton, "red");

// Add an icon to the button
let iconColoredTooltipButton = new IconDecorator(coloredTooltipButton, "fas fa-check");

// Render the enhanced button
console.log(iconColoredTooltipButton.render());
```

In this solution, the base button (`ButtonComponent`) renders a simple button. The decorators (`TooltipDecorator`, `ColorChangeOnHoverDecorator`, `IconDecorator`) then add or modify features of the base button without changing its core implementation. Each decorator focuses on a single enhancement, and decorators can be combined in any order to create a button with multiple features.