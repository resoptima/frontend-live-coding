# Frontend Live Coding Exercise — Product Catalogue

## Overview

Build a small product catalogue application consisting of:

- A frontend application that displays a list of products.
- A small Backend-for-Frontend (BFF) service that provides the data to the frontend.
- The BFF should retrieve product data from the public [DummyJSON API](https://dummyjson.com/).

The goal is to build a simple working solution while making sensible decisions about API design, data transformation, error handling, and frontend structure.

---

## Architecture

The expected high-level architecture is:

```text
┌──────────────┐
│   Frontend   │
└──────┬───────┘
       │
       │ GET /api/products
       ▼
┌──────────────┐
│     BFF      │
└──────┬───────┘
       │
       │ GET /products
       ▼
┌──────────────┐
│  DummyJSON   │
└──────────────┘
```

The frontend should **not call DummyJSON directly**. The BFF is responsible for communicating with the upstream API.

---

## Requirements

### 1. BFF

Create an endpoint that the frontend can use to retrieve products:

```text
GET /api/products
```

The BFF should:

1. Call the DummyJSON products API.
2. Transform the upstream response into a response suitable for the frontend.
3. Return the transformed response to the frontend.

You should **not simply proxy the DummyJSON response**.

For example, DummyJSON returns products containing fields such as:

```json
{
  "id": 1,
  "title": "Example Product",
  "description": "...",
  "price": 9.99,
  "category": "beauty",
  "rating": 4.5,
  "stock": 10,
  "thumbnail": "..."
}
```

Your frontend-facing API should expose a slightly different model such as:

```json
    {
      "id": 1,
      "name": "Example Product",
      "price": 9.99,
      "category": "beauty",
      "imageUrl": "...",
      "inStock": true
    }
```

The exact implementation and API design are up to you.

### 2. Frontend

Create a simple UI that:

- Retrieves products from your BFF.
- Displays the products in a list or grid.
- Shows the product name, price, image, category, and availability.
- Handles loading and error states.

The UI does not need to be highly polished. Focus on functionality and code quality.

---

## Upstream API

You can use the following public API:

**Products**

```text
https://dummyjson.com/products
```

Documentation:

https://dummyjson.com/docs/products

No API key or authentication is required.

---

## Optional Improvements

If you complete the core requirements early, feel free to improve the solution.

Some examples:

- Pagination
- Product search
- Filtering
- Sorting
- Improved error handling
- Request cancellation
- Caching
- Input validation
- Automated tests
- Improved UI/UX
- Better API documentation

These are **not required**. Prioritize getting a clean, working solution first.

---

## Technical Choices

For this exercise, please use the following technologies:

### Frontend

- **React**
- **TypeScript**
- You are free to choose your preferred React setup, styling approach, and state management approach.

### BFF

- **Node.js**
- **TypeScript**
- Use a Node.js HTTP framework such as **Express**, **Fastify**, or another framework you are comfortable with.
- The BFF should expose the API consumed by the React application and be responsible for communicating with DummyJSON and transforming its response.

You are free to choose the project structure, libraries, and tooling you feel are appropriate.

There is no requirement to use a particular build tool, component library, state management library, or testing framework.

---

## What We're Looking For

There is no single correct implementation.

We are interested in how you:

- Break down the problem.
- Design the BFF/frontend boundary.
- Transform and model data.
- Handle asynchronous operations and failures.
- Structure your code.
- Make technical trade-offs.
- Explain your decisions.

If you would approach something differently in a production application, feel free to discuss that during the exercise.

**Don't feel that you need to implement every possible improvement.** The exercise is intentionally small, and we care more about your approach and reasoning than the number of features you complete.
