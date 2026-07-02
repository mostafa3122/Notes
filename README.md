# Notes

These are my notes while learning **JavaScript** ⚡ and **React** ⚛️.  
 I might make mistakes 🧠, so feel free to correct me ✍️ or share feedback 💬 👨‍💻.

---

### Template Literals ` `` `

🔹 A modern way to write strings in JavaScript code  
🔹 Uses backticks ` (``) ` instead of quotes

🧠 Why use it?  
🔹 Easier to insert variables inside strings  
🔹 Cleaner and more readable code  
🔹 Multi-line strings

```js
// Old way:
const text = "Hello\nWorld";
// Template literals:
const text = `
    Hello
    World
    `;
```

---

### Ternary Operator `? :`

🔹 A shortcut for `if...else` statements

```js
condition ? expressionIfTrue : expressionIfFalse;
condition ? "true result" : "false result";

const age = 20;
const result = age >= 18 ? "Adult" : "Minor";
console.log(result); // Adult
// Template Literals with Ternary Operator
const className = `btn ${isActive ? "active" : ""}`;
```

---

### Short Circuiting

🔹 Uses `&&` and `||` operators  
🧠 Idea:  
🔹 `&&` → **runs right side if left is true** → Returns the first falsy value OR the last value if all are truthy → ( stops at frist falsy value )  
🔹 `||` → returns the **first truthy** value → ( stops at frist truthy value )

```js
console.log("JS" && 0 && "React"); // 0
console.log(null || undefined || 0 || "Default" || "Hello"); // Default
console.log("" || 0 || ("JS" && "React")); // React
{
  isLoggedIn && <Cart />;
} // “Render Cart only if the user is logged in”
```

---

### 🔍 Nullish Coalescing Operator `(??)`

🔹 The nullish coalescing operator `(??)` is used to provide a default value when something is `null` or `undefined`.  
🔹 Returns the right value only if left is `null` or `undefined`.

🧠 Difference from `||`:  
🔹 `||` treats `0`, `""`, `false`, `null` and `undefined` as falsy.  
🔹 `??` only checks `null` and `undefined`

```js
const userName = null;
const displayName = userName ?? "Anonymous";
console.log(displayName); // Anonymous
```

---

### Optional Chaining `(?.)`

🔹 Is used to safely access nested object properties without causing errors if something is `null` or `undefined`.  
🔹 👉 Prevents crashes when API data is not ready yet.  
🔹 Returns `undefined` if value is missing.

```js
const response = {
  data: {
    user: {
      name: "Mostafa",
    },
  },
};
console.log(response?.data?.user?.name); // Mostafa
console.log(response?.data?.user?.id); // undefined
```

---

### [ ] Array Destructuring

🔹 Is a way to extract values from an array and store them in variables in a clean way.  
🔹 Based on Position (index)

```js
const colors = ["red", "green", "blue"];
const [first, second, third] = colors;
console.log(first); // red

// useState is an exapmle for it
```

---

### { } Object Destructuring

🔹 Is a way to extract values from objects and store them in variables in a clean way.  
🔹 Based on Property names

```js
// Props destructuring
function UserCard({ name, age }) {
  return (
    <div>
      <h1>{name}</h1>
      <p>{age}</p>
    </div>
  );
}
```

---

### Spread Operator `(...) `

🔹 The spread operator `(...)` is used to expand elements from arrays or properties from objects.
🔹 Used for copying data without changing data or merging arrays/objects easily.

```js
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];
console.log(arr2); // [1,2,3,4]

const user = { name: "Mostafa" };
const updatedUser = { ...user, age: 22 };
console.log(updatedUser); // {Mostafa,22}
```

---

### Rest Parameter (...)

🔹 The rest parameter uses `...` to collect multiple values into one array.  
🔹 Used in function params

```js
function greet(name, age, ...hobbies) {
  console.log(name); // Mostafa
  console.log(age); // 24
  console.log(hobbies); // ["coding", "reading", "gaming"]
}

greet("Mostafa", "24", "coding", "reading", "gaming");
```

##

🔹 Rest = collect values  
🔹 Spread = expand values  
🔹 Both use `...` but behavior depends on context

```js
function createUser(name, age, ...hobbies) {
  //  rest: collects remaining arguments into an array in hobbies
  const user = {
    name,
    age,
    hobbies,
  };
  // spread: copies object and adds new property
  const updatedUser = {
    ...user,
    isActive: true,
  };

  return updatedUser;
}
const result = createUser("Mostafa", 22, "coding", "reading", "gaming");
console.log(result); // { name: "Mostafa", age: 22, hobbies: ["coding", "reading", "gaming"], isActive: true }
```

---

# HTML Interview Questions

> Front-End Interview Notes
>
> Level: Junior → Mid-Level

---

# 1. What is the difference between `<div>` and `<span>`?

## 🎯 Short Answer

`<div>` is a **Block-level element**, while `<span>` is an **Inline element**.

---

## 📖 Detailed Explanation

الفرق الأساسي بينهم هو **Display Behavior**.

### `<div>`

- Block Element.
- بيبدأ دائمًا في **new line**.
- بياخد **100% من العرض** بشكل افتراضي.
- بيستخدم كـ **Container** لتجميع عناصر كتير مع بعض.

### `<span>`

- Inline Element.
- بيفضل في نفس السطر.
- بياخد مساحة المحتوى فقط.
- بنستخدمه لتنسيق جزء صغير من النص.

---

## 💻 Example

```html
<div class="card">
  <h2>Frontend</h2>
  <p>Interview Notes</p>
</div>

<p>
  Hello
  <span style="color:red;">Mostafa</span>
</p>
```

---

## 🧠 Interview Tip

المحاور غالبًا هيكمل بـ:

- What is Block Element?
- What is Inline Element?
- What is Inline-Block?

---

## ✅ Key Points

- div → Block
- span → Inline
- Both are Non-semantic Elements.

---

# 2. What is Semantic HTML?

## 🎯 Short Answer

Semantic HTML means using HTML elements that describe the **meaning of the content** instead of using `<div>` for everything.

---

## 📖 Detailed Explanation

Semantic Elements بتوضح وظيفة كل جزء من الصفحة.

بدل ما تكتب:

```html
<div>
  <div>
    <div></div>
  </div>
</div>
```

استخدم:

- `<header>`
- `<nav>`
- `<main>`
- `<section>`
- `<article>`
- `<aside>`
- `<footer>`

وده بيساعد في:

- Better SEO
- Better Accessibility
- Cleaner Code
- Easier Maintenance

---

## 💻 Example

```html
<header>
  <nav></nav>
</header>

<main>
  <section>
    <article>Frontend Interview Notes</article>
  </section>
</main>

<footer>Copyright 2026</footer>
```

---

## 🧠 Interview Tip

لو سألك:

> Why should we use Semantic HTML?

قول:

- Search engines understand the page better.
- Screen readers can navigate the page easily.
- Code becomes more readable.
- Easier to maintain.

---

## ✅ Key Points

- Semantic = Meaningful HTML.
- Better SEO.
- Better Accessibility.
- Better Code Structure.

---

# 3. When should you use `<section>` and `<article>`?

## 🎯 Short Answer

- `<section>` represents a group of related content.
- `<article>` represents independent content that can stand alone.

---

## 📖 Detailed Explanation

### Use `<section>`

لما يكون عندك جزء من الصفحة له عنوان ومحتوى مرتبط بيه.

Examples:

- About Us
- Services
- Contact
- Features

---

### Use `<article>`

للمحتوى المستقل.

Examples:

- Blog Post
- News
- Product Card
- Forum Post
- Comment

لو أخدت الـ Article وحطيته في صفحة لوحده هيظل له معنى.

---

## 💻 Example

```html
<section>
  <h2>Latest News</h2>

  <article>AI is changing Web Development.</article>

  <article>React 20 Released.</article>
</section>
```

---

## 🧠 Interview Tip

كل Article ممكن يحتوي Sections.

لكن مش كل Section يبقى Article.

---

## ✅ Key Points

- Section → Related Content
- Article → Independent Content

---

# 4. What is the difference between `id` and `class`?

## 🎯 Short Answer

- `id` should be unique.
- `class` can be reused.

---

## 📖 Detailed Explanation

### id

كل Element المفروض يكون ليه ID مختلف.

```html
<h1 id="title"></h1>
```

بيستخدم في:

- JavaScript
- Anchor Links
- Unique Elements

---

### class

ممكن تستخدم نفس الـ Class على عدد غير محدود من العناصر.

```html
<div class="card"></div>

<div class="card"></div>

<div class="card"></div>
```

وده الأكثر استخدامًا في CSS.

---

## 💻 Example

```html
<h1 id="main-title">Frontend</h1>

<div class="card"></div>

<div class="card"></div>

<div class="card"></div>
```

---

## 🧠 Interview Tip

لو سألك:

Can two elements have the same ID?

الإجابة:

❌ No.

أما الـ Class:

✅ Yes.

---

## ✅ Key Points

- id → Unique
- class → Reusable
- CSS يعتمد غالبًا على Class.

---

# 5. What is the difference between Block, Inline, and Inline-Block?

## 🎯 Short Answer

| Type         | New Line | Width                            |
| ------------ | -------- | -------------------------------- |
| Block        | ✅       | Full Width                       |
| Inline       | ❌       | Content Only                     |
| Inline-Block | ❌       | Content + Can Set Width & Height |

---

## 📖 Detailed Explanation

### Block

- Starts on a new line.
- Takes full width.

Examples

```html
<div></div>

<p></p>

<h1></h1>

<section></section>
```

---

### Inline

- Doesn't start on a new line.
- Width equals content only.

Examples

```html
<span></span>

<a></a>

<strong></strong>

<img />
```

---

### Inline-Block

بيتصرف زي Inline لكنه يسمح باستخدام:

- width
- height
- margin
- padding

وده مفيد جدًا في تصميم Buttons أو Cards.

---

## 💻 Example

```css
button {
  display: inline-block;

  width: 200px;

  height: 50px;
}
```

---

## 🧠 Interview Tip

من أشهر الأسئلة:

Why can't width work on inline elements?

لأن Inline Elements لا تدعم width و height بشكل طبيعي.

---

## ✅ Key Points

- Block → New Line
- Inline → Same Line
- Inline-Block → Best of both

---

# 6. What is Accessibility (a11y)?

## 🎯 Short Answer

Accessibility (a11y) means building websites that **everyone can use**, including people with disabilities.

---

## 📖 Detailed Explanation

Accessibility هي إنك تخلي موقعك قابل للاستخدام لكل الناس، سواء كانوا:

- 👁️ ضعاف أو فاقدي البصر.
- 👂 ضعاف السمع.
- ⌨️ بيستخدموا Keyboard بدل الـ Mouse.
- 🧠 عندهم صعوبات في الإدراك أو التعلم.

لو الموقع معمول بشكل صحيح، هيكون سهل استخدامه بواسطة:

- Screen Readers.
- Keyboard Navigation.
- Voice Assistants.

---

## 💻 Example

❌ Bad

```html
<div onclick="login()">Login</div>
```

ليه غلط؟

- مش قابل للوصول بالكيبورد.
- Screen Reader مش هيعرف إنه Button.

---

✅ Good

```html
<button>Login</button>
```

---

مثال تاني

❌

```html
<img src="logo.png" />
```

✅

```html
<img src="logo.png" alt="Company Logo" />
```

---

## 🧠 Interview Tip

لو اتسألت:

How can you improve Accessibility?

قول:

