# Working with 3D Render

To render 3D object such as your CAD in the format of `.stl` file, we will use the [Three.js](https://threejs.org/) library. It is a very cool library that allows you to do mind-blowing graphic stuff in the browser. However, it is very out-of-scope for our purpose, so we have helped written a component script so you can just simply use it with minimal configuration to display your `.stl` file.

To use the 3D render component, we need to import the following into our `index.html` file.

```html
<head>
  ...

  <script type="importmap">
  {
    "imports": {
      "three": "https://cdn.jsdelivr.net/npm/three@v0.166.1/build/three.module.js",
      "three/addons/": "https://cdn.jsdelivr.net/npm/three@v0.166.1/examples/jsm/"
    }
  }
  </script>
  <script type="module"
    src="https://cdn.jsdelivr.net/npm/@shoelace-style/shoelace@2.16.0/cdn/shoelace-autoloader.js"></script>

  ...

  <script type="module" src="./render.js"></script>
</body>
```

It is a bit more complicated than other module because of the `three.js` library. It is important that you make sure the import is in the order above for `three.js` to work properly. Don't forget the `type="module"` when importing the `render.js` file as it is necessary for the script to work properly.

To use the component, you just simply have to create a `<div>` with the `id` value that you want:

```html
<div id="render1"></div>
```

Then, in the `render.js` file call the `createRender` function accordingly as shown.

```js
createRender(
  "render1",
  400,
  [0, -1, 0],
  [0.05, 0.05, 0.05],
  [-Math.PI / 2, 0, 0],
  false,
  "../assets/benchy.stl",
);
```

It will render your `.stl` file in the specified `<div>`.

Now, let take a loot at what each of the arguments means, and how you can use them:

```js
function createRender(
  id,
  height,
  position,
  scale,
  rotation,
  enableAxes,
  stlFilePath,
) {
```

- `id`: is the id you gave to the `div` element that you want to render your `.stl` to.
- `height`: is the height in pixel of the view box of your object. You can adjust the width by modifying the `div` width directly
- `position`: the position of your object in 3D space, in the following order [x , y , z]
- `scale`: same as position but for scaling, you will have to experiment to see what scale would work for you as some stl can be very big, and some can be very small.
- `rotation`: same as position and scale, but for the rotation angle of your object. It uses Euler angle. As a rule of thumb you should use `Math.PI / 2` as trial value because it equals to a rotation of 90 degree.
- `enableAxes`: whether you want to enable the X Y Z axis for debugging purposes or not.
- `stlFilePath`: this is the path to your `.stl` file. Do note that Github has file size limitations to what you can upload there, so if your CAD is just too big in memory size, maybe it would be better if you upload it to some other storage method such as Google Drive or Dropbox and then provide the url to that `stl` file here. Otherwise, just put your `stl` file into the `assets` folder, and write the correct path to that `stl` file here.

Rendering 3D can be quite intensive on some more underpowered devices, so try to only use this component to show things that would highlight your effort instead of dumping every single CAD that you have here. Because remember, the user would need to download all of you CAD before they can view them, so it doesn't make sense to make user download 1GB worth of CAD to view it for only 5 seconds.

In another word, use this component prudently and responsibly.
