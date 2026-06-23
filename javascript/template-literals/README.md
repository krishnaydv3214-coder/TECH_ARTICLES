<a id="top">
# Template Literals in JavaScript: Why They Were Introduced and How They Changed String Handling
</a>
Before **ES6** introduced Template Literals, JavaScript developers used the + operator whenever they wanted to combine strings and variables.

Let’s see a simple example:

```javascript
const name = "John";

const message = "Hello " + name + ", welcome back!";

console.log(message);
```

Output:

```text
Hello JOHN, welcome back!
```

For small strings like this, everything looks fine.  
But as code became larger, developers started facing a few annoying problems.

### Problem 1: Too Many + Signs

Imagine we want to create a longer sentence:

```javascript
const name = "John";

const age = 20;

const city = "Delhi";

const message =

  "My name is " + name +

  ". I am " + age +

  " years old and I live in " + city + ".";

console.log(message);
```

The final output is simple:

```text
Hello JOHN, welcome back!
```

But look at the code. There are quotation marks everywhere and several + operators. As the string gets longer, the code starts looking messy.

### Problem 2:Writing Multiple Lines Was Awkward

Suppose we want a string that spans multiple lines.

Before Template Literals, developers often wrote something like this:

```javascript
const text =
  "JavaScript is fun.\n" +
  "It is easy to learn.\n" +
  "Practice is important.";

//Or when creating html 
const html =
  "<div>" +
  "<h1>Welcome</h1>" +
  "<p>Hello World</p>" +
  "</div>";

//The HTML itself is simple, but all those quotes and + signs make it harder to read.
```

### Problem 3:Easy to Make Small Mistakes

When writing long strings, forgetting a single + could break the code.

For example:

```javascript
const name = "John";

const message = "Hello " name;
```

This causes an error because the + operator is missing.

Small mistakes like this were common when working with large strings.

### Problem 4: The Code Doesn’t Look Like the Final Output

Consider this example:

```javascript
const product = "Laptop";
const price = 50000;

const text =
  "The price of " + product +
  " is ₹" + price + ".";
```

The actual sentence is:

```text
The price of Laptop is ₹50000.
```

But when reading the code, you have to mentally join all the pieces together to understand what the final string will look like.

### Problem 5: Building Large Templates Was Painful

Modern web applications often generate:

*   HTML
    
*   Email templates
    
*   Reports
    
*   Notifications
    
*   SQL queries
    

Using traditional concatenation, even a small HTML template could become difficult to manage:

```javascript
const user = "Krishna";

const html =
  "<div class='card'>" +
  "<h2>" + user + "</h2>" +
  "<p>Welcome to our website</p>" +
  "</div>";
```

The more dynamic content we wanted, the more unreadable the code became. We wanted a cleaner way to write strings—something that looked closer to the final output.

This need eventually led to the introduction of Template Literals in ES6.

## 2\. Template Literal Syntax

