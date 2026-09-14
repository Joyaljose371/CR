# ClassPilot PWA — Firebase setup

This build is offline-first and installable.

## One-time Firebase setup
1. In Firebase Console for project `classr-29e5f`, create a **Cloud Firestore** database.
2. In **Authentication → Sign-in method**, enable **Email/Password**.
3. Install Firebase CLI on your computer: `npm install -g firebase-tools`
4. From this folder run:
   - `firebase login`
   - `firebase deploy`
5. Open the HTTPS Hosting URL Firebase gives you.
6. In ClassPilot → Settings → Cloud Sync, create/sign in to your private account.
7. On Android/Chrome or supported desktop browsers use **Install App** / **Add to Home screen**.

## How data works
- Every edit is written to local browser storage immediately.
- If offline, the app keeps working and marks cloud sync as pending.
- When internet returns, it automatically syncs to your private Firebase user path.
- Firestore browser persistence is also enabled when supported.
- Each changed cloud state creates a restore-point version; the newest 30 are retained.
- Manual restore points can be created from Settings.

## Security
The included Firestore rules only allow an authenticated user to read/write their own `/users/{uid}/...` data. Do not replace these with public `allow read, write: if true` rules.

## Birthdays
Student DOBs are stored in Student Details. On every app open, birthdays occurring today or tomorrow appear as reminders. Birthday messages are copy/share ready.
