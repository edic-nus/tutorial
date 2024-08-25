# Video Component

The video component is very similar to the image component, with the difference is that it display video instead. This is actually how video from site such as Youtube can be embedded in different webpage. The format is as follow:

```html
<video-component 
    tag="rick" 
    source="https://www.youtube.com/embed/dQw4w9WgXcQ"
    subtitle="Video: Never gonna give you up?"
></video-component>
```

The image componet has 3 main attributes:
- `tag`: this is the same as the `id` attributes in the `div` element, you can use this with `<a>` link to point to the picture.
- `source`: this is the source of your video, in this template, we encourage you to upload the video you want as a listed or unlisted video on Youtube first. Then, you can use the link provided from Youtube to your video as the source.Putting a video into the `assets` folder and then put the link to the source, may or may not work. It also bad practice as Github only meant to host small static file, so you might meet their file size restriction. 
- `subtitle`: add subtitle text under the video.

> <p class="note"> Note
>
> The video might not be able to render properly when you are using the local server. This is because Youtube is protecting your browser and their videos from potential exploit. Don't worry if it doesn't show the video properly on your website while developing. As long as the link is correct, it will load just fine once it is deployed to Github.

