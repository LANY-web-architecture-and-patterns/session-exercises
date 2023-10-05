# Exercise 3: Enhancing Web Components Using the Decorator Pattern

## Overview

The Decorator pattern is a structural design pattern that allows you to add new functionalities to existing objects without altering their structure. This pattern creates a decorator class that wraps the original class and provides additional functionalities, ensuring that class responsibilities can be added or removed dynamically.

## Objective

To understand how the Decorator pattern can be used to enhance or modify web components dynamically without changing their core behavior or structure.

## Pre-requisites

- Familiarity with JavaScript, CSS, and web development basics.
- A code editor and a browser for testing.

## Task Description

You'll be working with a basic web component, such as a button. Your task is to use the Decorator pattern to add features like tooltips, change of color on hover, and more, without modifying the component's original code.

### Step 1: Define the Component

1. Create a class named `ButtonComponent` that represents a basic button on a web page.
2. The class should render a simple button on the page and might have a method like `click()` to simulate a button click.

### Step 2: Create the Decorator Base

1. Create a class or interface named `ButtonDecorator` that has the same methods as `ButtonComponent`.
2. This will serve as a base for all specific decorators you'll create next.

### Step 3: Implement Specific Decorators

1. **Tooltip Decorator**:
   - Create a class `TooltipDecorator` that extends or implements `ButtonDecorator`.
   - Add a method or modify the existing method to display a tooltip when the button is hovered over.
  
2. **ColorChangeOnHover Decorator**:
   - Create a class `ColorChangeOnHoverDecorator` that extends or implements `ButtonDecorator`.
   - Modify the rendering method to change the button's color when it's hovered over.
   
3. **IconDecorator**:
   - Create a class `IconDecorator` that extends or implements `ButtonDecorator`.
   - Modify the rendering method to add an icon to the button.

### Step 4: Use the Decorators

1. Instantiate a basic `ButtonComponent`.
2. Enhance the button using the decorators. For instance, you can wrap it in the `TooltipDecorator` to add a tooltip.
3. Continue wrapping or decorating as needed to add more functionalities.
4. Render the enhanced button on the web page and observe the added functionalities.

## Expected Outcome

A button that starts as a simple component but gains multiple features (like tooltips, color change on hover, and an icon) as it's wrapped in various decorators.

## Evaluation Criteria

1. Correct implementation of the Decorator pattern.
2. Successful enhancement of the button without altering its core code.
3. Dynamic addition and removal of features using decorators.
4. Code modularity and clarity.

## Tips

- Keep the decorators focused. Each decorator should add one specific feature to the button.
- Ensure decorators can be combined in any order. For instance, adding a tooltip should work regardless of whether the color change on hover is applied before or after it.
- The core button class should remain unchanged throughout this exercise. All modifications should be done using decorators.

## Conclusion

The Decorator pattern offers a robust mechanism to extend the functionalities of objects dynamically, promoting code reuse and flexibility. By the end of this exercise, you'll have gained practical experience in enhancing web components using this pattern, highlighting its value in real-world web development scenarios.