# React Router Frontend

A frontend can be added using the `add-frontend` tool, either manually or via the coding agent. This frontend serves as the main user-facing entry point to the distributed system. It is primarily used for user interaction and for visualizing backend functionality.

The frontend typically triggers requests to API endpoints to fetch or submit data and then displays the results. We use **React** as the frontend framework, with development commonly involving **HTML**, **TypeScript**, and **CSS**.

For routing, we use **React Router 17**, chosen for its predictable and easy-to-understand structure for both humans and AI. The routes you can navigate to are defined under:

```
modules/your-frontend-name/app/routes
```

We also integrate **shadcn/ui** components, so neither you nor the AI needs to build UI components from scratch. These components are easy to customize, and all their source code lives directly in your project under:

```
modules/your-frontend-name/components/ui
```

Instead of installing dependencies manually, you (or the coding agent) should use the `add-dependencies` tool, which installs and validates them automatically.

To view the frontend, open the following URL in your browser:

```
http://localhost:51732
```

Bluetext uses the bun runtime environment for fast start-up times and an excellent developer experience.
