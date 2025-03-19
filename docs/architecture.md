# Architecture

## Table of Contents

- [Overview](#overview)
- [User Experience Considerations](#user-experience-considerations)
- [Core Architectural Principles](#core-architectural-principles)
  - [Separation of Concerns](#separation-of-concerns)
  - [Driving the UI from Data Models](#driving-the-ui-from-data-models)
  - [Single Source of Truth](#single-source-of-truth)
  - [Unidirectional Data Flow](#unidirectional-data-flow)
- [Application Layers](#application-layers)
  - [UI Layer](#ui-layer)
  - [Data Layer](#data-layer)
  - [Domain Layer (Optional)](#domain-layer-optional)
- [Dependency Management](#dependency-management)
- [Best Practices](#best-practices)
- [Benefits of the Architecture](#benefits-of-the-architecture)
- [Additional Documentation](#additional-documentation)

---

## Overview

The App is built using a multi-layered architecture that decouples the user interface from business logic and data processing. This design ensures that core data remains consistent and persistent, regardless of the transient nature of UI components.

---

## User Experience Considerations

Mobile devices have resource constraints and can terminate processes unexpectedly. To address this, the architecture ensures:
- Data and business logic are isolated from UI components.
- The app maintains data consistency even if UI parts are recreated.
- Smooth user experience through responsive and reactive data updates.

---

## Core Architectural Principles

### Separation of Concerns

Each layer in the app handles a specific responsibility:
- **UI Components**: Focus on rendering data and handling user interactions.
- **Business Logic & Data Management**: Managed in dedicated layers to ensure consistency and testability.

### Driving the UI from Data Models

The UI layer is driven by data models that are maintained separately from the visual components. This approach:
- Preserves user data across sessions and unexpected interruptions.
- Ensures functionality under varying network conditions.
- Simplifies testing by decoupling presentation from data logic.

### Single Source of Truth

Each data type is managed by a single authoritative source:
- Changes to data occur in one centralized component.
- Data is exposed in an immutable format.
- Enhances traceability and minimizes data corruption risks.

### Unidirectional Data Flow

Data flows from higher-level components (repositories, use cases) down to the UI, while user events propagate upward to update the centralized data source. This flow:
- Increases consistency and predictability.
- Simplifies debugging.
- Reinforces the single source of truth principle.

---

## Application Layers

The App is divided into three primary layers:
![](assets/mad-arch-overview.png)

### UI Layer

 ![](assets/mad-arch-overview-ui.png)

- **Purpose**: Render data and capture user interactions.
- **Components**: Visual elements and state managers (controllers, view models, etc.).
- **Interaction**: Observes state changes from upper layers and emits events for state modifications.

### Data Layer
  
 ![](assets/mad-arch-overview-data.png)

- **Purpose**: Encapsulate business logic and manage data operations.
- **Components**:  
  - **Repositories**: Coordinate data from one or more sources.
  - **Data Sources**: Interfaces to external systems (network, file, local storage).
- **Role**: Serve as the single source of truth by centralizing business rules and data processing.

### Domain Layer (Optional)


 ![](assets/mad-arch-overview-domain.png)

- **Purpose**: Encapsulate complex or reusable business logic.
- **Components**: Use cases or interactors that expose functionalities to the UI layer.
- **When to Use**: For common business logic shared by multiple UI components or to further abstract complex operations.

---

## Dependency Management

To maintain scalability and testability, the app utilizes patterns such as:
- **Dependency Injection (DI)**: External provisioning of dependencies.
- **Service Locator**: A registry for shared services.

These approaches ensure modularity and facilitate future refactoring.

---

## Best Practices

1. **Keep UI Components Lean**: Delegate core data handling to dedicated layers.
2. **Minimize Platform Dependencies**: Keep business logic independent of any specific operating system.
3. **Establish Clear Module Boundaries**: Avoid mixing responsibilities within a module.
4. **Expose Only Necessary Details**: Prevent accidental coupling by hiding internal implementations.
5. **Focus on Core Features**: Leverage established libraries to handle boilerplate code.
6. **Design for Testability**: Isolate modules to simplify unit and integration testing.
7. **Handle Long-Running Operations Asynchronously**: Ensure the UI remains responsive.
8. **Persist Key Data**: Enable functionality even under intermittent connectivity.

---

## Benefits of the Architecture

- **Maintainability**: Clear separation of concerns makes it easier to update and extend.
- **Scalability**: Multiple teams can work on different layers without conflicts.
- **Testability**: Isolated modules lead to simpler and more effective testing.
- **Resilience**: Ensures continuity even if UI components are terminated.
- **Enhanced User Experience**: A stable, responsive interface that minimizes data loss.

---

## Additional Documentation

For platform-specific implementation details, please refer to:
- [Android Platform-Specific Architecture](android/android-architecture.md)
- [iOS Platform-Specific Architecture](ios/ios-architecture.md)
