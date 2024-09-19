# Working with Chart.js

To make the process of creating chart simple and streamline, we will utilize [Chart.js](https://www.chartjs.org/docs/latest/) library. If you open up the `index.html` in the `chart` folder. You should see the following:

```html
<!DOCTYPE html>
<html lang="en">

<head>
  .....

  <!-- You can add what components you want to include here  -->
  <link rel="stylesheet" href="../index.css">
  <link rel="stylesheet" href="../components/scroll-to-top/scroll-to-top.css">
  <script src="../components/scroll-to-top/scroll-to-top.js"></script>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <!--  -->
</head>

<body>
  <div class="content">
    <sl-button href="../">Back</sl-button>

    <h2 id="pie-doughtnut">1. Pie and Doughnut Chart</h2>
    <div style="display: flex; justify-content: space-around;">
      <div style="width: 45%;">
        <canvas id="pie-chart"></canvas>
      </div>
      <div style="width: 45%;">
        <canvas id="doughnut-chart"></canvas>
      </div>
    </div>

    <br />
    <h2 id="bar">2. Bar Chart</h2>
    <div>
      <canvas id="bar-chart"></canvas>
    </div>

    <br />
    <h2 id="line">3. Line Chart</h2>
    <div>
      <canvas id="line-chart"></canvas>
    </div>

    <br />
    <h2 id="scatter">4. Scatter Chart</h2>
    <div>
      <canvas id="scatter-chart"></canvas>
    </div>

    <sl-button class="scroll-to-top" variant="primary" size="medium" circle onclick="scrollToTop()">
      <sl-icon name="arrow-up" label="Settings"></sl-icon>
    </sl-button>

    <script src="./chart.js"></script>
</body>

</html>
```

We import the `Chart.js` library by simply adding the following line:

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
```

Now, we will create elements where we will draw the chart using Javascript later. To do that we use the following syntax:

```html
<div>
    <canvas id="something-chart></canvas>
</div>
```

The `id` can be anything you want, but remember that it should be unique to each graph because that is how you differentiate them in the Javascript code section later.

You would also notice that differnt from our usual way of import, we need to import the `chart.js` file at the bottom of the `<body>` element:

```html
    ...

    <sl-button class="scroll-to-top" variant="primary" size="medium" circle onclick="scrollToTop()">
      <sl-icon name="arrow-up" label="Settings"></sl-icon>
    </sl-button>

    <script src="./chart.js"></script>
</body>
```

This is because Javascript cannot grab an element if it has not been initialized yet. As we will see in the subsequent code in `chart.js`, it needs to know that `pie-chart` exist, before it can grab that elements, so we cannot declare the import before the declaration of the elements. In general, people tend to import Javascript code at the bottom of the body for this reason, but for organisation purpose, we would like to put thing related together closer to each other unless we have no other choice.

Now open up the `chart.js` file. Take this sample code:

```js
const PieCtx = document.getElementById("pie-chart");
const DoughnutCtx = document.getElementById("doughnut-chart");

const PieData = {
  labels: ["Red", "Blue", "Yellow"],
  datasets: [
    {
      label: "My First Dataset",
      data: [300, 50, 100],
      backgroundColor: [
        "rgb(255, 99, 132)",
        "rgb(54, 162, 235)",
        "rgb(255, 205, 86)",
      ],
      hoverOffset: 4,
    },
  ],
};

new Chart(PieCtx, {
  type: "pie",
  data: PieData,
});

new Chart(DoughnutCtx, {
  type: "doughnut",
  data: PieData,
});
```

The `PieCtx` constant holds the container which is the `<canvas id="pie-chart"></canvas>`, this is how we tell Javascript which `<canvas>` to draw what which is why we need the `id` to be unique.

Then we define what the data we want the chart to render. We will go indepth into this in a bit.

Finally, we will render this chart. To do this the syntax is:

```js
new Chart(ctx, {
    type: "pie",
    data: PieData
})
```

Where `ctx` stands for context, in another word, the `<canvas>` element that you grab. `type` refer to chart type you want to render, and finally the data you want the chart to render.

Now, we will go more indepth regarding the configuration of each graph, you could also learn more directly from [here](https://www.chartjs.org/docs/latest/charts/)

## 1. Pie and Doughnut Chart

```js
const PieData = {
  labels: ["Red", "Blue", "Yellow"],
  datasets: [
    {
      label: "My First Dataset",
      data: [300, 50, 100],
      backgroundColor: [
        "rgb(255, 99, 132)",
        "rgb(54, 162, 235)",
        "rgb(255, 205, 86)",
      ],
      hoverOffset: 4,
    },
  ],
};
```

Let break down what each of this fields means:
- `labels`: the labels for your data, it should match with the number of data you have
- `datasets`: the content of chart
    - `label`: is the label for this particular dataset, it will make more sense in subsequent charts
    - `data`: this is where you specify your data in an array, make sure you have same number of data as the labels
    - `backgroundColor`: this is for aesthetic purpose, you can use any standard css color syntax. If you don't want any color variation, just delete this portion.
    - `hoverOffset`: is just show how far should the offset from the center of the chart where the tooltip show when you hover over the chart

## 2. Bar Chart

```js
const BarData = {
  labels: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul"],
  datasets: [
    {
      label: "My First Dataset",
      data: [65, 59, 80, 81, 56, 55, 40],
      borderWidth: 1,
    },
    {
      label: "My Second Dataset",
      data: [23, 40, 67, 20, 79, 30, 80],
      borderWidth: 1,
    },
  ],
};
```

We can see that the `datasets` now have 2 set of data: `My First Dataset` and `My Second Dataset`.

This is why datasets is declared as an array of object. Because you can show one or more dataset on the same chart space.

`borderWidth` just specify how thick the border of the bar you want them to be.

## 3. Line Chart

```js
const LineData = {
  labels: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul"],
  datasets: [
    {
      label: "My First Dataset",
      data: [65, 59, 80, 81, 56, 55, 40],
      fill: false,
      tension: 0.1,
    },
    {
      label: "My Second Dataset",
      data: [23, 40, 67, 20, 79, 30, 80],
      tension: 0.1,
    },
  ],
};
```

- `fill`: whether you want the area under the line to be filled or not.
- `tension`: whether you want to smooth out the turn at each data point. At 0, it will just be straightline connect at each data point.

## 4. Scatter Chart

```js
const ScatterData = {
  datasets: [
    {
      label: "Scatter Dataset",
      data: [
        {
          x: 2,
          y: 4,
        },
        {
          x: 3,
          y: 2,
        },
        {
          x: 4,
          y: 5,
        },
        {
          x: 0.5,
          y: 5.5,
        },
      ],
      backgroundColor: "rgb(255, 99, 132)",
    },
  ],
};
```

Each data point in a scatter chart requires an `x` and `y` coordinates. We suggest that if you need to use a scatter graph, you should create a simple Python script maybe with the help of ChatGPT to convert all of your data to the format above and then just copy paste accordingly.
