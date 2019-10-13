# JavaScript za rad s React-om <!-- omit in toc -->

- [Template literals/strings](#template-literalsstrings)
  - [Tagged templates](#tagged-templates)
  - [Examples in Gatsby and React](#examples-in-gatsby-and-react)
- [Variable declaration (`var`, `let` and `const`)](#variable-declaration-var-let-and-const)
- [Inicijalizacija objekta](#inicijalizacija-objekta)
- [Destructuring objects](#destructuring-objects)

Za efektivno korištenje React.js biblioteke dobro je poznavati moderne funkcionalnosti JavaScript jezika (ES6+). U nastavku ćemo pokazati dio modernih aspekata i funkcionalnosti JavaScript za efektan rad s Reactom.

## Template literals/strings

[MDN: Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

```javascript
console.log('Hello' + ' ' + 'world' + '!') // Hello world!

const greeting = 'Hello';
const subject = 'world';

// mind the back-ticks (` `)
console.log(`${greeting} ${subject}!`) // Hello world!

// multiline strings
console.log(`Hello
world!`)
// Hello
// world!
```

### Tagged templates

```javascript
// here we define a tag called "fesb"
function fesb(strings, who, what) {
  const Who = who.charAt(0).toUpperCase() + who.slice(1);
  const What = what.charAt(0).toUpperCase() + what.slice(1);

  return `${Who}${strings[1]}"${What}" at FESB.`;
}

const who = "ivana";
const what = "computer science";

// tagged template literal
const output = fesb`${who} studies ${what}`;
console.log(output); // Ivana studies "Computer science" at FESB.
```

### Examples in Gatsby and React

```javascript
import { graphql } from "gatsby"

export const query = graphql`
  query {
    site {
      siteMetadata {
        title
        author
        date
      }
    }
  }
`
```

```javascript
import styled from "styled-components"

const Container = styled.div`
  margin: 3rem auto;
  max-width: 600px;
`
const Avatar = styled.img`
  flex: 0 0 96px;
  width: 96px;
  height: 96px;
`
const Username = styled.h2`
  margin: 0 0 12px 0;
  padding: 0;
`

// let's use new components
<Container>
    <Avatar img="photo.png"/>
    <Username>John Doe</Username>
</Container>
```

```javascript
const Button = styled.button`
  background: ${props => props.primary ? "black" : "white"};
  color: ${props => props.primary ? "white" : "black"};

  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid black;
`;

// now render button variations
<Button>Default</Button>
<Button primary>Default</Button>
```

## Variable declaration (`var`, `let` and `const`)

```javascript
var name = 'Ivan';
let surname = 'Ivanic';
const gender = 'male';
```

Tri jednostavna pravila pri deklaraciji varijabli:
  
  1. Ne koristite `var`.
  2. Kad god je to moguće koristite `const`.
  3. Koristite `let` kad varijablu želite mijenjati.

## Inicijalizacija objekta

[MDN: Object initializer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#New_notations_in_ECMAScript_2015)

```javascript
// old way
let o = {a: 'foo', b: 42, c: {}};
console.log(o); // { a: 'foo', b: 42, c: {} }

const a = 'foo', b = 42, c = {};
o = {a: a, b: b, c: c};
console.log(o); // { a: 'foo', b: 42, c: {} }

// modern way (EC6+)
o = {a, b, c};
console.log(o); // { a: 'foo', b: 42, c: {} }
```

Objekti mogu sadržavati i funkcije kao _property_-je:

```javascript
// old way
const securityService = {
    isAuthenticated: function(user) {
        return false;
    }
}
console.log(securityService) // { isAuthenticated: [Function: isAuthenticated] }

// modern JavaScript (EC6+)
const securityService = {
    isAuthenticated(user) {
        return false;
    }
}
console.log(securityService) // { isAuthenticated: [Function: isAuthenticated] }
```

## Destructuring objects

TBA