- Use Semantic HTML.
- Add alt attributes.
- Use labels with forms.
- Maintain proper color contrast.
- Make the website keyboard accessible.
- Use ARIA attributes when needed.

---

## ✅ Key Points

- Accessibility = Make websites usable for everyone.
- Semantic HTML improves Accessibility.
- Always use alt for images.
- Use real HTML elements instead of divs.

---

# 7. Why is the `alt` attribute important for images?

## 🎯 Short Answer

The `alt` attribute provides **alternative text** for an image if it cannot be displayed or for users using Screen Readers.

---

## 📖 Detailed Explanation

الـ alt له استخدامات مهمة جدًا.

### 1. Accessibility

لو شخص بيستخدم Screen Reader، هيقرأ قيمة الـ alt بدل الصورة.

---

### 2. Image Loading Failure

لو الصورة محملتش لأي سبب.

المتصفح هيعرض النص الموجود داخل alt.

---

### 3. SEO

Google بيستخدم الـ alt لفهم محتوى الصورة.

وده بيساعد في:

- Image Search.
- SEO Ranking.

---

## 💻 Example

```html
<img src="frontend.png" alt="Frontend Roadmap" />
```

---

مثال سيئ

```html
<img src="cat.png" alt="image" />
```

---

مثال أفضل

```html
<img src="cat.png" alt="White cat sleeping on a sofa" />
```

---

## 🧠 Interview Tip

لو الصورة Decorative فقط.

اكتب

```html
alt=""
```

وليس

```html
alt="image"
```

---

## ✅ Key Points

- Accessibility.
- SEO.
- Better User Experience.
- Screen Readers.

---

# 8. What is the difference between `localStorage` and `sessionStorage`?

## 🎯 Short Answer

Both store data in the browser.

لكن الفرق في مدة الاحتفاظ بالبيانات.

---

## 📖 Detailed Explanation

### localStorage

- يخزن البيانات بدون تاريخ انتهاء.
- البيانات تظل موجودة حتى بعد غلق المتصفح.
- لازم المستخدم أو الكود يمسحها.

---

### sessionStorage

- يخزن البيانات أثناء Session واحدة فقط.
- بمجرد غلق الـ Tab أو الـ Browser يتم حذفها.

---

## 💻 Example

### localStorage

```javascript
localStorage.setItem("name", "Mostafa");

const name = localStorage.getItem("name");

localStorage.removeItem("name");
```

---

### sessionStorage

```javascript
sessionStorage.setItem("token", "123");

const token = sessionStorage.getItem("token");
```

---

## 📊 Comparison

| Feature                     | localStorage | sessionStorage |
| --------------------------- | ------------ | -------------- |
| Storage Limit               | ~5MB         | ~5MB           |
| Persist After Browser Close | ✅ Yes       | ❌ No          |
| Shared Between Tabs         | ✅ Yes       | ❌ No          |

---

## 🧠 Interview Tip

Don't store sensitive information like Passwords.

لو هتخزن Authentication Data، افهم الأول الفرق بين:

- localStorage
- Cookies
- HttpOnly Cookies

لأن ده سؤال مشهور جدًا.

---

## ✅ Key Points

- localStorage → Permanent.
- sessionStorage → Temporary.
- Both store strings only.

---

# 9. What is the difference between `defer` and `async`?

## 🎯 Short Answer

Both are used to load JavaScript without blocking HTML parsing.

لكن طريقة التنفيذ مختلفة.

---

## 📖 Detailed Explanation

### Normal Script

```html
<script src="app.js"></script>
```

المتصفح:

- يوقف قراءة HTML.
- يحمل JavaScript.
- ينفذه.
- يكمل قراءة الصفحة.

وده ممكن يبطئ تحميل الصفحة.

---

### async

```html
<script async src="app.js"></script>
```

- يبدأ تحميل الملف مع HTML.
- أول ما يخلص تحميل ينفذه فورًا.
- ممكن يوقف HTML أثناء التنفيذ.
- ترتيب التنفيذ غير مضمون.

مناسب لـ

- Analytics.
- Ads.
- Third-party Scripts.

---

### defer

```html
<script defer src="app.js"></script>
```

- يحمل الملف أثناء تحميل HTML.
- لا ينفذه إلا بعد انتهاء HTML بالكامل.
- يحافظ على ترتيب الملفات.

وده الأفضل لمعظم مشاريع Front-End.

---

## 🧠 Interview Tip

Most of the time use:

```html
defer
```

إلا لو السكربت مستقل تمامًا ومش بيعتمد على HTML أو Scripts أخرى.

---

## ✅ Key Points

- async → Faster but unordered.
- defer → Ordered and waits for HTML.
- defer is preferred for most projects.

---

# 10. What is the difference between `meta viewport` and `meta charset`?

## 🎯 Short Answer

- `meta charset` specifies the character encoding.
- `meta viewport` controls how the page is displayed on mobile devices.

---

## 📖 Detailed Explanation

### meta charset

```html
<meta charset="UTF-8" />
```

بيحدد ترميز الأحرف.

بدونه ممكن العربي يظهر بالشكل ده:

```
Ù…Ø±Ø­Ø¨Ø§
```

لذلك نستخدم دائمًا:

```html
UTF-8
```

لأنه يدعم معظم لغات العالم.

---

### meta viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

بيخلي الموقع Responsive.

معنى القيم:

- width=device-width → استخدم عرض الجهاز.
- initial-scale=1 → لا تعمل Zoom عند الفتح.

---

## 💻 Example

```html
<head>
  <meta charset="UTF-8" />

  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</head>
```

---

## 🧠 Interview Tip

بدون `meta viewport`:

- الموقع هيظهر مصغر على الموبايل.
- الـ Responsive Design مش هيشتغل بالشكل المتوقع.

---

## ✅ Key Points

- charset → Character Encoding.
- viewport → Responsive Design.
- كلاهما يكتب داخل `<head>`.

---

# 🎉 HTML Interview Summary

## أهم الأسئلة اللي بتتكرر في المقابلات

- Difference between div and span.
- Semantic HTML.
- Section vs Article.
- id vs class.
- Block vs Inline vs Inline-Block.
- Accessibility.
- alt Attribute.
- localStorage vs sessionStorage.
- async vs defer.
- meta charset vs viewport.

---

# JavaScript Interview Questions

> Front-End Interview Notes
>
> Level: Junior → Mid-Level

---

# 1. What is the difference between `==` and `===`?

## 🎯 Short Answer

- `==` compares **values only** after type conversion.
- `===` compares **both value and data type** without type conversion.

---

## 📖 Detailed Explanation

في JavaScript يوجد نوعان من المقارنة.

### `==` (Loose Equality)

قبل المقارنة، JavaScript بتحاول تحول النوع (Type Coercion).

مثال:

```javascript
5 == "5";
```

النتيجة

```javascript
true;
```

لأن JavaScript حولت `"5"` إلى Number.

---

### `===` (Strict Equality)

لا يتم تحويل النوع.

يجب أن تكون القيمة والنوع متطابقين.

```javascript
5 === "5";
```

النتيجة

```javascript
false;
```

لأن:

- Number ≠ String

---

## 💻 Example

```javascript
console.log(5 == "5"); // true

console.log(5 === "5"); // false

console.log(true == 1); // true

console.log(true === 1); // false
```

---

## 🧠 Interview Tip

Always prefer

```javascript
===
```

لأنه يمنع أخطاء ناتجة عن Type Coercion.

---

## ✅ Key Points

- `==` → Value Only
- `===` → Value + Type
- Use `===` in almost all cases.

---

# 2. What is the difference between `null` and `undefined`?

## 🎯 Short Answer

- `undefined` means a variable has been declared but not assigned a value.
- `null` means the value is intentionally empty.

---

## 📖 Detailed Explanation

### undefined

JavaScript نفسها هي اللي بتحط القيمة دي.

```javascript
let name;

console.log(name);
```

النتيجة

```javascript
undefined;
```

---

### null

المبرمج هو اللي بيحددها.

يعني:

"لا توجد قيمة حاليًا."

```javascript
let user = null;
```

---

## 💻 Example

```javascript
let age;

console.log(age);

let phone = null;

console.log(phone);
```

---

## 📊 Comparison

| null                    | undefined                 |
| ----------------------- | ------------------------- |
| Assigned by Developer   | Assigned by JavaScript    |
| Intentional Empty Value | Variable has no value yet |

---

## 🧠 Interview Tip

اسأل نفسك:

هل JavaScript هي اللي حطت القيمة؟

➡️ undefined

ولا أنا اللي حددتها؟

➡️ null

---

## ✅ Key Points

- undefined → Not Assigned.
- null → Empty Value.
- Both represent absence of value.

---

# 3. What is the difference between `var`, `let`, and `const`?

## 🎯 Short Answer

| var            | let          | const           |
| -------------- | ------------ | --------------- |
| Function Scope | Block Scope  | Block Scope     |
| Can Reassign   | Can Reassign | Cannot Reassign |

---

## 📖 Detailed Explanation

### var

قديم.

مش بنستخدمه تقريبًا في المشاريع الحديثة.

مشكلته:

- Function Scope
- Hoisting
- يمكن إعادة تعريفه.

---

### let

الأفضل للمتغيرات اللي هتتغير.

```javascript
let age = 20;

age = 21;
```

---

### const

للثوابت.

```javascript
const pi = 3.14;
```

لا يمكن إعادة إسناد قيمة جديدة.

---

## 💻 Example

```javascript
var x = 5;

let y = 10;

const z = 15;
```

---

## 🧠 Interview Tip

استخدم

- const by default.
- let if the value will change.
- Avoid var.

---

## ✅ Key Points

- var → Old
- let → Mutable
- const → Immutable Binding

---

# 4. What is Hoisting?

## 🎯 Short Answer

Hoisting is JavaScript's behavior of moving declarations to the top of their scope before execution.

---

## 📖 Detailed Explanation

JavaScript بتقرأ الكود على مرحلتين.

1. Memory Creation Phase.
2. Execution Phase.

في أول مرحلة يتم رفع (Hoist) التصريحات.

---

مثال

```javascript
console.log(name);

var name = "Mostafa";
```

تصبح داخليًا

```javascript
var name;

console.log(name);

name = "Mostafa";
```

لذلك الناتج

```javascript
undefined;
```

---

أما

```javascript
let;
```

و

```javascript
const
```

فيتم عمل Hoisting لهم أيضًا.

لكن لا يمكن استخدامهم قبل تعريفهم بسبب

Temporal Dead Zone (TDZ).

---

## 💻 Example

```javascript
console.log(age);

let age = 20;
```

النتيجة

```
ReferenceError
```

---

## 🧠 Interview Tip

Hoisting يحدث مع:

- Variables
- Functions

لكن يختلف حسب نوع التصريح.

---

## ✅ Key Points

- var → undefined
- let → ReferenceError
- const → ReferenceError

---

# 5. What is Closure?

## 🎯 Short Answer

Closure is when an inner function remembers variables from its outer function even after the outer function has finished executing.

---

## 📖 Detailed Explanation

الـ Closure من أهم مفاهيم JavaScript.

الفكرة ببساطة:

Function داخل Function.

الـ Inner Function يقدر يوصل لمتغيرات الـ Outer Function حتى بعد انتهاء تنفيذها.

---

## 💻 Example

```javascript
function counter() {
  let count = 0;

  return function () {
    count++;

    return count;
  };
}

const increment = counter();

console.log(increment());

console.log(increment());

console.log(increment());
```

Output

```
1

2

3
```

---

## لماذا؟

لأن الـ Inner Function احتفظ بالمتغير

```
count
```

داخل الـ Memory.

