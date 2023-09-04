# Authorization

## Create two components for handling routing (See own files)
- AuthContext.jsx
- ProtectedRoutes.jsx

## How to use
- When setting up your routes you wrap your components inside of theese context providers
- Wrapping components in AuthContextProvider will give the component access to elements like createUser, signIn, logout, user
- Wrapping with ProtectedRoute will protect users from accessing components inside if they are not logged in
- Importing your AuthContextProvider and using
```js
import { UserAuth } from "./AuthContextProvider";
const { user } UserAuth();
```
  gives us access to user data, and we can then make user protected routes for personal information.