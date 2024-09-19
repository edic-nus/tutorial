# Working with Mermaid.js

[Mermaid.js](https://mermaid.js.org) can be said to be the defacto standard when it comes to creating diagram using Domain Specific Language. In fact, if you have ever seen diagram being render on Github repository before, it is all thanks to mermaid.js.

This section won't be teaching you how to create diagram but only how to allow you to render those diagram. To learn how to create this beautiful diagram, you can read their [document](https://mermaid.js.org/syntax/flowchart.html) or use their [Live Editor](https://mermaid.live) instead. 

If you open the `diagram` folder, you should be able to see 3 files:

- `index.html`
- `diagram.js`
- `svg-pan-zoom.min.js`

In the `index.html` file, we import 2 things:

```html
<script src="https://cdn.jsdelivr.net/npm/mermaid@11.2.1/dist/mermaid.min.js"></script>
<script src="svg-pan-zoom.min.js"></script>
```

The former is to import `mermaid.js`, the latter is to import the `svg-pan-zoom` library. Since this library have a bit of a problem being loaded from the CDN, we instead download it down to a file locally and name it as `svg-pan-zoom.min.js`.

The purpose of the `svg-pan-zoom` is allowing us to zoom in and out and pan around our diagram, which will allow you to draw bigger diagram without worrying that it is not readable. This is the main advantage over just taking a picture of your diagram. You don't have to use it if you don't want to, but it surely would make your report more interactive.

To render a mermaid chart, you just have to declare the `<pre>` element and give it the mermaid class. It will automatically be rendered.

Similar to the chart, we need to import `diagram.js` file at the bottom of the `<body>` element.

```html
    ...

    <sl-button class="scroll-to-top" variant="primary" size="medium" circle onclick="scrollToTop()">
      <sl-icon name="arrow-up" label="Settings"></sl-icon>
    </sl-button>

    <script src="./diagram.js"></script>
</body>
```

We don't actually need to know what is happening in the `diagram.js` file as it is only glue code to help with stitching the `svg-pan-zoom` with `mermaid.js` library. Just remember to include all of this file if you decide to use mermaid.js to draw your diagram.