---

## أشهر استخدامات Closure

- Data Privacy
- Factory Functions
- Event Handlers
- Callbacks

---

## 🧠 Interview Tip

لو فهمت Closure كويس.

هتفهم بعدها بسهولة:

- React Hooks
- useState
- Event Listeners

---

## ✅ Key Points

- Inner Function remembers Outer Variables.
- Variables stay alive.
- Very common in React.

---

# 6. How does JavaScript handle Asynchronous Code?

## 🎯 Short Answer

JavaScript is **Single-Threaded**, but it can handle asynchronous operations using:

- Web APIs
- Callback Queue
- Event Loop
- Promises
- Async/Await

---

## 📖 Detailed Explanation

ناس كتير فاكرة إن JavaScript بتنفذ أكتر من حاجة في نفس الوقت.

الحقيقة:

JavaScript نفسها عندها **Single Thread** يعني بتنـفذ **Task واحدة في كل مرة**.

طيب إزاي بتشغل:

- API Requests
- Timers
- Events

من غير ما توقف الصفحة؟

عن طريق الـ Browser.

الـ Browser يوفر حاجة اسمها **Web APIs**.

لما تكتب:

```javascript
setTimeout(() => {
  console.log("Done");
}, 2000);
```

الـ Browser هو اللي يمسك الـ Timer.

أما JavaScript تكمل تنفيذ باقي الكود.

بعد انتهاء الوقت...

الـ Callback تروح إلى:

```
Callback Queue
```

ثم الـ Event Loop يقرر إمتى تدخل إلى الـ Call Stack.

---

## 💻 Example

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timer");
}, 2000);

console.log("End");
```

Output

```
Start

End

Timer
```

---

## 🧠 Interview Tip

المحاور غالبًا هيكمل:

- What is Event Loop?
- What is Callback Queue?
- Why is JavaScript Single Threaded?

---

## ✅ Key Points

- JavaScript is Single Threaded.
- Browser handles async tasks.
- Event Loop manages execution.
- Promises and Async/Await are built on this mechanism.

---

# 7. What is the Event Loop?

## 🎯 Short Answer

The Event Loop continuously checks whether the **Call Stack** is empty. If it is, it moves tasks from the **Callback Queue** to the Call Stack.

---

## 📖 Detailed Explanation

تخيل إن عندك:

```
Call Stack
```

وده مكان تنفيذ الكود.

ولديك:

```
Callback Queue
```

وده مكان انتظار الـ Async Tasks.

الـ Event Loop شغال باستمرار.

كل شوية يسأل:

```
هل الـ Call Stack فاضي؟
```

لو الإجابة نعم.

يدخل أول Callback للتنفيذ.

---

## 💻 Example

```javascript
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

console.log("C");
```

Output

```
A

C

B
```

حتى لو الوقت صفر.

الـ Callback لازم تستنى لحد ما الـ Stack يفضى.

---

## 🧠 Interview Tip

احفظ الجملة دي.

> Event Loop moves callbacks from the Callback Queue to the Call Stack when the Call Stack becomes empty.

---

## ✅ Key Points

- Event Loop never stops.
- Checks the Call Stack.
- Executes callbacks when possible.

---

# 8. What is the difference between Call Stack and Callback Queue?

## 🎯 Short Answer

- Call Stack executes synchronous code.
- Callback Queue stores asynchronous callbacks waiting to execute.

---

## 📖 Detailed Explanation

### Call Stack

أي Function بتناديها.

بتدخل هنا.

```javascript
login();

fetchData();

showProfile();
```

كل Function تدخل فوق اللي قبلها.

ولما تخلص.

تخرج من الـ Stack.

---

### Callback Queue

أي Callback جاية من:

- setTimeout
- setInterval
- DOM Events

تستنى هنا.

لحد ما الـ Event Loop ينقلها للـ Stack.

---

## 📊 Comparison

| Call Stack    | Callback Queue |
| ------------- | -------------- |
| Executes Code | Waits          |
| LIFO          | FIFO           |
| Sync          | Async          |

---

## 🧠 Interview Tip

الترتيب الحقيقي

```
Web APIs

↓

Callback Queue

↓

Event Loop

↓

Call Stack
```

---

## ✅ Key Points

- Stack executes.
- Queue waits.
- Event Loop connects both.

---

# 9. What is the difference between Arrow Function and Regular Function?

## 🎯 Short Answer

Arrow Functions are shorter and don't have their own `this`, while Regular Functions have their own `this`.

---

## 📖 Detailed Explanation

### Regular Function

```javascript
function sayHello() {
  console.log("Hello");
}
```

---

### Arrow Function

```javascript
const sayHello = () => {
  console.log("Hello");
};
```

---

الفرق الحقيقي مش في الكتابة.

الفرق في:

```
this
```

الـ Arrow Function لا تنشئ this جديد.

بل تستخدم this من الـ Parent Scope.

---

### Regular Function

```javascript
const user = {
  name: "Mostafa",

  show: function () {
    console.log(this.name);
  },
};
```

---

### Arrow Function

```javascript
const user = {
  name: "Mostafa",

  show: () => {
    console.log(this.name);
  },
};
```

النتيجة

```
undefined
```

لأن this ليست الـ Object.

---

## 🧠 Interview Tip

Don't use Arrow Functions as Object Methods.

---

## ✅ Key Points

- Short Syntax.
- No own this.
- No arguments object.
- Cannot be used as Constructors.

---

# 10. When should you use `map()`, `filter()`, and `reduce()`?

## 🎯 Short Answer

- map → Transform Data.
- filter → Filter Data.
- reduce → Produce One Final Value.

---

## 📖 Detailed Explanation

### map()

ترجع Array جديدة بنفس الطول.

لكن بعد تعديل كل عنصر.

```javascript
const nums = [1, 2, 3];

const doubled = nums.map((num) => num * 2);
```

Output

```javascript
[2, 4, 6];
```

---

### filter()

ترجع العناصر التي تحقق شرطًا معينًا.

```javascript
const nums = [1, 2, 3, 4];

const even = nums.filter((num) => num % 2 === 0);
```

Output

```javascript
[2, 4];
```

---

### reduce()

تحول الـ Array كلها إلى قيمة واحدة.

مثل:

- Sum
- Average
- Object
- Count

```javascript
const nums = [1, 2, 3, 4];

const total = nums.reduce((acc, current) => {
  return acc + current;
}, 0);
```

Output

```javascript
10;
```

---

## 📊 Comparison

| Method | Returns        |
| ------ | -------------- |
| map    | New Array      |
| filter | Filtered Array |
| reduce | Single Value   |

---

## 💻 Real React Example

```javascript
const completedTasks = tasks

  .filter((task) => task.completed)

  .map((task) => task.title);
```

---

## 🧠 Interview Tip

من أشهر أسئلة الانترفيو:

> Can I replace map with forEach?

الإجابة:

تقريبًا لا.

لأن:

- map returns a new array.
- forEach returns undefined.

---

## ✅ Key Points

- map → Modify.
- filter → Select.
- reduce → Calculate.
- الثلاثة لا يغيروا الـ Original Array.

---

# 11. What is the difference between Shallow Copy and Deep Copy?

## 🎯 Short Answer

- **Shallow Copy** copies only the first level of an object.
- **Deep Copy** copies the entire object, including all nested objects and arrays.

---

## 📖 Detailed Explanation

لما تعمل Copy لـ Object أو Array، فيه طريقتين.

### Shallow Copy

بيعمل نسخة من المستوى الأول فقط.

لو الـ Object فيه Object تاني جواه، الاتنين هيشيروا لنفس الـ Reference.

يعني لو عدلت في الـ Nested Object، النسختين هيتأثروا.

---

### Example

```javascript
const user = {
  name: "Mostafa",
  address: {
    city: "Cairo",
  },
};

const copy = { ...user };

copy.address.city = "Alex";

console.log(user.address.city);
```

Output

```javascript
Alex;
```

ليه؟

لأن `address` اتنسخ بالـ Reference.

---

### Deep Copy

بيعمل نسخة جديدة بالكامل.

كل Object و Array بيكون ليه Reference جديد.

---

### Example

```javascript
const user = {
  name: "Mostafa",
  address: {
    city: "Cairo",
  },
};

const copy = structuredClone(user);

copy.address.city = "Alex";

console.log(user.address.city);
```

Output

```javascript
Cairo;
```

---

## أشهر طرق الـ Copy

### Shallow Copy

```javascript
const copy = { ...obj };

const copy = Object.assign({}, obj);
```

---

### Deep Copy

```javascript
const copy = structuredClone(obj);
```

أو

```javascript
const copy = JSON.parse(JSON.stringify(obj));
```

> لكن JSON Method لا تدعم:
>
> - Date
> - Map
> - Set
> - Function
> - undefined

لذلك `structuredClone()` هي الأفضل في المتصفحات الحديثة.

---

## 🧠 Interview Tip

Spread Operator (`...`) لا يعمل Deep Copy.

دي من أشهر الأخطاء في الانترفيو.

---

## ✅ Key Points

- Spread = Shallow Copy.
- structuredClone() = Deep Copy.
- Nested Objects تحتاج Deep Copy.

---

# 12. What is Scope? What are its types?

## 🎯 Short Answer

Scope determines **where a variable can be accessed**.

---

## 📖 Detailed Explanation

Scope يعني مكان رؤية أو استخدام المتغير.

لو المتغير خارج الـ Scope، هيظهر Error.

---

## Types of Scope

### 1. Global Scope

أي Variable معرف خارج أي Function أو Block.

يمكن الوصول إليه من أي مكان.

```javascript
let username = "Mostafa";

function show() {
  console.log(username);
}
```

---

### 2. Function Scope

أي Variable داخل Function.

لا يمكن الوصول إليه من الخارج.

```javascript
function login() {
  let password = "123";
}
```

```javascript
console.log(password);
```

Output

```
ReferenceError
```

---

### 3. Block Scope

أي Variable داخل

```javascript
{
}
```

ويعمل فقط مع:

- let
- const

```javascript
if (true) {
  let age = 20;
}

console.log(age);
```

Output

```
ReferenceError
```

---

## 🧠 Interview Tip

```
var
```

ليس Block Scoped.

أما

```
let

const
```

فهما Block Scoped.

---

## ✅ Key Points

- Global Scope.
- Function Scope.
- Block Scope.
- Prefer let & const.

---

# 13. What is the difference between Synchronous and Asynchronous?

## 🎯 Short Answer

- Synchronous → Code executes line by line.
- Asynchronous → Some tasks can finish later without blocking the main thread.

---

## 📖 Detailed Explanation

### Synchronous

كل سطر ينتظر السطر اللي قبله.

```javascript
console.log("A");

console.log("B");

console.log("C");
```

Output

```
A

B

C
```

---

### Asynchronous

بعض العمليات تحتاج وقت.

مثل:

- API Calls
- Timers
- File Uploads

بدل ما توقف الصفحة.

JavaScript تكمل تنفيذ باقي الكود.

---

## Example

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Done");
}, 2000);

console.log("End");
```

Output

```
Start

End

Done
```

---

## Real Examples

### Synchronous

- Math Operations
- Loops
- Variable Assignment

---

### Asynchronous

- fetch()
- Axios
- setTimeout()
- setInterval()
- addEventListener()

---

## 🧠 Interview Tip

JavaScript ليست Multi-threaded.

هي Single-threaded.

لكن المتصفح يساعدها باستخدام:

- Web APIs
- Event Loop

---

## ✅ Key Points

- Sync = Wait.
- Async = Don't Wait.
- Async improves User Experience.

