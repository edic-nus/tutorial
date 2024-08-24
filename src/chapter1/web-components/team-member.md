# Team Member Component

The team member compoment / element is a **custom web component** specific to this template that we have built to simplify your portfolio development process. You can see the detail of its implementation in the `components/team-member` folder. In another word, you can't "Google" this element / component, so don't waste your time on that.

Here is the example presented to you in the template:

```html
<div class="team-member-wrapper">
  <team-member 
      avatar="assets/blackranger.png" 
      name="Black" 
      department="Mechanical Engineering"
      year="1993">
  </team-member>

  .... other elements ....
</div>
```

Let break it down into individual components to understand how to use this component correctly.

## The wrapper

The `<div>` element act as a wrapper around the content inside, this element was created for aesthetic purposes to help with all the `<team-member>` component layout. You can see its styling in the `team-member.css` file in the component folder.

## How to use this component

You have 4 attributes to take note of:
- `avatar`: the link to the person portrait.
- `name`: the name of the person.
- `department`: the home department of the person.
- `year`: the year you matriculate.

It is quite self-explanatory. You can list as many component as you want inside the `<div>` element and it will all be automatically nicely organised for you. It does not need to be 5, it can be 2 it can also be 6, it depends on your team size and how many `<team-member>` you add.

To add your portrait, take a nice and bright looking photo of yourself, and add it to the assets folder. Then you just have to link to that portrait as shown in the example template.

We suggest deleting and adding a few `<team-member>` components to get yourself familiar with how it works.
