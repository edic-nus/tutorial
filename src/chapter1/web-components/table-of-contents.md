# Table of Contents Component

This is the first component that was not fully built by us and instead relying on an external web component library called [Shoelace](https://shoelace.style/). Shoelace provide a very handy way to design website with minimal dependency and no need to download anything.

The shoelace component is already preloaded as it is on the template, so there is no need for you to do anything extra to use it. You can visit the link above to see what other component you would maybe like to use. This is for more advanced developer, and you don't have to explore if you don't want to.

All the shoelace components / elements will have this following syntax `<sl-xxxxx>` with the acronym `sl` prefix in front.

Here is how table-of-content components look like in the template:

```html
<div class="table-of-content">
  <h2>Table of Contents</h2>
  <sl-tree>
    <sl-tree-item expanded>
      <a href="#section-header-1">1. Section Header 1</a>
      <sl-tree-item>
        <a href="#sub-section-1-header-1">1.1. Sub-section Header 1</a>
      </sl-tree-item>
      <sl-tree-item>
        <a href="#sub-section-1-header-2">1.2. Sub-section Header 2</a>
      </sl-tree-item>
    </sl-tree-item>

    <sl-tree-item expanded>
      <a href="#section-header-2">2. Section Header 1</a>
      <sl-tree-item>
        <a href="#sub-section-2-header-1">2.1. Sub-section Header 1</a>
      </sl-tree-item>
      <sl-tree-item>
        <a href="#sub-section-2-header-2">2.2. Sub-section Header 2</a>
      </sl-tree-item>
    </sl-tree-item>

    <sl-tree-item>
      <a href="#references">References</a>
    </sl-tree-item>
  </sl-tree>
</div>
```

As with previous component, the `div` element is used for styling purposes. So we can ignore it here. Same with the `h2` heading as it just dipslay the title. The actual main implementation of the table of contents start with the `<sl-tree>` element.

## Shoelace tree element

We are using the `tree` element in Shoelace to help us with structuring our table of contents. There are only 2 component you need to be awared of:

```html
<sl-tree></sl-tree>
<sl-tree-item></sl-tree-item>
```

The `<sl-tree>` is only used once as the wrapper around all of the `<sl-tree-item>`. We will pay more focus on the `<sl-tree-item>`.

In its most simple form, the `<sl-tree-item>` can be thought of a list item. Whatever is inside that element will be displayed as one list item for example:

```html
<sl-tree>
    <sl-tree-item> Item 1</sl-tree-item>
    <sl-tree-item> Item 2</sl-tree-item>
</sl-tree>
```

This should remind of you the standard structure of the `<ul>` and `<li>` pair in the [Basic elements](./basic-elements.md) section.

The tree allow us to nest an item within another item like so:

```html
<sl-tree>
    <sl-tree-item> 
      Item 1

      <sl-tree-item> Item 1.1 </sl-tree-item>
      <sl-tree-item> Item 1.2 </sl-tree-item>

    </sl-tree-item>

    <sl-tree-item> Item 2</sl-tree-item>
</sl-tree>
```

If you write the above code into the template, you should that the `Item 1` now has a drop down option. And if you click onto it, it will expand to show the `Item 1.1` and `Item 1.2`. If you want it to be expanded by default, like how we have our table content in the template, you just simply add the attribute `expanded` to the root item:

```html
<sl-tree>
    <sl-tree-item expanded>
      Item 1

      <sl-tree-item> Item 1.1 </sl-tree-item>
      <sl-tree-item> Item 1.2 </sl-tree-item>

    </sl-tree-item>

    <sl-tree-item> Item 2</sl-tree-item>
</sl-tree>
```

To complete our table of content component, we need to add the appropriate like referencing to each of our sections. To do so we just simply change the item text to the appropriate link `<a>` element.

```html
<sl-tree>
    <sl-tree-item expanded>
      <a href="#section-header-1">1. Section Header 1</a>

      <sl-tree-item>
        <a href="#sub-section-1-header-1">1.1. Sub-section Header 1</a>
      </sl-tree-item>

      <sl-tree-item>
        <a href="#sub-section-1-header-2">1.2. Sub-section Header 2</a>
      </sl-tree-item>

    </sl-tree-item>

    <sl-tree-item>
      <a href="#references">References</a>
    </sl-tree-item>
</sl-tree>
```

Please familiarize yourself with how to use the component by creating different nesting level of content and adding and modifying them to your liking.
