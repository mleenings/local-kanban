# Task: [Short Description]

## 🧐 Problem Analysis
- **Context:** Why is this task necessary?
- **Root Cause:** (If bug) Why did it happen?
- **Current State:** How does it behave now?

## 💡 Solution Design
- **First Principles Thinking:** What is the simplest way to solve this?
- **Architecture:** Which components/files are affected?
- **Decisions:** Why did I choose approach A over B?

## 📝 Implementation Notes
- **Changes:** List of major modifications.
- **Dependencies:** Any new libraries or config changes?

## 🚀 Verification Steps
- [ ] Step 1: Execute command `X`
- [ ] Step 2: Check output `Y`


--

Finished Example:

# Task: Fix Authorization Header in API Client

## 🧐 Problem Analysis
- **Context:** API returns 401 Unauthorized for all requests since the last security update.
- **Root Cause:** The `Bearer` prefix was missing in the HTTP header; only the raw token was sent.

## 💡 Solution Design
- Modified `ApiClient.java` to prepend "Bearer " to the token string.
- Chose a global interceptor approach to ensure all future requests are covered automatically (DRY principle).

## 📝 Implementation Notes
- Updated `HeaderInterceptor.java`.
- Verified that the token is still correctly retrieved from the secure storage.

## 🚀 Verification Steps
- [x] Run local integration test `AuthFlowTest`.
- [x] Verify logs: `Authorization: Bearer <token>` is present.
- [x] Tested with expired token: 401 is handled correctly by the UI.
