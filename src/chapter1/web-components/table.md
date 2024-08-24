# Table Component

The table component will be the first component that require you to touch some Javascript. It is a bit harder to work with relative to other component, but don't worry, as long as you follow the tutorial carefully, it will just be some basic copy and paste job.

On the surface, here is what the table component looks like:

```html
<table-component subtitle="Table: Demo table">
  <div id="table-1"></div>
</table-component>
```

There is one important thing to take note of, that is the table `id`. This is very important for the table to work so please pay attention to it.


If you open up the javascript file in `components/table-component/table-component.js`. You should see something that looks like this:

```js
new gridjs.Grid({
  columns: ["Name", "Email", "Phone Number"],
  data: [
    ["John", "john@example.com", "(353) 01 222 3333"],
    ["Mark", "mark@gmail.com", "(01) 22 888 4444"],
    ["Eoin", "eoin@gmail.com", "0097 22 654 00033"],
    ["Sarah", "sarahcdd@gmail.com", "+322 876 1233"],
    ["Afshin", "afshin@mail.com", "(353) 22 87 8356"],
  ],
}).render(document.getElementById("table-1"));

class TableComponent extends HTMLElement {
  static get observedAttributes() {
    return ["subtitle"];
  }

  constructor() {
    super();
    this.attachShadow({ mode: "open" });
  }

  connectedCallback() {
    this.render();
  }

  attributeChangedCallback(name, _, newValue) {
    this[name] = newValue;
  }

  render() {
    const div = document.createElement("div");
    div.innerHTML = `
    <slot></slot>
    <sub>${this.subtitle}</sub>
    <style>
      :host {
        display: block;
        text-align: center;
      }

      sub {
        font-size: 1rem;
        font-style: italic;
      }
    </style>
  `;

    this.shadowRoot.appendChild(div);
  }
}

customElements.define("table-component", TableComponent);
```

We only need to focus on this section: 

```js
new gridjs.Grid({
  columns: ["Name", "Email", "Phone Number"],
  data: [
    ["John", "john@example.com", "(353) 01 222 3333"],
    ["Mark", "mark@gmail.com", "(01) 22 888 4444"],
    ["Eoin", "eoin@gmail.com", "0097 22 654 00033"],
    ["Sarah", "sarahcdd@gmail.com", "+322 876 1233"],
    ["Afshin", "afshin@mail.com", "(353) 22 87 8356"],
  ],
}).render(document.getElementById("table-1"));
```

The rest is just template code, and you don't need to pay attention to it. You can see at the bottom of the code, the `id` of `table-1` is mentioned again. This is how we attach our javascript code to the table component we use in our HTML.

## Creating custom table

From a brief look, it should be obvious where the data that get display on the table come from, it is under the `data` field. Now, we will teach you how to create a new table using the example above.

First, in the `index.html` create a new table component like so:

```html
<table-component subtitle="Table: Example table">
  <div id="example"></div>
</table-component>
```

Notice how the the `id` is now `example`.

Next we will copy the code exactly as above into the `table-component.js` file, so that you look something like this:

```js
new gridjs.Grid({
  columns: ["Name", "Email", "Phone Number"],
  data: [
    ["John", "john@example.com", "(353) 01 222 3333"],
    ["Mark", "mark@gmail.com", "(01) 22 888 4444"],
    ["Eoin", "eoin@gmail.com", "0097 22 654 00033"],
    ["Sarah", "sarahcdd@gmail.com", "+322 876 1233"],
    ["Afshin", "afshin@mail.com", "(353) 22 87 8356"],
  ],
}).render(document.getElementById("table-1"));

new gridjs.Grid({
  columns: ["Name", "Email", "Phone Number"],
  data: [
    ["John", "john@example.com", "(353) 01 222 3333"],
    ["Mark", "mark@gmail.com", "(01) 22 888 4444"],
    ["Eoin", "eoin@gmail.com", "0097 22 654 00033"],
    ["Sarah", "sarahcdd@gmail.com", "+322 876 1233"],
    ["Afshin", "afshin@mail.com", "(353) 22 87 8356"],
  ],
}).render(document.getElementById("table-1"));

// template code down here ...
```

Now, focus on the block of code that we just paste and modified it to point to the `example` instead.

```js
// ....

new gridjs.Grid({
  columns: ["Name", "Email", "Phone Number"],
  data: [
    ["John", "john@example.com", "(353) 01 222 3333"],
    ["Mark", "mark@gmail.com", "(01) 22 888 4444"],
    ["Eoin", "eoin@gmail.com", "0097 22 654 00033"],
    ["Sarah", "sarahcdd@gmail.com", "+322 876 1233"],
    ["Afshin", "afshin@mail.com", "(353) 22 87 8356"],
  ],
}).render(document.getElementById("example"));

// ...
```

Now, if we save the change made to the HTML and the change made to the Javascript file, we should see a new table that look exactly identical to our template table. Congratulation, you just use the table component successfully.

Now, to customize the table to your needs, you can change the `columns` to add or delete columns as you wish, just makre sure that the data you provided has the same length as the number of collumns that you have.  

```js
// ....

new gridjs.Grid({
  columns: ["Name", "Email"],
  data: [
    ["Red Ranger", "red@mpr.com"],
    ["Green Ranger", "green@mpr.com"],
  ],
}).render(document.getElementById("example"));

// ...
```

This table component is based on another library called [Grid.js](https://gridjs.io/). You can go into the documentation to epxlore more option that the library offered. You can do quite advanced thing like offering searching ability, ordering of data and more.