A Template Literal is a special way of creating strings using backticks ( ) instead of single quotes (') or double quotes (").

#### Traditional String Concatenation

```javascript
const name = "JOHN";

const message = "Hello " + name + ", welcome back!";

console.log(message);
```

Output:

```text
Hello JOHN, welcome back!
```

#### Using a Template Literal

```javascript
const name = "JOHN";

const message = `Hello JOHN, welcome back!`;

console.log(message);
```

Output:

```text
Hello JOHN, welcome back!
```

###### The biggest visual difference is the use of backticks instead double quotation mark.

## 3\. Embedding Variables in Strings

One of the most useful features of Template Literals is the ability to place variables directly inside a string.

This feature is technically called **String Interpolation**.

The syntax is:

```javascript
${expression}
```

JavaScript evaluates whatever is inside ${} and inserts the result into the final string.

```javascript
const name = "JOHN";

console.log(`Hello ${name}`);
```

Output:

```text
Hello JOHN
```

Without Template Literals:

```javascript
const name = "JOHN";

console.log("Hello " + name);
```

With Template Literals:

```javascript
const name = "JOHN";

console.log(`Hello ${name}`);
```

The second version is easier to read because the variable appears exactly where it should appear in the final output.

#### Embedding Multiple Variables

```javascript
const name = "JOHN";
const age = 20;

console.log(`My name is ${name} and I am ${age} years old.`);
```

```text
My name is JOHN and I am 20 years old.
```

#### Embedding Expressions

Anything that produces a value can be placed inside ${}.

```javascript
const a = 5;
const b = 10;

console.log(`The sum is ${a + b}`);
```

```text
The sum is 15
```

JavaScript first evaluates:

```text
a + b
```

and then inserts the result into the string.

#### Calling Functions

```javascript
function greet() {
    return "Welcome";
}

console.log(`${greet()} back!`);
```

Output:

```text
Welcome back!
```

**How it works?** This works because JavaScript evaluates the function call before inserting the result into the string.

## 4\. Multi-line Strings

Before Template Literals, creating strings that spanned multiple lines was inconvenient.

Developers often had to use newline characters (\\n) or multiple concatenations.

```javascript
const text = "JavaScript is fun.\n" +
             "It is easy to learn.\n" +
             "Practice is important.";

console.log(text);
```

Output:

```text
JavaScript is fun.
It is easy to learn.
Practice is important.
```

#### With Template Literals, multi-line strings become much simpler:

```javascript
const text = `JavaScript is fun.
It is easy to learn.
Practice is important.`;

console.log(text);
```

Output:

```text
JavaScript is fun.
It is easy to learn.
Practice is important.
```

###### The line breaks are preserved exactly as they are written, making the code cleaner and easier to read.  

## 5\. Tagged Template Literals  

JavaScript provides an advanced feature called Tagged Template Literals, where a function gets control over the Template Literal before the final string is created.

Instead of JavaScript automatically producing the string, a custom function can inspect, modify, or completely change the result.

Basic Syntax

```javascript
tagFunction`some text ${value}`;
```

Notice something unusual:

There are no parentheses after the function name.

Instead, the function name is written directly before the Template Literal.

Simple Example

```javascript
function myTag(strings, value) {
    console.log(strings);
    console.log(value);
}

const name = "JOHN";

myTag`Hello ${name}`;
```

Output:

```text
["Hello ", ""]
JOHN
```

At first glance, this looks strange.

Let’s understand what JavaScript is doing.

#### What JavaScript Passes to the Function

For:

```javascript
myTag`Hello ${name}`;
```

JavaScript splits the Template Literal into two parts:

1.  Static Text
    

```javascript
["Hello ", ""]
```

Everything outside ${} becomes an array of strings.

2.  Dynamic Values
    

```javascript
name
```

which becomes:

```javascript
JOHN
```

So JavaScript secretly converts:

```javascript
myTag`Hello ${name}`;
```

into something similar to:

```javascript
myTag(
    ["Hello ", ""],
    "JOHN"
);
```

#### Returning a Custom String

The tag function can return anything.

```javascript
function myTag(strings, value) {
    return strings[0] + value.toUpperCase();
}

const name = "john";

console.log(myTag`Hello ${name}`);
```

Output:

```text
Hello JOHN
```

Notice that we modified the value before creating the final string.

#### Multiple Expressions

```javascript
function myTag(strings, ...values) {
    console.log(strings);
    console.log(values);
}

const name = "JOHN";
const age = 20;

myTag`My name is ${name} and I am ${age}`;
```

Output:

```text
["My name is ", " and I am ", ""]
["JOHN", 20]
```

JavaScript places:

*   Static text in the first array
    
*   Dynamic values in the second array
    

## 6\. Use Cases in Modern JavaScript

At this point, we might be wondering:

“Template Literals are nice, but where are they actually used in real-world applications?”

**ANSWER**: Modern JavaScript applications frequently use Template Literals to create dynamic content, generate HTML, build URLs, construct SQL queries, and power libraries through Tagged Template Literals.

#### 1\. Dynamic Messages

One of the most common uses is generating user-facing messages.

```javascript
const username = "John";
const unreadMessages = 5;

const message =
    `Hello ${username}, you have ${unreadMessages} unread messages.`;

console.log(message);
```

Output:

```text
Hello John, you have 5 unread messages.
```

#### 2\. Dynamic URLs

Template Literals make building URLs easier.

```javascript
const userId = 101;

const url =
    `https://api.example.com/users/${userId}`;

console.log(url);
```

Output:

```text
https://api.example.com/users/101
```

This pattern is very common when working with APIs.

#### 3\. Generating HTML

Before frameworks like React became popular, developers often generated HTML dynamically.

```javascript
const username = "John";

const html = `
<div class="card">
    <h2>${username}</h2>
</div>
`;

console.log(html);
```

Output:

```text
<div class="card">
    <h2>John</h2>
</div>
```

Notice how the HTML structure remains readable because the formatting is preserved.

#### 4\. Building Email Templates

```javascript
const customer = "John";
const orderId = 1024;

const email = `
Hello ${customer},

Your order #${orderId} has been shipped.

Thank you for shopping with us.
`;

console.log(email);
```

This is much easier to maintain than concatenating multiple strings.

#### 5.Creating SQL Queries

```javascript
const userId = 10;

const query =
    `SELECT * FROM users WHERE id = ${userId}`;

console.log(query);
```

Output:

```text
SELECT * FROM users WHERE id = 10
```

#### 6.Tagged Template Literal Use Cases

This allows developers to inspect and modify values before creating the final result.

###### Escaping Unsafe HTML

Imagine a user enters:

```javascript
const userInput =
    "<script>alert('Hacked')</script>";
```

Without protection:

```javascript
const html =
    `<h1>${userInput}</h1>`;
```

This could inject unwanted HTML.

A tagged template can sanitize the value first.

```javascript
safeHTML`<h1>${userInput}</h1>`;
```

The safeHTML function can escape dangerous characters before generating the final string.

This is a common security use case.

###### Some other use cases of **Tagged Template Literal**

*   **GraphQL Queries**(Many GraphQL libraries use tagged templates.)
    
*   **CSS-in-JS Libraries**(One of the most famous uses of Tagged Template Literals is the library styled-components.)
    

## Template Literals vs Traditional String Concatenation and String Interpolation Visualizations

![](https://cdn.hashnode.com/uploads/covers/699b471cf5291f20937649a4/273f44c4-9710-40be-a355-2dd29c2cc3c1.png align="center")

## Conclusion

When I first learned about **Template Literals**, they looked like nothing more than strings written with backticks instead of quotation marks. It didn’t seem like a feature that would make much difference.

But after understanding the problems developers faced before **ES6**, it becomes clear why Template Literals were introduced. Writing long strings with **multiple + operators** was messy, **multi-line text** was awkward to manage, and the code often looked very different from the final output.

**Template Literals** solved these problems by making strings easier to read and write. Features like **string interpolation** allow variables and expressions to be placed directly inside a string, while **multi-line strings** remove the need for extra characters and concatenations. For more advanced use cases, **Tagged Template Literals** even give developers control over how strings are processed.

Today, **Template Literals** are a standard part of modern JavaScript. Whether you’re building **dynamic messages, generating HTML, creating API URLs, or working with libraries** that use **tagged templates**, you’ll encounter them regularly.

In the end, **Template Literals** are a great example of how a small change in syntax can make everyday coding much cleaner, more readable, and easier to maintain.


---

[⬆ Back to Top](#top)
