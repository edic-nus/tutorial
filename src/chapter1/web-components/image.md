# Image Component

The image component is a simple component that can be used to quickly display an image with an attached subtitle. The format is as follow:

```html
<image-component 
    tag="image" 
    source="assets/requirement.png"
    subtitle="Image 1: iDP suggested pathway"
></image-component>
```

The image componet has 3 main attributes:
- `tag`: this is the same as the `id` attributes in the `div` element, you can use this with `<a>` link to point to the picture.
- `source`: this is the source of your image, it can be an image in the `assets` folder like in the example, or it could also be an url pointing to an image from an external page.
- `subtitle`: add subtitle text under the image.

This is a very simple component that you can also create through raw html, but if you don't need much modifications, using this component would be faster and cleaner.
