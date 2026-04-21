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

###  Ternary Operator `? :`

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

###  Short Circuiting

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
