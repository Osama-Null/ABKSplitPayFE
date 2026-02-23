# AGENTS.md — ABKSplitPay Frontend

## Build & Run
- `npm start` / `npx expo start` — start Expo dev server
- `npm run android` / `npm run ios` / `npm run web` — platform-specific start
- No test runner or linter is configured.

## Architecture
- **Expo SDK 52 + React Native 0.76** app (JavaScript, no TypeScript).
- Entry: `App.js` → auth check via token → `AuthNavigation` or `MainBottomNavigation`.
- `src/api/` — Axios instance (`index.js`) with JWT Bearer interceptor; API modules per domain (`auth`, `CartAPI`, `ProductAPI`, `StoreAPI`, `order`, `installment`, `profile`). Token stored via `storage.js` (expo-secure-store).
- `src/screens/` — feature folders: `auth/`, `shopping/`, `checkOut/`, `installment/`, `account/`.
- `src/navigation/` — React Navigation stack/tab navigators per feature area.
- `src/context/CartContext.js` — React Context for cart state.
- Data fetching: `@tanstack/react-query`; HTTP: `axios`.
- Backend: REST API at `http://<host>:5137/api`.

## Code Style
- Plain JavaScript (`.js`), no TypeScript. Use `import`/`export` (ES modules).
- Functional components with hooks; `StyleSheet.create` for styles (inline at bottom of file).
- API files use PascalCase for multi-word domains (`ProductAPI.js`) or camelCase (`auth.js`).
- Double quotes for strings; trailing commas in multi-line structures.
- Navigation prop-drilling for `setIsAuthenticated`; no global state library beyond React Context.
