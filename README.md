# Esy-State
Make your DOM react to changes.

No heavy frameworks, no aditional dependencies, no building, no transpilation.


## 👋 Getting Started

```shell
$ npm i esy-state
// Or import it via CDN
```

```html
<h1 #hello-world></h1>
<script type="module">
  import { state } from 'esy-state';
  state["hello-world"] = 'Hello World!';
</script>
```

## 🧩 Features

### Simple data binding
```html
<h1 #hello-world></h1>
<script type="module">
  import { state } from 'esy-state';
  state["hello-world"] = 'Hello World!';
</script>
```

### TODO: Data binding with "Mustache" syntax
```html
<h1 #world>Hello {{world]]!</h1>
<script type="module">
  import { state } from 'esy-state';
  state["world"] = 'World';
</script>
```

### Data binding (arbitrary HTML)

⚠️ Dynamically rendering arbitrary HTML on your website can be very dangerous because it can easily lead to XSS vulnerabilities. Only use this method on trusted content and never on user-provided content.

```html
<div +hello-world></div>
<script type="module">
  import { state } from 'esy-state';
  state["hello-world"] = '<h1>Hello World!</h1>';
</script>
```

### TODO: Attribu†e binding
```html
<h1 #foo></h1>
<input type="text" :value="foo" @change="onInputChange" id="input">
<script type="module">
  import { state, mutations } from 'esy-state';
  state["foo"] = 'bar!';
  mutations.onInputChange = () => {
    const name = document.getElementById("input").value;
    state["foo"] = bar;
    console.log(state);
  };
</script>
```

### TODO: Conditional rendering
```html
<div ?foo>I'm visible!<div>
<div ?!foo>I'm not visible</div>
<script type="module">
  import { state } from 'esy-state';
  state["foo"] = true;
</script>
```

### List rendering
```html
<div %arr></div>

 <li %people>
  <div>Index: {{__index}}</div>
  <div>Name: {{name}}</div>
  <div>Age: {{age}}</div>
</li>

<script type="module">
  import { state } from 'esy-state';
  state["arr"] = [1, 2, 3, 4, 5];
  state["people"] = [{ name: "John", age: 20 }, { name: "Jane", age: 21 }];
</script>
```

### Muanipulate the state (mutations)
```html
Hello <div #name>Noname</div>!
<input type="text" id="name" placeholder="Enter your name..">
<button @click="setName">Add</button>

<script type="module">
  import { state, mutations } from 'esy-state';
  mutations.setName = () => {
    const name = document.getElementById("name").value;
    state["name"] = name;
  };
</script>
```

## 🚀 Roadmap

- Known issue: Neasted list rendering is not possible yet.
- Improvment needed on: Mustache template implementation.
- Improvment needed on: Subscription handling.
- Figure out: Best way to distribute? CDN? NPM package?
- Figure out: Automatical testing? E2E?
- Figure out: Create a build/release pipline for version control.
- Better documentation.
- Release the first version.