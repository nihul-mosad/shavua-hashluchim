# שבוע כינוס השלוחים — הוראות התקנה

## 1. העלאה לאתר (GitHub Pages)
1. ב-GitHub: **New repository** בשם `shavua-hashluchim` (ציבורי).
2. **Add file → Upload files** ← מעלים את `index.html`.
3. **Settings → Pages** ← Branch: `main`, תיקייה `/ (root)` ← Save.
4. אחרי כדקה האתר זמין בכתובת:
   `https://<שם-המשתמש>.github.io/shavua-hashluchim/`
5. לבקש מנטפרי לאשר את הכתובת.

בשלב הזה האתר כבר עובד במצב הדגמה (הנתונים נשמרים רק במחשב שפותח אותו).

## 2. חיבור לענן (Firebase) — כדי שהצוות וההורים יראו את אותם נתונים
1. ב-https://console.firebase.google.com ← **Add project** ← שם: `shavua-hashluchim`.
2. **Build → Firestore Database → Create database** (מיקום: eur3, Production mode).
3. **Build → Authentication → Get started → Email/Password → Enable**.
   - בלשונית **Users → Add user** יוצרים משתמש לכל איש צוות (דוא"ל + סיסמה).
   - בלשונית **Settings → Authorized domains** מוסיפים: `<שם-המשתמש>.github.io`
4. **Firestore → Rules** ← מדביקים את התוכן של `firestore.rules`,
   מחליפים את `your-email@gmail.com` בדוא"ל של אנשי הצוות ← **Publish**.
5. **Project settings (גלגל שיניים) → Your apps → </> (Web)** ← רושמים אפליקציה
   ומעתיקים את אובייקט `firebaseConfig`.
6. ב-`index.html` מחפשים את השורה:
   `const FIREBASE_CONFIG = null;`
   ומחליפים ב:
   ```js
   const FIREBASE_CONFIG = { apiKey: "...", authDomain: "...", projectId: "...", storageBucket: "...", messagingSenderId: "...", appId: "..." };
   ```
7. מעלים שוב את `index.html` ל-GitHub (מחליף את הקודם).

## 3. שימוש
- **צוות**: כניסה ← "ניהול" ← הוספת כיתות ותלמידים (הדבקת רשימה, שם בשורה).
- **חלוקת כרטיסים**: בוחרים כיתה ← לוחצים על תלמיד ← לוחצים על הכרטיס. אפשר לבטל מיד.
- **כרטיס לכל הכיתה**: נקודות לכיתה כולה בלי לשייך לתלמיד.
- **מסך הקרנה**: מירוץ הכיתות במסך מלא, להקרנה במסדרון או באולם.
- **הורים**: "ניהול" ← "הדפסת פתקים להורים" — פתק לכל כיתה עם הכתובת והקוד.
  ההורה רואה רק את סה"כ הכיתה, את פילוח ארבעת הכרטיסים ואת מקום הכיתה. שמות ונתוני תלמידים לא נשלחים לעמוד ההורים בכלל.
- קוד שדלף? "קוד חדש" מבטל את הישן מיד.