---

# 14. How do you handle errors using `try...catch`?

## 🎯 Short Answer

`try...catch` allows you to catch runtime errors and prevent your application from crashing.

---

## 📖 Detailed Explanation

بدل ما البرنامج يقف عند أول Error.

تقدر تمسك الخطأ وتتفاعل معاه.

---

### Syntax

```javascript
try {
  // Code
} catch (error) {
  // Handle Error
}
```

---

## Example

```javascript
try {
  console.log(user.name);
} catch (error) {
  console.log("Something went wrong.");
}
```

Output

```
Something went wrong.
```

---

## Example with JSON

```javascript
try {
  const user = JSON.parse("{");
} catch (error) {
  console.log(error.message);
}
```

---

## finally

ينفذ سواء حصل Error أو لا.

```javascript
try {
  console.log("Start");
} catch (error) {
  console.log(error);
} finally {
  console.log("Finished");
}
```

Output

```
Start

Finished
```

---

## throw

تقدر تنشئ Error بنفسك.

```javascript
function login(age) {
  if (age < 18) {
    throw new Error("Age must be 18 or older.");
  }
}
```

---

## 🧠 Interview Tip

في React أو Next.js.

استخدم try...catch مع:

- fetch()
- Axios
- async/await

مثال

```javascript
try {
  const response = await fetch(url);
} catch (error) {
  toast.error(error.message);
}
```

---

## ✅ Key Points

- try → Code that may fail.
- catch → Handle errors.
- finally → Always runs.
- throw → Create custom errors.

---

# 🎉 JavaScript Interview Summary

## أهم الأسئلة اللي بتتكرر

- == vs ===
- null vs undefined
- var vs let vs const
- Hoisting
- Closure
- Asynchronous JavaScript
- Event Loop
- Call Stack vs Callback Queue
- Arrow Function vs Regular Function
- map vs filter vs reduce
- Shallow Copy vs Deep Copy
- Scope
- Sync vs Async
- try...catch

## 🚀 JavaScript Interview Roadmap

إذا فهمت المواضيع دي كويس، هتكون جاهز لمعظم مقابلات الـ Front-End:

- Variables & Data Types
- Functions
- Scope
- Hoisting
- Closures
- Objects & Arrays
- Array Methods
- Promises
- Async/Await
- Event Loop
- Error Handling
- ES6 Features

---

# CSS Interview Questions

> Front-End Interview Notes
>
> Level: Junior → Mid-Level

---

# 1. How does the CSS Box Model work?

## 🎯 Short Answer

Every HTML element is treated as a **box** consisting of:

- Content
- Padding
- Border
- Margin

---

## 📖 Detailed Explanation

أي Element في HTML عبارة عن Box.

الـ Box Model بيتكون من 4 أجزاء:

```
+---------------------------+
|          Margin           |
|  +---------------------+  |
|  |      Border         |  |
|  |  +---------------+  |  |
|  |  |    Padding    |  |  |
|  |  | +-----------+ |  |  |
|  |  | | Content   | |  |  |
|  |  | +-----------+ |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

---

### 1. Content

هو المحتوى نفسه.

- Text
- Image
- Button

---

### 2. Padding

مسافة داخلية.

بين الـ Content والـ Border.

```css
padding: 20px;
```

---

### 3. Border

الإطار حول العنصر.

```css
border: 2px solid black;
```

---

### 4. Margin

مسافة خارجية.

تفصل العنصر عن العناصر الأخرى.

```css
margin: 20px;
```

---

## 💻 Example

```css
.card {
  width: 300px;

  padding: 20px;

  border: 2px solid #333;

  margin: 30px;
}
```

---

## 🧠 Interview Tip

السؤال المشهور:

What is the actual width?

```css
width: 300px;

padding: 20px;

border: 5px;
```

الإجابة

```
350px
```

لأن

```
300

+20

+20

+5

+5

=
350px
```

إلا إذا استخدمت

```css
box-sizing: border-box;
```

---

## ✅ Key Points

- Content
- Padding
- Border
- Margin
- Learn box-sizing.

---

# 2. What is the difference between Flexbox and Grid?

## 🎯 Short Answer

- Flexbox → One-dimensional Layout.
- Grid → Two-dimensional Layout.

---

## 📖 Detailed Explanation

### Flexbox

يتعامل مع:

- Row

أو

- Column

فقط.

مناسب لـ:

- Navbar
- Cards
- Buttons
- Centering

---

### Grid

يتعامل مع:

Rows

و

Columns

في نفس الوقت.

مناسب لـ:

- Dashboards
- Gallery
- Complex Layouts

---

## 💻 Example

### Flex

```css
.container {
  display: flex;

  justify-content: center;

  align-items: center;
}
```

---

### Grid

```css
.container {
  display: grid;

  grid-template-columns: repeat(3, 1fr);

  gap: 20px;
}
```

---

## 📊 Comparison

| Flexbox        | Grid           |
| -------------- | -------------- |
| One Direction  | Two Directions |
| Easy Alignment | Complex Layout |
| Components     | Whole Page     |

---

## 🧠 Interview Tip

احفظ الجملة دي.

> Flexbox is for Components.

> Grid is for Layouts.

---

## ✅ Key Points

- Flex → Row or Column.
- Grid → Rows + Columns.

---

# 3. How do you build a Responsive Layout?

## 🎯 Short Answer

Responsive Design means making the website look good on all screen sizes.

---

## 📖 Detailed Explanation

أهم أدوات الـ Responsive

### 1. Media Queries

```css
@media (max-width: 768px) {
}
```

---

### 2. Flexbox

يسهل ترتيب العناصر.

---

### 3. CSS Grid

ممتاز للـ Layout.

---

### 4. Relative Units

استخدم

```
%

rem

vw

vh
```

بدل

```
px
```

كلما أمكن.

---

### 5. Responsive Images

```css
img {
  max-width: 100%;

  height: auto;
}
```

---

## 💻 Example

```css
.container {
  display: flex;

  flex-wrap: wrap;

  gap: 20px;
}
```

---

## 🧠 Interview Tip

أهم Meta Tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

بدونه الـ Responsive هيكون سيئ.

---

## ✅ Key Points

- Flexbox.
- Grid.
- Media Queries.
- Relative Units.

---

# 4. What is the difference between `display: none` and `visibility: hidden`?

## 🎯 Short Answer

- `display:none` removes the element completely.
- `visibility:hidden` hides the element but keeps its space.

---

## 📖 Detailed Explanation

### display:none

العنصر:

- يختفي.
- لا يحجز مكان.
- كأنه غير موجود.

---

### visibility:hidden

العنصر:

- يختفي.
- لكن يظل يحجز مكانه.

---

## 💻 Example

```css
.box {
  display: none;
}
```

---

```css
.box {
  visibility: hidden;
}
```

---

## 📊 Comparison

| display:none        | visibility:hidden |
| ------------------- | ----------------- |
| Hidden              | Hidden            |
| No Space            | Keeps Space       |
| Removed From Layout | Still In Layout   |

---

## 🧠 Interview Tip

السؤال الشهير:

Which one affects Layout?

الإجابة

```
visibility:hidden
```

لأنه يحتفظ بالمكان.

---

## ✅ Key Points

- display:none removes.
- visibility:hidden hides only.

---

# 5. What is CSS Specificity?

## 🎯 Short Answer

Specificity determines which CSS rule has the highest priority.

---

## 📖 Detailed Explanation

لما أكثر من Rule تستهدف نفس العنصر.

المتصفح يختار الأعلى في الأولوية.

الترتيب من الأعلى للأقل:

```
Inline Style

↓

ID

↓

Class

↓

Element
```

---

## 💻 Example

```css
#title {
  color: red;
}

.title {
  color: blue;
}

h1 {
  color: green;
}
```

```html
<h1 id="title" class="title">Hello</h1>
```

Output

```
Red
```

لأن

```
ID
```

أعلى.

---

## Specificity Order

| Selector     | Priority |
| ------------ | -------- |
| Inline Style | Highest  |
| ID           | High     |
| Class        | Medium   |
| Element      | Low      |

---

## 🧠 Interview Tip

تجنب استخدام

```css
!important
```

إلا عند الضرورة.

لأنه يجعل صيانة الكود أصعب.

---

## ✅ Key Points

- ID > Class > Element.
- Inline أعلى من الجميع.
- Avoid `!important`.

---

# 6. What is the difference between `position: relative` and `position: absolute`?

## 🎯 Short Answer

- `position: relative` moves the element relative to **its original position**.
- `position: absolute` removes the element from the normal document flow and positions it relative to the **nearest positioned parent**.

---

## 📖 Detailed Explanation

### position: relative

العنصر يفضل موجود في مكانه الطبيعي داخل الصفحة.

لكن تقدر تحركه باستخدام:

- top
- right
- bottom
- left

بدون ما يخرج من الـ Layout.

---

### Example

```css
.box {
  position: relative;

  top: 20px;

  left: 30px;
}
```

العنصر اتحرك.

لكن مكانه الأصلي مازال محجوز.

---

### position: absolute

العنصر يخرج من الـ Normal Flow.

ولا يحجز مكان داخل الصفحة.

ويبدأ يبحث عن أقرب Parent عنده:

```css
position: relative;
```

ولو ملقاش.

هيتحرك بالنسبة للـ Viewport.

---

## 💻 Example

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  position: relative;

  width: 300px;

  height: 300px;
}

.child {
  position: absolute;

  top: 20px;

  right: 20px;
}
```

---

## 📊 Comparison

| Relative           | Absolute                              |
| ------------------ | ------------------------------------- |
| Keeps Space        | Doesn't Keep Space                    |
| Relative to itself | Relative to nearest positioned parent |
| Still in Layout    | Removed from Layout                   |

---

## 🧠 Interview Tip

من أشهر الأسئلة:

Why do we put

```css
position: relative;
```

on the parent?

الإجابة:

حتى يكون مرجعًا للـ Absolute Element.

---

## ✅ Key Points

- Relative → Keeps Position.
- Absolute → Removed from Layout.
- Absolute searches for nearest positioned parent.

---

# 7. What is the difference between `position: fixed` and `position: sticky`?

## 🎯 Short Answer

- `fixed` stays fixed relative to the viewport.
- `sticky` behaves like relative until a certain scroll position, then becomes fixed.

---

## 📖 Detailed Explanation

### Fixed

العنصر يثبت في الشاشة.

حتى لو عملت Scroll.

---

## Example

```css
header {
  position: fixed;

  top: 0;

  left: 0;

  width: 100%;
}
```

وده مشهور جدًا مع:

- Navbar
- Chat Button
- Scroll To Top Button

---

### Sticky

في البداية.

يتصرف كأنه Relative.

لكن عندما تصل إليه أثناء الـ Scroll.

يتحول إلى Fixed.

---

## Example

```css
.sidebar {
  position: sticky;

  top: 20px;
}
```

---

## 📊 Comparison

| Fixed                | Sticky                 |
| -------------------- | ---------------------- |
| Always Fixed         | Fixed after scrolling  |
| Relative to Viewport | Relative to Parent     |
| Removed from Flow    | Behaves normally first |

---

## 🧠 Interview Tip

أفضل استخدامات

Fixed

- Navbar
- WhatsApp Button
- Floating Action Button

أفضل استخدامات

Sticky

- Table Headers
- Sidebar
- Categories List

---

## ✅ Key Points

- Fixed → Always Fixed.
- Sticky → Fixed only when needed.

---

# 8. What is the difference between `margin` and `padding`?

## 🎯 Short Answer

