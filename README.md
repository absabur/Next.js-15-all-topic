# Next.js 13+ Routing & Server Components Reference

This document covers advanced features and best practices of routing, layouts, metadata handling, server components, and more in Next.js 13+ (App Router).

---

## Route Segments

- catch-all:  
  - ``[[...slug]]``: matches zero or more segments  
  - ``[[[...slug]]]``: matches optional segments

---

## Private Folders

- Folders like `_lib`, `_utils` are not considered routes.
- The underscore prevents the folder from becoming a route.

---

## Underscores in Route URLs

- Use `%5F` for underscores in URLs (e.g., /user%5Fprofile).

---

## Route Groups

- `(groupName)` will group routes without affecting the URL.

```tsx
// app/(dashboard)/settings/page.tsx → URL: /settings
```

---

## Metadata Title Object

```js
export const metadata = {
  title: {
    default: "Fallback title for child pages",
    template: "%s | My App" // Child page title appears in %s
  }
};
```

To override the parent template:

```js
export const metadata = {
  title: {
    absolute: "Completely new title"
  }
};
```

---

## Link Navigation Behavior

- When using `<Link>`, sometimes the last route gets forgotten.
- To fix this, redirect to home before navigating back.

---

## params and searchParams

- In Server Components:  
  Use `async ({ params, searchParams }) => {}`

- In Client Components:  
  Use the `useParams()` and `useSearchParams()` hooks from `next/navigation`.

---

## layout.js vs template.js

- `layout.js`: Shared UI (sidebar, header), does not re-render on navigation.
- `template.js`: Re-renders every time the route is loaded.

---

## startTransition from React

Used to defer non-urgent updates:

```js
startTransition(() => {
  // less important state update
});
```

---

## global-error.js

- Acts as a global error boundary.
- Must include `<html><body>` to take over the whole page.
- Works only in production mode.

---

## Parallel Routes

- Use folders prefixed with `@`, e.g., `@modal`.
- Each parallel route must have a fallback: `default.js`.

---

## Intercepted Routes

- Prefix folders with:
  - `(.)route`: from same level  
  - `(..)route`: one level up  
  - `(..)(..)route`: two levels up  
  - `(...)route`: from the root

---

## Static to Dynamic SSR

```js
export const dynamic = "force-dynamic"; // Forces server rendering
```

---

## Dynamic to Static SSR (SSG)

- Use `generateStaticParams()` to prebuild static pages.

---

## server-only Package

- Prevents server code from being bundled into the client.
- Useful for secure server logic.

---

## client-only Package

- Prevents certain modules from running on the server.
- Ensures client-side-only packages don't break SSR.

---

## Using Server Components in Client

- You can't import a Server Component directly into a Client Component if it uses server-only modules.
- Workaround: Pass it as a `children` or prop.

---

## useFormStatus()

- Provides the pending status of a form submission.
- Can disable buttons or show loading UI.

---

## function.bind()

- Use `.bind()` to pass extra arguments to event handlers:

```js
<button onClick={handleClick.bind(null, id)}>Delete</button>
```

---

## useOptimistic()

- Used for optimistic UI updates:
  - Temporarily updates UI before the server confirms the action.

---

## Forms in Server Components

- Forms can directly submit to server actions.
- Supports create, update, delete with validation.

---

## Form Component with action="/route"

- Submitting a form with an action:
  - Automatically sends form data as query params.
  - Redirects to the target route after submit.

---

## Clerk Authentication

- Use Clerk package for secure authentication in App Router.
