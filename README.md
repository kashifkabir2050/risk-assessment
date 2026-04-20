# Risk Assessment Portal
**Pakistan Islamia Higher Secondary School · Sharjah**

Two-page system:
- `index.html` → Employee form (Classroom & Outdoor assessments)
- `dashboard.html` → Admin dashboard (password protected)

---

## Firebase Setup (Already Configured)
Your Firebase project `wellbeing-portal` is already connected.

### Firestore Rules — MUST set this:
Go to Firebase Console → Firestore Database → Rules → paste:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /risk_assessments/{docId} {
      allow read, write: if true;
    }
    match /submissions/{docId} {
      allow read, write: if true;
    }
  }
}
```

---

## GitHub Pages Deployment

1. Create repo at github.com → name: `risk-assessment`
2. Upload `index.html` and `dashboard.html`
3. Settings → Pages → Deploy from main branch
4. Live at: `https://YOUR_USERNAME.github.io/risk-assessment/`

---

## Admin Dashboard Login
- Username: `admin`
- Password: `risk2024`

Change these in `dashboard.html`:
```js
const ADMIN_USER='admin', ADMIN_PASS='risk2024';
```

---

## Features
- Classroom + Outdoor risk assessment forms
- Mon–Thu daily risk table with Safety / Equipment / General categories
- Risk levels: None / Low / Medium / High / Critical
- All data saved to Firebase Firestore
- Dashboard: Overview, Daily, Weekly, Monthly analysis
- Charts: line, bar, doughnut for all periods
- Delete any record (with confirmation)
- PDF download for every view + individual record PDFs
- Flagged tab for High/Critical risk records