- Margin = Outside Space.
- Padding = Inside Space.

---

## 📖 Detailed Explanation

### Margin

المسافة خارج العنصر.

تفصل العنصر عن العناصر الأخرى.

```css
margin: 20px;
```

---

### Padding

المسافة داخل العنصر.

بين المحتوى والـ Border.

```css
padding: 20px;
```

---

## 💻 Example

```css
.card {
  padding: 20px;

  margin: 30px;
}
```

---

### Visualization

```
Margin

+----------------------+

Border

+------------------+

Padding

+--------------+

Content

+----------+
```

---

## 🧠 Interview Tip

لو زودت

```css
padding
```

هيكبر العنصر.

أما

```css
margin
```

فقط يبعده عن العناصر الأخرى.

---

## ✅ Key Points

- Margin → Outside.
- Padding → Inside.
- Padding affects element size.

---

# 9. What is the difference between `em` and `rem`?

## 🎯 Short Answer

- `em` depends on the parent font size.
- `rem` depends on the root (`html`) font size.

---

## 📖 Detailed Explanation

### rem

يعتمد على

```css
html
```

إذا كان

```css
html {
  font-size: 16px;
}
```

فإن

```css
2rem
```

تساوي

```
32px
```

---

### em

يعتمد على الـ Parent.

لو الأب حجمه

```
20px
```

فإن

```css
2em
```

تساوي

```
40px
```

---

## 💻 Example

```css
html {
  font-size: 16px;
}

h1 {
  font-size: 2rem;
}
```

---

```css
.parent {
  font-size: 20px;
}

.child {
  font-size: 2em;
}
```

---

## 🧠 Interview Tip

في أغلب المشاريع الحديثة.

استخدم

```
rem
```

لأنه أكثر استقرارًا.

---

## ✅ Key Points

- rem → Root.
- em → Parent.
- rem is recommended.

---

# 10. What are different ways to center elements in CSS?

## 🎯 Short Answer

There are multiple ways to center elements depending on the situation.

---

## 📖 Method 1 — Flexbox ⭐ (Recommended)

```css
.container {
  display: flex;

  justify-content: center;

  align-items: center;
}
```

أفضل طريقة لمعظم الحالات.

---

## 📖 Method 2 — Grid ⭐

```css
.container {
  display: grid;

  place-items: center;
}
```

أسهل طريقة لو بتستخدم Grid.

---

## 📖 Method 3 — Margin Auto

للعناصر الـ Block.

```css
.box {
  width: 300px;

  margin: auto;
}
```

---

## 📖 Method 4 — Absolute + Transform

```css
.box {
  position: absolute;

  top: 50%;

  left: 50%;

  transform: translate(-50%, -50%);
}
```

مفيدة في الـ Modals والـ Popups.

---

## 📖 Method 5 — Text Align

لتوسيط النص فقط.

```css
text-align: center;
```

---

## 📖 Method 6 — Line Height

لتوسيط النص رأسيًا (في حالات بسيطة).

```css
height: 100px;

line-height: 100px;
```

---

## 📊 Comparison

| Method               | Best For         |
| -------------------- | ---------------- |
| Flexbox              | Components       |
| Grid                 | Layouts          |
| Margin Auto          | Block Elements   |
| Absolute + Transform | Modal            |
| Text Align           | Text             |
| Line Height          | Single Line Text |

---

## 🧠 Interview Tip

لو سألك:

What's the best way to center an element?

الإجابة:

استخدم Flexbox.

```css
display: flex;

justify-content: center;

align-items: center;
```

---

## ✅ Key Points

- Flexbox is the most common.
- Grid is the easiest.
- Margin Auto centers block elements.
- Absolute is useful for modals.

---

# 🎉 CSS Interview Summary

## أكثر الأسئلة شيوعًا في مقابلات الـ Front-End

- CSS Box Model
- Flexbox vs Grid
- Responsive Design
- display:none vs visibility:hidden
- CSS Specificity
- position: relative vs absolute
- position: fixed vs sticky
- margin vs padding
- em vs rem
- Centering Elements

## 🚀 CSS Interview Roadmap

إذا فهمت المواضيع دي كويس، هتكون جاهز لمعظم مقابلات الـ Front-End:

- Selectors
- Box Model
- Display
- Position
- Flexbox
- Grid
- Responsive Design
- Units (px, %, em, rem, vw, vh)
- Specificity
- Transitions & Animations
- Media Queries
- CSS Variables
- Pseudo Classes & Pseudo Elements

---

# Performance & Optimization Interview Questions

> Front-End Interview Notes
>
> Level: Junior → Mid-Level

---

# 1. How can you improve website performance?

## 🎯 Short Answer

Website Performance can be improved by reducing the amount of work the browser needs to do.

---

## 📖 Detailed Explanation

لما المستخدم يفتح الموقع، المتصفح بيعمل حاجات كتير:

- Download HTML
- Download CSS
- Download JavaScript
- Download Images
- Render Page

كل ما تقلل حجم الملفات وعدد الطلبات (Requests)، الموقع هيكون أسرع.

---

## أهم طرق تحسين الـ Performance

### 1. Optimize Images

استخدم صور بحجم مناسب.

بدل

```
5 MB
```

خليها

```
200 KB
```

أو استخدم:

- WebP
- AVIF

---

### 2. Minify CSS & JavaScript

احذف:

- Spaces
- Comments
- Unused Code

بدل

```javascript
const name = "Mostafa";
```

قد تصبح

```javascript
const n = "Mostafa";
```

---

### 3. Lazy Loading

حمل الصور عند الحاجة فقط.

بدل تحميل كل الصور مرة واحدة.

---

### 4. Code Splitting

حمل الجزء المطلوب فقط من التطبيق.

وده موجود في:

- React
- Next.js
- Vite

---

### 5. Caching

احتفظ بالملفات داخل Browser.

بدل تحميلها كل مرة.

---

### 6. Reduce HTTP Requests

بدل:

```
100 Images
```

اجعلها:

```
20 Images
```

---

### 7. Remove Unused CSS & JS

لا تحمل Libraries لا تستخدمها.

---

### 8. Compress Files

استخدم

- Gzip
- Brotli

لتقليل حجم الملفات.

---

## 🧠 Interview Tip

لو سألك:

How would you improve a slow website?

اذكر على الأقل:

- Image Optimization
- Lazy Loading
- Code Splitting
- Minification
- Caching

---

## ✅ Key Points

- Optimize Images.
- Minify Files.
- Lazy Loading.
- Code Splitting.
- Caching.
- Compression.

---

# 2. How does Lazy Loading work?

## 🎯 Short Answer

Lazy Loading means loading resources **only when they are needed**, instead of loading everything at once.

---

## 📖 Detailed Explanation

تخيل عندك صفحة فيها:

```
100 Images
```

بدل تحميلهم كلهم.

المتصفح يحمل أول الصور الظاهرة فقط.

ولما المستخدم يعمل Scroll.

يحمل باقي الصور.

وده يقلل:

- Initial Loading Time
- Bandwidth Usage

---

## 💻 Example

### HTML

```html
<img src="image.jpg" loading="lazy" alt="Frontend" />
```

---

### React

```jsx
const Home = lazy(() => import("./Home"));
```

---

## Benefits

- Faster Page Load.
- Better Performance.
- Better User Experience.
- Less Network Usage.

---

## 🧠 Interview Tip

Lazy Loading لا يستخدم مع الصور فقط.

يمكن استخدامه مع:

- Components
- Routes
- Videos
- Images

---

## ✅ Key Points

- Load only when needed.
- Faster initial loading.
- Less bandwidth.

---

# 3. What is Critical CSS?

## 🎯 Short Answer

Critical CSS is the minimum CSS required to render the visible part of the page immediately.

---

## 📖 Detailed Explanation

لما الصفحة تفتح.

المستخدم يرى الجزء الأول فقط.

يسمى

```
Above the Fold
```

إذن.

لماذا نحمل CSS الخاص بالفوتر؟

الأفضل:

- تحميل CSS الخاص بالجزء الظاهر أولًا.
- وتأجيل باقي CSS.

وده يجعل الصفحة تظهر أسرع.

---

## Visualization

```
Visible Area

↓

Critical CSS

--------------

Hidden Area

↓

Load Later
```

---

## Benefits

- Faster First Paint.
- Better Lighthouse Score.
- Better User Experience.

---

## 🧠 Interview Tip

Critical CSS لا يعني حذف CSS.

بل يعني:

تحميل المهم أولًا.

---

## ✅ Key Points

- Above the Fold.
- Faster Rendering.
- Better Performance.

---

# 4. How can you reduce CSS and JavaScript bundle size?

## 🎯 Short Answer

Reduce the amount of code shipped to the browser.

---

## 📖 Detailed Explanation

كلما زاد حجم الـ Bundle.

زاد وقت التحميل.

---

## أفضل الطرق

### Tree Shaking

إزالة الكود غير المستخدم.

---

### Code Splitting

تحميل الملفات عند الحاجة.

---

### Minification

حذف:

- Spaces
- Comments

---

### Compression

استخدم:

- Gzip
- Brotli

---

### Remove Unused Libraries

بدل تحميل مكتبة حجمها

```
300 KB
```

واستخدام Function واحدة.

اكتبها بنفسك.

---

### Dynamic Imports

```javascript
const Dashboard = lazy(() => import("./Dashboard"));
```

---

## 🧠 Interview Tip

React + Vite + Next.js

كلهم يعملوا:

Tree Shaking

بشكل تلقائي.

---

## ✅ Key Points

- Tree Shaking.
- Code Splitting.
- Compression.
- Minification.
- Remove Unused Code.

---

# 5. What is the difference between Debounce and Throttle?

## 🎯 Short Answer

- Debounce waits until the user stops triggering an event.
- Throttle limits how often an event can run.

---

## 📖 Detailed Explanation

### Debounce

كل مرة المستخدم يكتب.

الـ Timer يعيد نفسه.

لن يتم تنفيذ الـ Function.

إلا بعد أن يتوقف المستخدم.

---

### Example

```
Search Input
```

المستخدم كتب

```
M

Mo

Mos

Most

Mostafa
```

بدل إرسال

```
5 API Requests
```

يتم إرسال Request واحدة فقط.

---

### Throttle

يسمح بتنفيذ Function مرة كل فترة.

مثلاً.

مرة كل ثانية.

حتى لو المستخدم استمر في التحريك.

---

### Example

```
Scroll Event

Resize

Mouse Move
```

---

## 📊 Comparison

| Debounce   | Throttle       |
| ---------- | -------------- |
| Wait       | Limit          |
| Search     | Scroll         |
| Last Event | Every Interval |

---

## 🧠 Interview Tip

Search Box

↓

Debounce

Scroll

↓

Throttle

---

## ✅ Key Points

- Debounce → Wait.
- Throttle → Limit.
- Both improve Performance.

---

# 6. What is Caching? How does it improve performance?

## 🎯 Short Answer

Caching means storing data temporarily so it can be reused without downloading it again.

---

## 📖 Detailed Explanation

بدل تحميل:

```
logo.png
```

كل مرة.

المتصفح يحفظها.

وفي الزيارة التالية.

يعرضها مباشرة.

---

## أنواع الـ Caching

### Browser Cache

يحفظ:

- Images
- CSS
- JavaScript

---

### CDN Cache

يحفظ الملفات على Servers حول العالم.

---

### API Cache

يحفظ نتائج الـ API.

بدل إعادة إرسال نفس الطلب.

---

## Benefits

- Faster Loading.
- Less Network Requests.
- Better User Experience.
- Lower Server Load.

---

