---
title: "Configure AWS Cognito"
date: 2025-09-10
weight: 4
chapter: false
pre: "  5.4.  "
---

## Goal

In this step, we describe how **Amazon Cognito** is used in the *English Journey* web application to manage user authentication.  
Students can sign in using:

- **Email & password**
- **Google (Gmail) account**
- **Facebook account**

Cognito acts as the central identity provider that issues tokens for the frontend and backend of English Journey.

---

## 5.4.1 Role of Amazon Cognito in the architecture

In the architecture of English Journey:

- **Cognito User Pool** stores user identities (email, name, etc.).
- It handles **sign-up, sign-in, password reset and email verification**.
- It integrates with **Amplify** so the React frontend can easily call `signIn`, `signUp` and other auth functions.
- It also connects to **social identity providers**:  
  - **Google** → for users who want to log in with their Gmail  
  - **Facebook** → for users who prefer their Facebook account

All successful logins (email, Google, Facebook) result in **Cognito tokens** that are used to protect our APIs and Lambda functions.

---

## 5.4.2 Creating the Cognito User Pool

The main configuration steps:

1. **Create a User Pool**
   - Sign in to the AWS Management Console → **Amazon Cognito** → **User pools** → **Create user pool**.
   - Choose **Email** as the primary sign-in identifier.
   - Allow **self-registration** so students can create their own accounts.

2. **Configure password policy & verification**
   - Set a basic password policy (minimum length, characters, etc.).
   - Enable **email verification** so students must confirm their email before using the app.
   - Customize email templates (optional) for sign-up and password reset.

3. **Create an app client**
   - Create a **public app client** for the web frontend.
   - Enable **Cognito User Pool** and **social IdPs** as allowed identity providers.
   - Configure allowed **callback URLs** and **sign-out URLs** (for example, the Amplify frontend domain of English Journey).

This user pool is later referenced by Amplify and the React frontend.

---

## 5.4.3 Enabling Google (Gmail) and Facebook login

To support social logins, we added **Google** and **Facebook** as identity providers in Cognito.

### Google (Gmail) login

1. In **Google Cloud Console**, create an **OAuth 2.0 Client ID** for a web application.
2. Set the **authorized redirect URI** to the Cognito callback URL generated for the user pool.
3. Copy the **Client ID** and **Client Secret** from Google.
4. In **Cognito → User pool → Identity providers → Google**:
   - Paste the Client ID and Client Secret.
   - Map Google attributes (email, name) to Cognito standard attributes.

Now users can click **"Sign in with Google"** and authenticate using their Gmail account.

### Facebook login

1. In **Meta for Developers (Facebook Developer)**, create a new **App** and enable **Facebook Login** for Web.
2. Configure the **Valid OAuth Redirect URIs** with the Cognito callback URL.
3. Copy the **App ID** and **App Secret**.
4. In **Cognito → User pool → Identity providers → Facebook**:
   - Paste the App ID and App Secret.
   - Map Facebook attributes (email, name) to Cognito standard attributes.

After this, users can click **"Sign in with Facebook"** to log in with their Facebook profile.

---

## 5.4.4 Integrating Cognito with the Amplify frontend

The **React** frontend of English Journey uses **AWS Amplify Auth** to communicate with Cognito.

Conceptually:

- For **email/password**:
  - `Auth.signUp()` is used to create a new user.
  - `Auth.signIn()` is used for normal login.
- For **Gmail / Facebook** social login:
  - We call `Auth.federatedSignIn({ provider: 'Google' })` or `Auth.federatedSignIn({ provider: 'Facebook' })`.
  - Amplify redirects the user to Google/Facebook, then back to Cognito, then back to the web app with valid tokens.

Example (simplified) React code:

```tsx
import { Auth } from 'aws-amplify';

async function signInWithGoogle() {
  await Auth.federatedSignIn({ provider: 'Google' });
}

async function signInWithFacebook() {
  await Auth.federatedSignIn({ provider: 'Facebook' });
}
```
---
**On the UI, the login page shows three main options:**

    Sign in with email & password

    Sign in with Google

    Sign in with Facebook

All three methods still end up in the same Cognito User Pool.

---
## 5.4.5 Security and user management

**With Cognito we can:**

- Enforce email verification before allowing full access.

- Control which domains can use the login (through callback URLs).

- Centrally manage users (lock account, reset password, delete user, etc.).

- Extend later with MFA or stronger password policies if needed.

**For the scope of this workshop, we focus on:**

- Email & password login

- Social login via Gmail and Facebook

- Basic email verification

## Summary

**In this step, we configured Amazon Cognito as the identity service for English Journey:**

- A User Pool handles user registration and authentication.

-  Students can log in using email, Google (Gmail) or Facebook.

- The React + Amplify frontend uses Cognito tokens to call backend APIs securely.