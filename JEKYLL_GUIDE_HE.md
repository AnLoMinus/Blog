## מדריך מלא להפעלת Jekyll

ברוכים הבאים למדריך שמלווה אתכם צעד אחר צעד בהקמת בלוג אישי או אתר סטטי באמצעות Jekyll. המדריך נבנה כדי לאפשר שימוש חוזר בתבנית המאגר ולהסביר כל שלב – מהתקנה ועד תחזוקה.

---

### 1. מה זה Jekyll?

Jekyll הוא מחולל אתרים סטטיים (Static Site Generator) שנבנה מעל Ruby ומתחבר היטב ל-GitHub Pages. הוא מאפשר לכתוב פוסטים בפורמט Markdown, להגדיר מבנה תצורה גמיש ולהפיק אתר מהיר ובטוח.

---

### 2. דרישות מקדימות

- macOS / Linux / Windows (WSL2).
- Ruby 3.1 ומעלה.
- Bundler (מנהל התלויות של Ruby).
- Git, Node.js (לא חובה אך מומלץ לערכות נושא מתקדמות).
- עורך טקסט / IDE (VS Code, Cursor, Neovim וכו').

בדקו התקנות:

```shell
ruby -v
bundle -v
git --version
```

---

### 3. התקנות ראשוניות

1. התקינו Ruby (ב-macOS מומלץ להשתמש ב-Homebrew או ב-rbenv).
   ```shell
   brew install rbenv ruby-build
   rbenv install 3.2.2
   rbenv global 3.2.2
   ```
2. התקינו Bundler:
   ```shell
   gem install bundler
   ```
3. שחזרו את המאגר:
   ```shell
   git clone https://github.com/<your-user>/Blog.git
   cd Blog
   ```
4. התקינו תלויות:
   ```shell
   bundle install
   ```

---

### 4. מבנה המאגר

| תיקיה / קובץ | תיאור |
| --- | --- |
| `_config.yml` | קובץ התצורה הראשי של Jekyll. |
| `_posts/` | כל פוסט חדש בפורמט `YYYY-MM-DD-title.md`. |
| `_layouts/` | תבניות עיצוב לדפים ופוסטים. |
| `_includes/` | רכיבים הניתנים לשילוב חוזר (כותרות, פוטר וכו'). |
| `assets/` | קבצי CSS, JS ותמונות. |
| `JEKYLL_GUIDE_HE.md` | המדריך שאתם קוראים כעת. |
| `CODE_OF_CONDUCT.md` וכו' | מסמכי מדיניות ומידע תפעולי. |

---

### 5. הגדרות בסיסיות (`_config.yml`)

פתחו את הקובץ `_config.yml` ועדכנו:

- `title`: שם הבלוג.
- `description`: תיאור קצר שיופיע במטה.
- `url`: כתובת האתר המלאה (למשל `https://<user>.github.io`).
- `baseurl`: בדרך כלל ריק ל-GitHub Pages ראשי, או `/blog` למאגר בשם שונה.
- `author`: פרטי הכותב (שם, אימייל, קישורים).

לאחר כל שינוי, הריצו build לבדיקה:

```shell
bundle exec jekyll build
```

---

### 6. הרצת שרת מקומי

```shell
bundle exec jekyll serve
```

ברירת המחדל: <http://localhost:4000>. השתמשו באופציה `--livereload` לקבלת רענון אוטומטי.

```shell
bundle exec jekyll serve --livereload
```

לחצו `Ctrl+C` כדי לעצור.

---

### 7. יצירת פוסט חדש

1. צרו קובץ חדש ב-`_posts/` בשם לפי התבנית: `2025-11-12-welcome.md`.
2. הוסיפו Front Matter (YAML בראש הקובץ):

```markdown
---
layout: post
title: "ברוכים הבאים"
date: 2025-11-12 12:00:00 +0300
categories: [חדשות]
tags: [התחלה, jekyll]
---
```

3. כתבו את התוכן ב-Markdown. שמרו והריצו `jekyll serve` לראות את התוצאה.

---

### 8. דפים סטטיים

- צרו קובץ `about.md` ב-root עם Front Matter:

```markdown
---
layout: page
title: "אודות"
permalink: /about/
---
```

- הוסיפו תוכן ושמרו. הדף יופיע תחת הנתיב `/about/`.

---

### 9. התאמה אישית של עיצוב

- ערכו את `assets/css/style.scss` להוספת צבעים ומרווחים.
- הוסיפו רכיבי HTML ל-`_includes/header.html` או `footer.html`.
- לשינויים גדולים, שקלו יצירת Layout חדש ב-`_layouts/`.

זכרו להריץ build לאחר כל שינוי משמעותי:

```shell
bundle exec jekyll build
```

---

### 10. שימוש בתוספים (Plugins)

1. פתחו את `Gemfile` והוסיפו שורה:
   ```ruby
   gem "jekyll-seo-tag"
   ```
2. עדכנו את `_config.yml`:
   ```yaml
   plugins:
     - jekyll-seo-tag
   ```
3. התקינו והריצו:
   ```shell
   bundle install
   bundle exec jekyll build
   ```

שימו לב: ב-GitHub Pages יש רשימת תוספים מאושרת. בדקו את התיעוד לפני שימוש בתוסף שאינו ברשימה.

---

### 11. פריסה ל-GitHub Pages

#### אפשרות 1: GitHub Actions

1. צרו קובץ `.github/workflows/deploy.yml`.
2. השתמשו בתבנית פעולה (ראו דוגמא במאגר או בתיעוד GitHub).
3. ודאו שה-branch `main` מכיל את קובץ ה-build וש-GitHub Pages מופעל עבור `gh-pages` (או `docs/`).

#### אפשרות 2: פרסום ידני

```shell
JEKYLL_ENV=production bundle exec jekyll build
git add .
git commit -m "Build for deploy"
git push origin main
```

ב-GitHub Pages בחרו את התיקייה `/_site` או את ה-branch הרלוונטי בהתאם להגדרות שלכם.

---

### 12. תחזוקה שוטפת

- עדכנו תלות כל רבעון:
  ```shell
  bundle update
  ```
- בדקו קישורים שבורים:
  ```shell
  bundle exec htmlproofer ./_site
  ```
- שמרו על `CHANGELOG.md` ו-`VERSIONS.md` מעודכנים.
- בדקו את `ROADMAP.md` לתכנון עתידי.

---

### 13. פתרון תקלות נפוצות

| בעיה | סיבה אפשרית | פתרון |
| --- | --- | --- |
| `Could not find gem` | תלויות חסרות | הריצו `bundle install` או `bundle update`. |
| אתר לא מתעדכן | Cache מקומי | מחקו את `_site/` והפעילו שוב. |
| 404 בעמודים | `permalink` שגוי | בדקו את כתובות ה-URL ב-`_config.yml` ובקבצים. |
| דף ריק | Front Matter חסר | ודאו שקיימים `---` בתחילת הקובץ ותכנים חובה. |

---

### 14. הרחבות מתקדמות

- **תמיכה בריבוי שפות**: השתמשו בתוספים כמו `jekyll-multiple-languages-plugin`.
- **שילוב נתונים חיצוניים**: צרפו קבצי YAML ב-`_data/` כדי לייצר רשימות דינמיות.
- **כלי כתיבה**: כתיבה ב-Markdown דרך VS Code עם תוסף `Markdown All in One`.
- **ניתוחים**: הוסיפו סקריפטים ב-`_includes/analytics.html` ומקמו ב-layout הראשי.

---

### 15. נספחים

#### 15.1 פקודות שימושיות

```shell
bundle exec jekyll build --trace   # דיבוג תקלות
bundle exec jekyll serve --drafts  # הצגת טיוטות
bundle exec jekyll clean           # ניקוי קבצי Build
```

#### 15.2 המלצות לניהול מאגר

- הגנו על ה-branch `main` עם כללים ל-PR.
- השתמשו ב-`ISSUE_TEMPLATE` וב-`PULL_REQUEST_TEMPLATE` לגילוי מוקדם של מידע חסר.
- בצעו גיבוי תקופתי (לדוגמה דרך `gh repo clone` לשרת חיצוני).

---

### 16. לסיכום

בעזרת תבנית המאגר והמדריך ניתן להקים בלוג Jekyll מלא תוך מספר דקות ולהרחיב אותו לפי הצורך. קראו את המסמכים הנלווים (`CONTRIBUTING.md`, `SECURITY.md`, `ROADMAP.md`) כדי להכיר את המדיניות והכיוונים הבאים של הפרויקט.

שאלות? פתחו Issue חדש, הצטרפו לדיון או כתבו לנו במייל. בהצלחה רבה!