## 💻 Example

```
User Visit

↓

Download CSS

↓

Browser Cache

↓

Second Visit

↓

Load From Cache

✅ Faster
```

---

## 🧠 Interview Tip

لو سألك:

Why is the second visit faster?

الإجابة غالبًا:

```
Browser Cache
```

---

## ✅ Key Points

- Browser Cache.
- CDN Cache.
- API Cache.
- Faster Loading.
- Fewer Requests.

---

# 🎉 Performance Interview Summary

## أشهر الأسئلة

- Improve Website Performance.
- Lazy Loading.
- Critical CSS.
- Bundle Optimization.
- Debounce vs Throttle.
- Caching.

## 🚀 Performance Roadmap

إذا فهمت المواضيع دي، هتكون جاهز لمعظم أسئلة الـ Performance:

- Lazy Loading
- Code Splitting
- Tree Shaking
- Minification
- Compression
- Critical CSS
- Caching
- CDN
- Image Optimization
- Lighthouse
- Core Web Vitals

---

# React Interview Questions

> Front-End Interview Notes
>
> Level: Junior → Mid-Level

---

# 1. What is the difference between State and Props?

## 🎯 Short Answer

- **Props** are passed from a parent component to a child component.
- **State** is managed inside the component itself and can change over time.

---

## 📖 Detailed Explanation

### Props

Props اختصار لـ **Properties**.

هي البيانات اللي الأب (Parent) بيبعتها للابن (Child).

الـ Child يقدر يقرأها فقط، لكنه **لا يغيرها**.

> Props are **Read-Only**.

---

### State

الـ State هي البيانات الخاصة بالـ Component.

الـ Component نفسه هو اللي يقدر يغيرها باستخدام:

```jsx
setState();
```

أو

```jsx
setCount();
```

لو الـ State اتغيرت.

React يعمل:

```
Re-render
```

للكومبوننت.

---

## 💻 Example

### Parent

```jsx
function App() {
  return <User name="Mostafa" />;
}
```

---

### Child

```jsx
function User({ name }) {
  return <h1>{name}</h1>;
}
```

`name` هنا تعتبر **Prop**.

---

### State Example

```jsx
const [count, setCount] = useState(0);
```

```jsx
<button onClick={() => setCount(count + 1)}>{count}</button>
```

---

## 📊 Comparison

| Props                  | State                           |
| ---------------------- | ------------------------------- |
| Read Only              | Can Change                      |
| Passed From Parent     | Inside Component                |
| No Re-render by itself | Updating State causes Re-render |

---

## 🧠 Interview Tip

احفظ الجملة دي:

> Props are owned by the Parent.

> State is owned by the Component.

---

## ✅ Key Points

- Props → Parent → Child.
- State → Internal Data.
- State changes trigger Re-render.

---

# 2. When should you use `useEffect`?

## 🎯 Short Answer

`useEffect` is used to perform **Side Effects** after rendering.

---

## 📖 Detailed Explanation

أي حاجة مش مرتبطة مباشرة بالـ UI تعتبر Side Effect.

مثل:

- API Calls
- Timers
- Event Listeners
- Local Storage
- Updating Document Title

---

## Example

```jsx
useEffect(() => {
  console.log("Component Mounted");
}, []);
```

هيتنفذ مرة واحدة بعد أول Render.

---

### Fetch API

```jsx
useEffect(() => {
  fetchUsers();
}, []);
```

---

### Run on Dependency Change

```jsx
useEffect(() => {
  console.log(count);
}, [count]);
```

كلما تغير `count` سيتم تنفيذ الـ Effect.

---

### Cleanup Function

```jsx
useEffect(() => {
  window.addEventListener("resize", resize);

  return () => {
    window.removeEventListener("resize", resize);
  };
}, []);
```

---

## 🧠 Interview Tip

احفظ الحالات الثلاث:

```jsx
useEffect(fn);
```

➡️ Runs after every render.

---

```jsx
useEffect(fn, []);
```

➡️ Runs once.

---

```jsx
useEffect(fn, [count]);
```

➡️ Runs when `count` changes.

---

## ✅ Key Points

- API Calls.
- Timers.
- Event Listeners.
- Local Storage.
- Cleanup Function.

---

# 3. How can you prevent unnecessary Re-renders?

## 🎯 Short Answer

React re-renders when State or Props change.

يمكن تقليل الـ Re-renders باستخدام أدوات معينة.

---

## 📖 Detailed Explanation

كل Re-render غير ضروري بيأثر على الأداء.

React يوفر أدوات لتقليلها.

---

### React.memo()

يمنع إعادة رسم الـ Component إذا لم تتغير الـ Props.

```jsx
export default React.memo(Card);
```

---

### useMemo()

يحفظ نتيجة العمليات الثقيلة.

```jsx
const total = useMemo(() => {
  return calculateTotal(items);
}, [items]);
```

---

### useCallback()

يحفظ الـ Function نفسها.

```jsx
const handleClick = useCallback(() => {
  console.log("Hello");
}, []);
```

---

### Don't Update State Unnecessarily

لا تستدعي:

```jsx
setState();
```

إذا كانت القيمة لم تتغير.

---

## 🧠 Interview Tip

اسأل نفسك:

هل المشكلة في:

- Component؟
- Function؟
- Calculation؟

ثم اختر:

- React.memo
- useMemo
- useCallback

---

## ✅ Key Points

- React.memo
- useMemo
- useCallback
- Avoid unnecessary State updates.

---

# 4. What is the difference between Controlled and Uncontrolled Components?

## 🎯 Short Answer

- Controlled Components are controlled by React State.
- Uncontrolled Components are controlled by the DOM.

---

## 📖 Detailed Explanation

### Controlled Component

React هو المصدر الوحيد للحقيقة (Single Source of Truth).

```jsx
const [name, setName] = useState("");
```

```jsx
<input value={name} onChange={(e) => setName(e.target.value)} />
```

---

### Uncontrolled Component

القيمة موجودة داخل الـ DOM.

ويتم الوصول إليها باستخدام:

```jsx
useRef();
```

---

## Example

```jsx
const inputRef = useRef();
```

```jsx
<input ref={inputRef} />
```

```jsx
console.log(inputRef.current.value);
```

---

## 📊 Comparison

| Controlled        | Uncontrolled            |
| ----------------- | ----------------------- |
| React State       | DOM                     |
| Easier Validation | Less Code               |
| More Control      | Faster for simple forms |

---

## 🧠 Interview Tip

في أغلب المشاريع.

ستستخدم:

```
Controlled Components
```

لأنها أسهل في:

- Validation
- Forms
- Error Handling

---

## ✅ Key Points

- Controlled → State.
- Uncontrolled → Ref.
- Controlled is more common.

---

# 5. What is the difference between the Virtual DOM and the Real DOM?

## 🎯 Short Answer

- Real DOM is the actual DOM in the browser.
- Virtual DOM is a lightweight copy maintained by React.

---

## 📖 Detailed Explanation

### Real DOM

أي تغيير.

يجعل المتصفح يعيد:

- Layout
- Paint
- Render

وده مكلف.

---

### Virtual DOM

React ينشئ نسخة داخل الذاكرة.

عند تغيير الـ State.

React:

1. Creates a new Virtual DOM.
2. Compares it with the previous one (Diffing).
3. Updates only the changed parts.

وده يجعل React أسرع.

---

## Visualization

```
State Changed

↓

Virtual DOM

↓

Diffing

↓

Update Changed Nodes Only

↓

Real DOM
```

---

## 🧠 Interview Tip

React لا يعيد رسم الصفحة بالكامل.

بل يحدث العناصر التي تغيرت فقط.

---

## ✅ Key Points

- Virtual DOM is faster.
- React compares old vs new Virtual DOM.
- Only changed elements are updated.

---

# 6. What is the difference between `useState` and `useRef`?

## 🎯 Short Answer

- `useState` stores data and causes a Re-render.
- `useRef` stores data without causing a Re-render.

---

## 📖 Detailed Explanation

### useState

يستخدم لتخزين البيانات التي تؤثر على واجهة المستخدم.

```jsx
const [count, setCount] = useState(0);
```

كلما تغيرت القيمة.

React يعمل:

```
Re-render
```

---

### useRef

يحفظ قيمة بين الـ Renders.

لكن تغييرها لا يعيد رسم الـ Component.

---

## Example

```jsx
const inputRef = useRef();
```

```jsx
<input ref={inputRef} />
```

```jsx
inputRef.current.focus();
```

---

## Another Example

```jsx
const renderCount = useRef(0);

renderCount.current++;
```

يمكن استخدامها لمعرفة عدد مرات الـ Render بدون إعادة الرسم.

---

## 📊 Comparison

| useState         | useRef               |
| ---------------- | -------------------- |
| Causes Re-render | No Re-render         |
| UI Data          | DOM References       |
| State Management | Store Mutable Values |

---

## 🧠 Interview Tip

استخدم:

- `useState` عندما تريد تحديث الـ UI.
- `useRef` للوصول إلى عناصر الـ DOM أو تخزين قيمة لا تؤثر على الـ UI.

---

## ✅ Key Points

- useState → Re-render.
- useRef → No Re-render.
- useRef is commonly used with DOM elements.

---

# 🎉 React Interview Summary

## أشهر الأسئلة

- State vs Props
- useEffect
- React Re-render
- React.memo vs useMemo vs useCallback
- Controlled vs Uncontrolled Components
- Virtual DOM vs Real DOM
- useState vs useRef

## 🚀 React Interview Roadmap

إذا فهمت المواضيع دي كويس، هتكون جاهز لمعظم مقابلات React:

- JSX
- Components
- Props
- State
- Event Handling
- Conditional Rendering
- Lists & Keys
- Forms
- useState
- useEffect
- useRef
- useMemo
- useCallback
- React.memo
- Context API
- Custom Hooks
- Routing
- API Integration
- Performance Optimization

---

# Extra Front-End Interview Questions

> Front-End Interview Notes
>
> Most Frequently Asked Questions

---

# 1. What is REST API?

## 🎯 Short Answer

REST API is a way for the **Frontend** and **Backend** to communicate using HTTP requests.

---

## 📖 Detailed Explanation

لما المستخدم يعمل Login.

الـ Frontend لا يستطيع الوصول إلى قاعدة البيانات مباشرة.

بدلًا من ذلك.

يرسل Request إلى الـ Backend.

والـ Backend يعالج الطلب ويرجع Response.

```
Frontend

↓

HTTP Request

↓

Backend

↓

Database

↓

HTTP Response

↓

Frontend
```

---

## أشهر HTTP Methods

| Method | Purpose             |
| ------ | ------------------- |
| GET    | Read Data           |
| POST   | Create Data         |
| PUT    | Update All Data     |
| PATCH  | Update Part of Data |
| DELETE | Delete Data         |

---

## 💻 Example

```javascript
fetch("https://api.example.com/users");
```

---

## 🧠 Interview Tip

REST API تعتمد على

```
HTTP
```

وليس JavaScript.

---

## ✅ Key Points

- Frontend ↔ Backend
- JSON
- HTTP Methods

---

# 2. What is JSON?

## 🎯 Short Answer

JSON stands for **JavaScript Object Notation**.

It is the most common format for exchanging data between Frontend and Backend.

---

## 📖 Detailed Explanation

بدل إرسال البيانات بهذا الشكل

```
Name=Mostafa
Age=25
```

نرسلها كالتالي

```json
{
  "name": "Mostafa",
  "age": 25
}
```

---

## تحويل JSON

Object → JSON

```javascript
JSON.stringify(user);
```

