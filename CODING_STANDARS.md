
# Engineering Standards & Coding Guidelines

This document serves as the authoritative guide for software development within this repository. All code must adhere to these standards to ensure a professional, maintainable, and scalable codebase.

---

## 1. Core Implementation Rules
To maintain consistency across the team, the following rules are mandatory:
* **Language:** All code (identifiers, logic) and documentation must be in **English**.
* **Paradigm:** Object-Oriented Programming (OOP) with a focus on **SOLID** principles.
* **Architecture:** Use established Design Patterns (Factory, Strategy, Repository, etc.).
* **Documentation:** Every class, method, and variable must be documented using professional technical English.

---

## 2. Naming Conventions

| Entity | Standard | Example |
| :--- | :--- | :--- |
| **Classes / Structs** | `PascalCase` | `UserAuthenticationService` |
| **Interfaces** | `IPascalCase` | `IDataRepository` |
| **Methods** | `camelCase` | `calculateMonthlyRevenue()` |
| **Variables / Params** | `camelCase` | `isProcessCompleted` |
| **Private Fields** | `_camelCase` | `_databaseConnection` |
| **Constants** | `UPPER_SNAKE_CASE` | `MAX_RETRY_ATTEMPTS` |

---

## 3. Structural Patterns: The Repository Pattern
We use the **Repository Pattern** to decouple the business logic from the data source, ensuring the **Dependency Inversion Principle**.

```typescript
/**
 * IUserRepository: Defines the contract for user data operations.
 * Following the Interface Segregation Principle.
 */
interface IUserRepository {
    /**
     * Retrieves a user from the data source.
     * @param {string} id - The unique identifier of the user.
     * @returns {object | null} The user data or null if not found.
     */
    getUserById(id: string): object | null;
}

/**
 * SqlUserRepository: SQL-specific implementation of the repository.
 */
class SqlUserRepository implements IUserRepository {
    public getUserById(id: string): object | null {
        // Logic for SQL Querying
        console.log(`[SQL] Fetching user ${id} from database.`);
        return { id, username: "dev_user" };
    }
}
```
---

## 4. Core Principles & Standards

This project follows strict engineering standards to ensure maintainability and scalability.

SOLID Compliance: Every class has a single responsibility and depends on abstractions.

1) Design Patterns: Implementation of Creational, Structural, and Behavioral patterns.

2) Documentation: All entities, methods, and variables are documented using JSDoc/Standard English conventions.

## 3. Documentation Standards (Clean Code)

To ensure code quality, the following rules are applied across the codebase:

* **Descriptive Naming**: Avoid abbreviations. Use `processingOrderTimeout` instead of pOrdT.

* **Function Purity**: Methods should avoid side effects where possible.

* **Encapsulation**: Use private or protected modifiers to hide internal state and expose only what is necessary through public methods.
---
## 4. Development Standard Operating Procedures (DSOP)

a) General Naming Conventions

To maintain a clean and professional codebase, all identifiers must follow these strict naming rules:

* Classes & Interfaces: `PascalCase` (e.g., `UserAuthenticationService`).

* Methods & Variables: `camelCase` (e.g., `calculateTotalAmount`).

* Constants: `UPPER_SNAKE_CASE` (e.g., `MAX_RETRY_ATTEMPTS`).

* Interfaces: Must start with an `I` prefix (e.g., `IDataProvider`).

* Private Members: Must start with an `underscore _` (e.g., `_databaseConnection`).
---
## 5. Mandatory Documentation Standards

Every class and public method MUST include a documentation block following the JSDoc/Doxygen standard.

**Variable & Property Documentation:**
```typescript
/**
  * Global application constants.
 */
class AppConstants {
    /** * @type {number}
      * The time in milliseconds before a network request is aborted.
     */
    public static readonly NETWORK_TIMEOUT_MS: number = 5000;

    /** * @type {string}
      * The default language code for the UI.
     */
    public static readonly DEFAULT_LOCALE: string = "en-US";
}
```

**Method Documentation:**
```typescript
/**
  * Calculates the final price including tax and discounts.
  * @param {number} basePrice - The original price of the item.
  * @param {number} taxRate - The tax percentage as a decimal (e.g., 0.15 for 15%).
  * @param {number} discount - The flat discount amount to subtract.
  * @returns {number} The final calculated price.
 */
function calculateFinalPrice(basePrice: number, taxRate: number, discount: number): number {
    const taxAmount = basePrice * taxRate;
    const finalPrice = (basePrice + taxAmount) - discount;
    return Math.max(0, finalPrice); // Ensure price is never negative
}
```
