# Implementing a Basic Observer Pattern

## 1. Define the Subject (`EventGenerator`)

```javascript
class EventGenerator {
    constructor() {
        this.observers = [];
    }

    // Register an observer
    addObserver(observer) {
        this.observers.push(observer);
    }

    // Remove an observer
    removeObserver(observer) {
        const observerIndex = this.observers.indexOf(observer);
        if (observerIndex > -1) {
            this.observers.splice(observerIndex, 1);
        }
    }

    // Notify all observers
    notifyObservers(message) {
        for (let observer of this.observers) {
            observer.update(message);
        }
    }
}
```

## 2. Define the Observer (`NotificationComponent`)

```javascript
class NotificationComponent {
    constructor(id) {
        this.id = id;
    }

    update(message) {
        console.log(`NotificationComponent ${this.id} received message: ${message}`);
    }
}
```

## 3. Implement Interaction

```javascript
// Instantiate the EventGenerator (Subject)
let eventGenerator = new EventGenerator();

// Create and register observers
let notification1 = new NotificationComponent(1);
let notification2 = new NotificationComponent(2);

eventGenerator.addObserver(notification1);
eventGenerator.addObserver(notification2);

// Simulate an event and notify observers
eventGenerator.notifyObservers("Button clicked!");

// Expected output:
// NotificationComponent 1 received message: Button clicked!
// NotificationComponent 2 received message: Button clicked!
```

In this solution, the `EventGenerator` (the subject) maintains a list of observers (`NotificationComponent`). When the `notifyObservers` method of `EventGenerator` is called, all registered observers get the update via their `update` method. The observers can be added and removed dynamically, ensuring flexibility and decoupling between the main subject and the observers.