---

JSON → Object

```javascript
JSON.parse(data);
```

---

## 🧠 Interview Tip

كل API تقريبًا ترجع

```
JSON
```

---

## ✅ Key Points

- Lightweight
- Easy to Read
- Easy to Parse

---

# 3. What is HTTP?

## 🎯 Short Answer

HTTP stands for **HyperText Transfer Protocol**.

It is the protocol used to transfer data between Client and Server.

---

## 📖 Detailed Explanation

كل مرة تفتح موقع.

المتصفح يرسل

```
HTTP Request
```

والسيرفر يرد

```
HTTP Response
```

---

## HTTP Request

```
GET /users
```

---

## HTTP Response

```json
[
  {
    "id": 1,
    "name": "Mostafa"
  }
]
```

---

## أشهر Status Codes

| Code | Meaning      |
| ---- | ------------ |
| 200  | Success      |
| 201  | Created      |
| 204  | No Content   |
| 400  | Bad Request  |
| 401  | Unauthorized |
| 403  | Forbidden    |
| 404  | Not Found    |
| 500  | Server Error |

---

## 🧠 Interview Tip

احفظ

```
200

201

401

403

404

500
```

لأنهم أشهر Status Codes.

---

## ✅ Key Points

- Request
- Response
- Status Codes

---

# 4. What is CORS?

## 🎯 Short Answer

CORS allows or blocks requests between different origins.

---

## 📖 Detailed Explanation

لو عندك

```
localhost:3000
```

والـ API موجودة على

```
localhost:5000
```

المتصفح هيمنع الـ Request.

إلا إذا الـ Backend سمح بذلك باستخدام CORS.

---

## لماذا؟

لحماية المستخدم.

ومنـع المواقع الخبيثة من قراءة البيانات.

---

## 🧠 Interview Tip

CORS ليس Error في React.

بل Security Feature في المتصفح.

---

## ✅ Key Points

- Different Origins
- Browser Security
- Backend Controls CORS

---

# 5. What is Authentication?

## 🎯 Short Answer

Authentication means verifying **who the user is**.

---

## 📖 Detailed Explanation

مثال

```
Email

Password
```

↓

Backend

↓

Valid؟

↓

JWT Token

↓

Frontend

---

بعد نجاح الـ Login.

يتم حفظ Token.

ثم يتم إرساله مع كل Request.

---

## 🧠 Interview Tip

Authentication

↓

Who are you?

Authorization

↓

What can you access?

---

## ✅ Key Points

- Login
- JWT
- Identity Verification

---

# 6. What is JWT?

## 🎯 Short Answer

JWT stands for **JSON Web Token**.

It is used to identify authenticated users.

---

## 📖 Detailed Explanation

بعد نجاح Login.

الـ Backend يرجع

```
JWT Token
```

مثل

```
eyJhbGciOi...
```

الـ Frontend يحفظه.

ثم يرسله مع كل Request.

```http
Authorization

Bearer Token
```

---

## 🧠 Interview Tip

JWT لا يحتوي Password.

بل يحتوي معلومات مشفرة.

---

## ✅ Key Points

- Authentication
- Bearer Token
- Authorization Header

---

# 7. What is the difference between Cookies and Local Storage?

## 🎯 Short Answer

Cookies are automatically sent with HTTP requests.

Local Storage is not.

---

## 📊 Comparison

| Cookies                   | Local Storage |
| ------------------------- | ------------- |
| Sent Automatically        | Manual        |
| Small Size                | Larger Size   |
| Can Expire                | Until Removed |
| More Secure with HttpOnly | Less Secure   |

---

## 🧠 Interview Tip

Authentication غالبًا يستخدم

```
HttpOnly Cookies
```

بدل Local Storage.

---

## ✅ Key Points

- Cookies → Server Communication
- Local Storage → Browser Storage

---

# 8. What is the difference between Authentication and Authorization?

## 🎯 Short Answer

Authentication = Who are you?

Authorization = What are you allowed to do?

---

## Example

Login

↓

Authentication

↓

Admin

↓

Authorization

↓

Access Dashboard

---

## 🧠 Interview Tip

احفظها كده

```
Authentication

↓

Identity

Authorization

↓

Permissions
```

---

## ✅ Key Points

- Authentication first.
- Authorization second.

---

# 9. What is CSR, SSR, SSG, and ISR?

## 🎯 Short Answer

These are different rendering strategies.

---

## CSR

Client Side Rendering

React renders everything in the browser.

---

## SSR

Server Side Rendering

HTML generated on every request.

---

## SSG

Static Site Generation

Generated once during Build Time.

---

## ISR

Incremental Static Regeneration

Static pages regenerated after deployment.

---

## 📊 Comparison

| Type | Generated     |
| ---- | ------------- |
| CSR  | Browser       |
| SSR  | Every Request |
| SSG  | Build Time    |
| ISR  | After Build   |

---

## 🧠 Interview Tip

Next.js يدعم الأربع طرق.

---

## ✅ Key Points

- CSR
- SSR
- SSG
- ISR

---

# 10. What is the difference between Access Token and Refresh Token?

## 🎯 Short Answer

Access Token is used to access protected resources.

Refresh Token is used to generate a new Access Token.

---

## 📖 Detailed Explanation

```
Login

↓

Access Token

(15 min)

↓

Expired

↓

Refresh Token

↓

New Access Token
```

---

## لماذا؟

حتى لا يضطر المستخدم لتسجيل الدخول كل فترة.

---

## 🧠 Interview Tip

Access Token

↓

Short Lifetime

Refresh Token

↓

Long Lifetime

---

## ✅ Key Points

- Access Token → API Requests
- Refresh Token → Renew Access Token
- Better Security

---

# JavaScript Interview Questions

> Topic: Promises & Async/Await

---

# 1. What is a Promise?

## 🎯 Short Answer

A **Promise** is an object that represents the **future result** of an asynchronous operation.

It can be in one of three states:

- Pending
- Fulfilled
- Rejected

---

## 📖 Detailed Explanation

لما تعمل API Request.

النتيجة مش بترجع فورًا.

JavaScript بترجع Promise.

بعدها الـ Promise إما:

- تنجح (Resolve)
- تفشل (Reject)

---

## Promise States

```
Pending

↓

Fulfilled (Resolved)

OR

Rejected
```

---

## 💻 Example

```javascript
const promise = new Promise((resolve, reject) => {
  const success = true;

  if (success) {
    resolve("Login Success");
  } else {
    reject("Login Failed");
  }
});
```

---

## Handling Promise

```javascript
promise
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.log(error);
  });
```

Output

```
Login Success
```

---

## Real Example

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.log(error));
```

---

## 🧠 Interview Tip

Promise تساعد في تجنب مشكلة:

```
Callback Hell
```

---

## ✅ Key Points

- Handles asynchronous operations.
- Has 3 states.
- Uses `.then()` and `.catch()`.

---

# 2. What is Async/Await?

## 🎯 Short Answer

`async/await` is a cleaner way to work with Promises, making asynchronous code look like synchronous code.

---

## 📖 Detailed Explanation

بدل كتابة:

```javascript
fetch(...)
.then(...)
.then(...)
.catch(...)
```

يمكنك كتابة:

```javascript
async

await
```

فيصبح الكود أسهل للقراءة.

---

## Example

```javascript
async function getUsers() {
  const response = await fetch("https://jsonplaceholder.typicode.com/users");

  const data = await response.json();

  console.log(data);
}
```

---

## Using try...catch

```javascript
async function getUsers() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/users");

    const data = await response.json();

    console.log(data);
  } catch (error) {
    console.log(error);
  }
}
```

---

## Important Notes

### async

أي Function تبدأ بـ

```javascript
async;
```

ترجع Promise تلقائيًا.

```javascript
async function hello() {
  return "Hello";
}
```

تعادل:

```javascript
Promise.resolve("Hello");
```

---

### await

يمكن استخدامها فقط داخل:

```javascript
async function
```

---

## 🧠 Interview Tip

إذا استخدمت `await` خارج `async`.

ستحصل على:

```
SyntaxError
```

---

## ✅ Key Points

- Cleaner than `.then()`.
- Easier to read.
- Works only inside `async`.

---

# 3. Promise vs Async/Await

## 📊 Comparison

| Promise (.then)                 | Async/Await                  |
| ------------------------------- | ---------------------------- |
| Chain of `.then()`              | Looks like synchronous code  |
| Harder to read in complex cases | Easier to read               |
| Uses `.catch()`                 | Uses `try...catch`           |
| Good for simple chains          | Best for complex async logic |

---

## Example using Promise

```javascript
fetch(url)
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.log(error));
```

---

## Example using Async/Await

```javascript
try {
  const response = await fetch(url);

  const data = await response.json();

  console.log(data);
} catch (error) {
  console.log(error);
}
```

---

## 🧠 Interview Tip

الاتنين بيعتمدوا على نفس الفكرة.

`async/await` مجرد Syntax أسهل للتعامل مع الـ Promises.

---

# 4. Execution Flow Example

## Example

```javascript
console.log("Start");

async function getData() {
  const response = await fetch(url);

  console.log("Data Loaded");
}

getData();

console.log("End");
```

### Output

```
Start

End

Data Loaded
```

---

## لماذا؟

لأن `fetch()` عملية Asynchronous.

JavaScript لا تنتظر انتهاء الـ Request.

وتكمل تنفيذ باقي الكود.

---

# 5. Promise Methods

## Promise.all()

ينتظر نجاح جميع الـ Promises.

```javascript
Promise.all([promise1, promise2]).then((results) => console.log(results));
```

إذا فشل واحد فقط.

كل العملية تفشل.

---

## Promise.allSettled()

ينتظر انتهاء جميع الـ Promises.

سواء نجحت أو فشلت.

```javascript
Promise.allSettled([promise1, promise2]);
```

---

## Promise.race()

يرجع أول Promise تنتهي.

سواء نجاح أو فشل.

```javascript
Promise.race([promise1, promise2]);
```

---

## Promise.any()

يرجع أول Promise ناجحة.

ويتجاهل الفاشلة.

```javascript
Promise.any([promise1, promise2]);
```

---

## 📊 Comparison

| Method             | Behavior         |
| ------------------ | ---------------- |
| Promise.all        | All must succeed |
| Promise.allSettled | Waits for all    |
| Promise.race       | First finished   |
| Promise.any        | First successful |

---

# 6. Common Interview Questions

## Q: Does `await` block JavaScript?

**Answer:**

لا.

هو يوقف تنفيذ الـ **async function فقط**.

لكن JavaScript تكمل تنفيذ باقي الكود خارجها.

---

## Q: Can we use `await` without `async`?

**Answer:**

❌ No.

إلا في بعض البيئات التي تدعم **Top-Level Await** (مثل ES Modules).

---

## Q: Is Async/Await faster than Promise?

**Answer:**

❌ No.

الاتنين نفس الأداء تقريبًا.

الفرق فقط في **Syntax** وسهولة القراءة.

---

## Q: Which one should I use?

**Answer:**

في أغلب المشاريع الحديثة (React / Next.js):

✅ استخدم `async/await`.

---

# 🎯 Interview Summary

## Promise

- Represents future value.
- Pending → Fulfilled → Rejected.
- Uses `.then()` and `.catch()`.

---

## Async/Await

- Cleaner syntax.
- Built on top of Promises.
- Uses `try...catch`.
- Easier to read and maintain.

---

# 🚀 Real React Example

```javascript
useEffect(() => {
  const getUsers = async () => {
    try {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      );

      const data = await response.json();

      setUsers(data);
    } catch (error) {
      console.log(error);
    }
  };

  getUsers();
}, []);
```

> 💡 **Interview Tip:** في معظم مشاريع React وNext.js الحديثة، ستجد `async/await` مع `try...catch` هو الأسلوب الأكثر استخدامًا لأنه يجعل الكود أوضح وأسهل في الصيانة.

---

# Bonus Front-End Interview Questions

> Most Asked Questions in Real Interviews

---

# 1. What is the Virtual DOM Diffing Algorithm?

## 🎯 Short Answer

React compares the old Virtual DOM with the new Virtual DOM, then updates only the changed elements in the Real DOM.

### ✅ Key Points

- Faster rendering.
- Updates only changed nodes.
- Improves performance.

---

# 2. What are Keys in React?

## 🎯 Short Answer

Keys are unique identifiers used by React to track list items efficiently.

### Example

```jsx
users.map((user) => <User key={user.id} />);
```

### ❌ Don't Use

```jsx
key = { index };
```

إلا لو القائمة ثابتة ولا تتغير.

### ✅ Key Points

- Must be unique.
- Helps React identify changed items.
- Improves rendering performance.

---

# 3. Why shouldn't you use Array Index as a Key?

## Answer

لأن لو حصل:

- Delete
- Insert
- Reorder

React ممكن يحدث العنصر الغلط.

الأفضل دائمًا استخدام:

```jsx
key={item.id}
```

---

# 4. What is Lifting State Up?

## Answer

لما أكثر من Component يحتاجوا نفس البيانات.

ننقل الـ State إلى أقرب Parent.

```
Parent

