# Card Game

## התחלת פרויקט בסיסיֿ
על מנת להתחיל פרוייקט בסיסי, פתחו טרמינל על התיקייה 

```bash
npx degit <URL_REPO_HERE>
```

## התעסקות עם גיט

ראשית, פתחו פרוייקט גיט באמצעות bitbucket, gitlab או TFS ותעשו clone אליכם למחשב.
לאחר מכן, פתחו טרמינל על התיקייה.

ועכשיו, נתחיל את המשחק עם גיט:

1. תעשו קומיט לקובץ ה-gitignore בלבד

```shell
    git add .gitignore
    git commit -m "initial commit"
```

2. תעשו קומיט לשאר הקבצים

```shell
git add .
git commit -m "basic boilerplate"
```

3. תעשו push להכל

```shell
git push origin master
```

4. תעברו מ-master ל-branch אחר

> לרוב לא מפתחים קוד על המאסטר- לשם מגיע רק קוד שעבר בדיקה של גורם נוסף

```shell
git checkout -b dev
```

## הרמת פרויקט

התקינו את החבילות של הפרוייקט באופן הבא:

```shell
npm i
```

על מנת להרים שרת שיראה את השינויים הנוכחיים שלכם ויתעדכן עבור כל שינוי של קובץ, הריצו את הפקודה הבאה

```shell
npm run dev
```

היכנסו לכתובת שהוא מדפיס לכם, לרוב יהיה [`http://localhost:3000`](http://localhost:3000)

****

## קצת על הפרוייקט

כרגע יש לכם פרוייקט טייפסקריפט שאת הקוד הסופי הוא מריץ על הדפדפן. אם תריצו את הפרוייקט תוכלו לראות UI שנבנה במיוחד בשבילכם יחד עם ספרייה שעוזרת לשלוט על ה-UI בצורה הכי פשוטה שאפשר.

## דוקומנטציה של `ui@`

על מנת להשתמש ב-ui@ יש לייבא אותו בצורה הבאה:

```javascript
import gameUI from "@ui";
```

דרך gameUI מספר פונקציות מונגשות:

1. onGameStart

אירוע עבור כל פעם שהמשחק מתחיל במצב מתקדם

2. onHigheBetClick

קוד שירוץ כל פעם שלוחצים על כפתור Higher

3. onLowerBetClick

קוד שירוץ כל פעם שלוחצים על כפתור Lower

4. onBetClick

קוד שירוץ כל פעם שלוחצים על אחד הכפתורים Higher/Lower

5. onResetClick

קוד שירוץ של פעם שלוחצים על כפתור Reset

6. setScore

מציג את הניקוד

7. setCurrentCard

מציג את הקלף הנוכחי

8. winGame

משבית את המשחק ומציג שהמשתמש ניצח

9. loseGame

משבית את המשחק ומציג שהמשתמש הפסיד

10. reset

מנקה את התצוגה ומאפס אותה למצב התחלתי

11. setHigherButtonColor

מאפשר לקבוע את צבע הרקעת הטקסט וה-border של כפתור Higher

12. setLowerButtonColor

מאפשר לקבוע את צבע הרקעת הטקסט וה-border של כפתור Lower

13. setButtonsShape

מאפשר לקבוע את הצורה של כפתורי המשחק - Higher\Lower

14. advancedMode

כניסה למצב מתקדם - במצב זה לפני כל תחילת משחק יופיע חלונית הגדרות שמאפשרת לקבוע מאיפה החפיסה ומה האסטרטגיה של לקיחת הקלף.

המשחק מתחיל רק כאשר המשתמש מסיים את האינטרקציה שלו עם חלונית ההגדרות.

אפשרויות למקור החפיסה: 

- מיוצרת רנדומלית לבד
- מתוך קונפיגורציה

אפרויות לאסטרטגיית לקיחת קלף:

- הראשון בחפיסה
- רנדומלי מהחפיסה

## מבנה הפרוייקט ודגשים

הקובץ שאתם רואים על הדפדפן שרץ בסוף הוא`index.html`. בתחתית הקובץ תוכלו להבחין בתגית `<script></script>` עם הקובץ `src/main.ts` שהוא הקובץ הראשי איתו אתם עובדים.

כמה הערות על המשך העבודה: 

1. תוודאו שאתם מחלקים לקבצים - אין לעשות קובץ אחד ענק עם 500 שורות

2. תוודאו שאתם מחלקים נכון לתיקיות

3. תוודאו שאתם עושים export עבור פונקציות, משתנים, מחלקות או טייפים שאתם רוצים שהקובץ ייחצן

4. אין להתעסק עם ספריית UI או קובץ הHTML ללא אישור מהמפקדים

5. אתם מקבלים את הפרוייקט עם תרגיל מקדים - יש לעשות את התרגיל המקדים לפני שמתחילים את הפרוייקט.

7. שמרו על קוד נקי, ריווח והזחות נכונות, ותנו שמות אינדיקטיביים

8. תהנו.

## התחלת מימוש

### לוגיקה

#### CardType

צרו `enum` בשם `CardType` שיכיל את סוגי הקלפים השונים. עבור כל ערך תנו מספר - ככל שהמספר גבוה יותר כך סוג הקלף חשוב יותר מאחרים.

#### Card

צרו מחלקה בשם `Card` שתקבל 2 ערכים:

- value: ערך מספרי של הקלף
- type: סוג הקלף 

ממשו עבור המחלקה פונקציה `toString` שמציגה את ערך הקלף והסוג שלו בצורה קריאה

#### DeckBuilder

צרו מחלקה בשם `DeckBuilder` שתהיה אחראית ליצירת חפיסות קלפים. חפיסת קלפים זה מערך של מחלקת `Card`

![deckBuilder UML](./assets/DeckBuilder.png)

- למחלקה אמורה להיות פונקציה שמקבלת רשימה של ערכים מספריים ועבור כל מספר מייצרת 4 קלפים מסוגים שונים אך אותו מספר. הפונקציה שומרת את הקלפים שנוצרו בתוך משתנה של המחלקה `cards`

```typescript
addValuesToAllTypes(values: number[]):void
```

> עבור כל ערך, אם הוא לא בין 1 ל-10 אין להשתמש בו.

- למחלקה אמורה להיות פונקציה שמקבלת אובייקט JSON שהוא מערך של  אובייקטים בו כל אובייקט מייצג קלף, והיא מוסיפה את הקלפים ל-`cards`

```typescript
fromJson({type:string, value:number}[]): void
```

דוגמה לקובץ קונפיגורציה:

```JSON
[
    {"type": "HEART", "value":1},
    {"type": "HEART", "value":2},
    {"type": "HEART", "value":3},
    {"type": "HEART", "value":4},
    {"type": "HEART", "value":5},
    {"type": "CLUB", "value":1},
    {"type": "CLUB", "value":2},
    {"type": "CLUB", "value":3},
    {"type": "CLUB", "value":4},
    {"type": "CLUB", "value":5},
    {"type": "DIAMOND", "value":1},
    {"type": "DIAMOND", "value":2},
    {"type": "DIAMOND", "value":3},
    {"type": "DIAMOND", "value":4},
    {"type": "DIAMOND", "value":5}
]
```

צרו פונקציה במחלקה בשם `getDeck` שמחזירה את הקלפים שהתווספו עד כה.

```typescript
getDeck():Card[]
```
