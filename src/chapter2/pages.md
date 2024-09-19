# Make your report into multiple pages

In this section, we will learn how to split the content up into their respective pages so that you can more neatly organised your content for readability.

## 1. Create a new content page

So we have learn from Chapter 1 that when you visit your web report on Github, it will serve the `index.html` file back down to your browser and the rest of your report is render from there. However, if you try to cramp your whole report into only one page, it can become quite lengthy and sluggish to read. Overall, it is not just an ideal web experience. 

It is in fact quite trivial to split up the content into their own respective pages. If you look at the [template repo](https://github.com/edic-nus/advanced), you can see that to create a new page, we can simply just create a new folder and put another `index.html` file inside it.

Take for example the `chart` folder. If you look inside, you can see that there are 2 files:
- `chart.js`
- `index.html`

So when you visit the path:

> https://edic-nus.github.io/advanced/chart/

It will render the `index.html` file inside the `chart` folder on your browser. You can try the same thing for `/diagram` and `/3d-render`.

So to summarize, to create a new page for your report. You just simply have to create a new folder and put a `index.html` file inside it. The name of your folder will be the name of your path.

> <p class="warn"> Warning
> 
> This should come as something obvious but you should not use a name with a special character (eg. space, tab, etc.) in them, as it might have trouble linking the path correctly. As a standard practice, just use a one word name such as `about` or `diagram`. If you need more than one word, use `-` to connect the words instead: `about-us`. 

## 2. Using `template-page.html`

Now that you know how creating a new page works, you must be wondering what to put into the `index.html` file. No worry, we have provided you with a template so you can just copy paste everytime you create a new page. You can find it in our demo code under the name `template-page.html`. Let's take a look at what is inside the template and how to use it.

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Project Title</title>
  <link rel="icon" href="./favicon.ico" type="image/x-icon">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@shoelace-style/shoelace@2.16.0/cdn/themes/light.css" />
  <script type="module"
    src="https://cdn.jsdelivr.net/npm/@shoelace-style/shoelace@2.16.0/cdn/shoelace-autoloader.js"></script>

  <!-- You can add what components you want to include here  -->
  <link rel="stylesheet" href="./index.css">
  <link rel="stylesheet" href="./components/scroll-to-top/scroll-to-top.css">
  <script src="./components/scroll-to-top/scroll-to-top.js"></script>

  <!--  -->
</head>

<body>
  <div class="content">
    <sl-button href="../">Back</sl-button>

    <sl-button class="scroll-to-top" variant="primary" size="medium" circle onclick="scrollToTop()">
      <sl-icon name="arrow-up" label="Settings"></sl-icon>
    </sl-button>
</body>

</html>
```

As you can see, it is quite a short file. For the most parts, you can ignore all of it. There are only 2 things that you should pay attention to, that is:

1. How to add components that you need
2. How the back button works

### 2.1. How to add components that you need

Look at this portion of the code:

```html
<!-- You can add what components you want to include here  -->
<link rel="stylesheet" href="./index.css">
<link rel="stylesheet" href="./components/scroll-to-top/scroll-to-top.css">
<script src="./components/scroll-to-top/scroll-to-top.js"></script>

<!--  -->
```

There are 2 kinds of import that we utilize that is `<link>` and `<script>`.

We use:

```html
<link rel="stylesheet" href="./index.css">
```

to import the css files needed to add styling to your web page. Here, you can see that we are importing the style from the `index.css` file and the `scroll-to-top.css` file in the components folder. 

We use:

```html
<script src="./components/scroll-to-top/scroll-to-top.js"></script>
```

to import the js files needed to run the javascript for that web page.

Please note that, you would have to do this for every new `index.html` file you created, as importing on one `index.html` does not get share with other `index.html` files in different folders / paths.

One of the important thing to understand is how path syntax works to tell the element in HTMl to figure out where your file is located relative to each other.

- `./` is used to specify looking at the current folder and locate the file. For example: `./components/scroll-to-top/scroll-to-top.css` means to look in the current folder, find `components` folder, go into `components` folder, find `scroll-to-top` folder, go into `scroll-to-top` folder, and find `scroll-to-top.css` file.
- `../` is use to go 1 folder above the current folder. For example, if you are currently in the `scroll-to-top` folder, then `../scroll-to-top` is one folder above / outside of it, that would be the `components` folder.

I know it could be a bit confusing, but the best way to get used to it is just try to add components yourself to see how the path would work, and if you are stuck you can ask ChatGPT for help in figuring out how to import your files correctly.

With that out of the way, you should notice by now, that with our current path declaration, our template would not be able to properly import `index.css` file when it is used inside another folder. That is because it used `./index.css`. But when inside another folder, such as `chart`, it actually needs to be `../index.css` instead, because the file `index.css` is in a folder one level above the `chart` folder. So do pay attention to this when trying to import file from different location.

### 2.2. How the back button works

Let look at the code:

```html
<sl-button href="../">Back</sl-button>
```

You should have noticed that we used a shoelace button from the introduction to Shoelace in previous chapter. However, you could also just use the default button provided by html, there is no different in functionality.

You should see that the `href` attribute use the same path syntax that we have discussed above. This is because navigating within a website is very similar to how you navigate between folders. So a `href="../"` just simply mean to go one folder above, or in another words, go back to our main folder that contains the entry `index.html`.

## 3. How to navigate between pages

Now that we roughly understand how path syntax works, let looks at how do we provide link from one page to another. If we open up the main entry `index.html` files, you can see the familiar Table of Contents code:

```html
<div class="table-of-content">
  <h2>Table of Contents</h2>
  <sl-tree>
    <sl-tree-item expanded>
      <a href="./chart/">Chart</a>
      <sl-tree-item>
        <a href="./chart/#pie-doughnut">1. Pie and Doughnut Chart</a>
      </sl-tree-item>
      <sl-tree-item>
        <a href="./chart/#bar">2. Bar Chart</a>
      </sl-tree-item>
      <sl-tree-item>
        <a href="./chart/#line">3. Line Chart</a>
      </sl-tree-item>
      <sl-tree-item>
        <a href="./chart/#scatter">4. Scatter Chart</a>
      </sl-tree-item>
    </sl-tree-item>

    <sl-tree-item>
      <a href="./diagram/">Interactive diagram</a>
    </sl-tree-item>

    <sl-tree-item>
      <a href="./3d-render/">3D Render</a>
    </sl-tree-item>
  </sl-tree>
</div>
```

What to focus on here is the value we provided to the `href` attribute. Using our previous knowledge regarding path, it should be easy to see that `./chart/` means to go to the `chart` folder or equivalently the `/chart/` path in the url. As long as you understand this concept, the rest is similar to what we have learnt in Chapter 1. To specify a `id` we want to target in another page, we just have to add the `#id` syntax in the url as shown above. 