↓

Child A

↓

Child B
```

بدل ما كل Child يكون عنده State منفصلة.

---

# 5. What is Prop Drilling?

## Answer

تمرير الـ Props عبر عدة Components فقط للوصول إلى Component بعيد.

```
App

↓

Layout

↓

Dashboard

↓

Sidebar

↓

Profile
```

الحل غالبًا يكون:

- Context API
- Redux
- Zustand

---

# 6. What is Context API?

## Answer

طريقة لمشاركة البيانات بين Components بدون الحاجة لتمرير Props في كل مستوى.

مناسب لـ:

- Theme
- Language
- Logged-in User

---

# 7. When should you use Redux?

## Answer

استخدم Redux عندما يكون عندك Global State كبيرة ومعقدة.

مثل:

- Shopping Cart
- Authentication
- Dashboard
- Notifications

---

# 8. What is React Fragment?

## Answer

يسمح بإرجاع أكثر من Element بدون إضافة عنصر جديد للـ DOM.

```jsx
<>
  <Header />
  <Main />
</>
```

---

# 9. What is Hydration in Next.js?

## Answer

الـ Server يرسل HTML جاهز.

ثم React يضيف له JavaScript حتى يصبح تفاعليًا.

```
Server HTML

↓

Browser

↓

Hydration

↓

Interactive Page
```

---

# 10. What is Code Splitting?

## Answer

تحميل أجزاء التطبيق عند الحاجة فقط.

بدل تحميل التطبيق كله مرة واحدة.

---

# 11. What is Tree Shaking?

## Answer

إزالة الكود غير المستخدم أثناء عملية الـ Build.

---

# 12. What is Memoization?

## Answer

حفظ نتيجة العمليات المكلفة لإعادة استخدامها بدل حسابها مرة أخرى.

في React يتم ذلك باستخدام:

```jsx
useMemo();
```

---

# 13. What is the Difference between npm and npx?

## npm

لتثبيت Packages.

```bash
npm install axios
```

---

## npx

لتشغيل Package مباشرة بدون تثبيتها عالميًا.

```bash
npx create-next-app
```

---

# 14. What is Package.json?

## Answer

هو ملف يحتوي على:

- Project Name
- Version
- Scripts
- Dependencies
- DevDependencies

---

# 15. What is the Difference between Dependencies and DevDependencies?

## dependencies

تُستخدم أثناء تشغيل التطبيق.

مثل:

- React
- Axios

---

## devDependencies

تستخدم أثناء التطوير فقط.

مثل:

- ESLint
- Prettier
- TypeScript

---

# 16. What is Environment Variables?

## Answer

متغيرات لتخزين بيانات حساسة مثل:

- API URL
- Secret Keys
- Tokens

في React:

```env
VITE_API_URL=
```

في Next.js:

```env
NEXT_PUBLIC_API_URL=
```

---

# 17. What is SEO?

## Answer

SEO = Search Engine Optimization.

تحسين ظهور الموقع في نتائج محركات البحث.

من أهم العوامل:

- Semantic HTML
- Meta Tags
- Title
- Description
- Performance
- SSR / SSG

---

# 18. What is Lighthouse?

## Answer

أداة من Google لقياس جودة الموقع.

تقيس:

- Performance
- Accessibility
- SEO
- Best Practices

---

# 19. What is Accessibility (a11y)?

## Answer

جعل الموقع قابلًا للاستخدام لجميع المستخدمين، بما فيهم ذوو الاحتياجات الخاصة.

أمثلة:

- alt للصور
- Labels للـ Forms
- Keyboard Navigation
- Semantic HTML

---

# 20. Tell me about yourself (Front-End)

## نموذج مختصر

> Hi, I'm Mostafa. I'm a Front-End Developer specializing in React, Next.js, TypeScript, and Tailwind CSS. I enjoy building responsive and user-friendly web applications, integrating REST APIs, and writing clean, maintainable code. Recently, I've worked on projects like Hotel Booking System and Quiz App, where I focused on authentication, state management, and performance optimization. I'm always learning new technologies and improving my problem-solving skills.

---

# 🎯 Final Interview Tips

- Understand, don't memorize.
- Explain every answer with a simple example.
- Think aloud during coding questions.
- Be honest if you don't know something.
- Focus on clean code and problem solving.

---

# TypeScript Interview Questions

> Front-End Interview Notes
>
> Level: Junior → Mid-Level

---

# 1. What is the difference between `type` and `interface`?

## 🎯 Short Answer

- `interface` is mainly used to define the shape of **objects** and supports **declaration merging**.
- `type` is more flexible and can represent **objects, primitives, unions, tuples, intersections, and functions**.

---

## 📖 Detailed Explanation

الاتنين بيستخدموا لتعريف أنواع البيانات (Types)، لكن في فرق بينهم.

### Interface

مناسب لتعريف شكل الـ Object.

```typescript
interface User {
  name: string;
  age: number;
}
```

---

### Type

يقدر يعمل كل اللي Interface بتعمله، بالإضافة إلى:

- Union Types
- Intersection Types
- Tuples
- Primitive Types

```typescript
type User = {
  name: string;
  age: number;
};
```

---

### Union Example

```typescript
type Status = "success" | "error" | "loading";
```

Interface لا يمكنها عمل ذلك مباشرة.

---

### Declaration Merging

ميزة موجودة في Interface فقط.

```typescript
interface User {
  name: string;
}

interface User {
  age: number;
}
```

تصبح:

```typescript
interface User {
  name: string;
  age: number;
}
```

---

## 📊 Comparison

| Interface        | Type     |
| ---------------- | -------- |
| Objects          | Any Type |
| Supports Merging | ❌       |
| Can Extend       | ✅       |
| Union Types      | ❌       |
| Primitive Types  | ❌       |

---

## 🧠 Interview Tip

- استخدم **interface** مع Objects و API Models.
- استخدم **type** مع Union و Intersection والأنواع المعقدة.

---

## ✅ Key Points

- Interface → Objects.
- Type → More Flexible.
- Interface supports Declaration Merging.

---

# 2. What is the difference between `unknown` and `any`?

## 🎯 Short Answer

- `any` disables TypeScript checking.
- `unknown` keeps TypeScript safe by forcing you to check the type before using it.

---

## 📖 Detailed Explanation

### any

يسمح لك بعمل أي شيء.

```typescript
let value: any = 10;

value.toUpperCase();
```

لن يظهر Error أثناء الـ Compile.

لكن قد يحدث Runtime Error.

---

### unknown

أكثر أمانًا.

```typescript
let value: unknown = "Mostafa";

console.log(value.length);
```

❌ Error

يجب التأكد من النوع أولًا.

```typescript
if (typeof value === "string") {
  console.log(value.length);
}
```

---

## 📊 Comparison

| any                 | unknown                |
| ------------------- | ---------------------- |
| Unsafe              | Safe                   |
| No Type Checking    | Type Checking Required |
| Can access anything | Must Narrow First      |

---

## 🧠 Interview Tip

يفضل دائمًا استخدام `unknown` بدل `any` إذا كنت لا تعرف نوع البيانات.

---

## ✅ Key Points

- any → Turns off TypeScript.
- unknown → Safe.
- Prefer unknown.

---

# 3. What is Type Inference?

## 🎯 Short Answer

Type Inference means TypeScript automatically detects the variable type without explicitly writing it.

---

## 📖 Detailed Explanation

بدل ما تكتب:

```typescript
let age: number = 25;
```

يمكنك كتابة:

```typescript
let age = 25;
```

TypeScript يعرف أن `age` من النوع `number`.

---

## Example

```typescript
let name = "Mostafa";
```

TypeScript يفهم أن النوع هو:

```typescript
string;
```

---

## Benefits

- Less Code.
- Better Readability.
- Strong Type Safety.

---

## 🧠 Interview Tip

كلما استطعت، دع TypeScript يستنتج النوع تلقائيًا.

---

## ✅ Key Points

- Automatic Type Detection.
- Cleaner Code.
- Better Developer Experience.

---

# 4. How do you use Generics?

## 🎯 Short Answer

Generics allow you to write reusable code that works with different data types while maintaining type safety.

---

## 📖 Detailed Explanation

بدل كتابة Function لكل نوع.

```typescript
function getString(value: string) {
  return value;
}
```

ثم

```typescript
function getNumber(value: number) {
  return value;
}
```

استخدم Generic.

---

## Example

```typescript
function identity<T>(value: T): T {
  return value;
}
```

---

Usage

```typescript
identity<string>("Mostafa");

identity<number>(100);

identity<boolean>(true);
```

---

## Generic Interface

```typescript
interface ApiResponse<T> {
  data: T;
  success: boolean;
}
```

---

## Example

```typescript
const user: ApiResponse<string> = {
  data: "Mostafa",
  success: true,
};
```

---

## 🧠 Interview Tip

Generics تستخدم كثيرًا في:

- React Hooks
- Axios
- API Responses
- Utility Functions

---

## ✅ Key Points

- Reusable Code.
- Type Safe.
- Flexible.

---

# 5. What is the difference between Optional and Readonly properties?

## 🎯 Short Answer

- Optional (`?`) means the property may or may not exist.
- Readonly means the property cannot be changed after initialization.

---

## 📖 Detailed Explanation

### Optional Property

```typescript
interface User {
  name: string;

  age?: number;
}
```

يمكن إنشاء Object بدون `age`.

---

### Readonly Property

```typescript
interface User {
  readonly id: number;

  name: string;
}
```

بعد إنشاء الـ Object.

لا يمكن تغيير `id`.

---

## Example

```typescript
const user = {
  id: 1,

  name: "Mostafa",
};

user.id = 2;
```

❌ Error

---

## 📊 Comparison

| Optional      | Readonly      |
| ------------- | ------------- |
| May Not Exist | Cannot Change |
| `?`           | `readonly`    |

---

## 🧠 Interview Tip

يمكن استخدامهما معًا.

```typescript
readonly age?: number;
```

---

## ✅ Key Points

- Optional → Optional Field.
- Readonly → Immutable Field.

---
