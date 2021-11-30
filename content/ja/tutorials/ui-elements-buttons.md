---
title: ユーザインターフェイス - ボタン
template: tutorial-page.tmpl.html
tags: ui
thumb: https://s3-eu-west-1.amazonaws.com/images.playcanvas.com/projects/12/501973/ED1B35-image-75.jpg
---

<iframe src="https://playcanv.as/p/jpRiV53D/"></iframe>

*Simple buttons using Element and Button components. See the [full scene][1].*

アプリケーションのUIを構築する際、通常はボタンを作成する必要があります。このチュートリアルでは、組み込みの[Element][2]を使用してそれを実現する方法を示します。

この[シーン][1]では、階層内で次のような2D[Screen][3]を作成しました。

![階層][4]

## スクリーン設定

スクリーンは次のように設定されています：

![スクリーン][5]

それは2Dスクリーンなので、スクリーンスペースをチェックしました。リファレンス解像度は、目標とする解像度です。この場合は1080 x 1920です。ScaleモードのBlendを選択して、画面が解像度の変更に適応するようにし、Scale Blendを1に設定して、画面が高さの変化のみに適応するようにします。

画面には、上部に表示されるロゴのImage Elementや'SELECT QUALITY'のテキストを示すText Elementと3つのボタンなどのさまざまな子があります。

## Adding a button to the UI

There are two ways to add a button to the scene.

### Via the Hierarchy Panel

This is the easiest way to add a button to the scene as it creates the necessary entities, components and preconfigures the properties.

<img src="/images/tutorials/ui/buttons/adding-button-via-hierarchy.gif">

### With an existing Element

If there is an existing Element that we would like to turn into a button, we can add Button component to it in the Inspector panel and configure it ourselves.

<img src="/images/tutorials/ui/buttons/adding-button-via-inspector.gif" width="300px">

Remember to enable Use Input on the Element component so the user can interact with it:

<img src="/images/tutorials/ui/buttons/use-input-element.png" width="300px">

And set the Image Entity property on the Button component to be same Entity that the Element component is on.

<img src="/images/tutorials/ui/buttons/set-image-entity-button.png" width="300px">

## ボタン設定

Let's take a closer look at the first button in the example project:

<img src="/images/tutorials/ui/buttons/button.png" width="300px">

The button has 3 components:

- **Element component** - Positions the renders the button UI relative to it's parent Screen.
- **Button component** - Handles how the button looks when the user is interacting with it.
- **Script component** - Listens for events on the Button component and handles the logic on what to do when clicked.

The button Entity also has a Text Element as a child for showing text (this is optional depending on the style of your button).

<img src="/images/tutorials/ui/buttons/text-element.png" width="300px">

The Element's type is Image and it's anchored to the bottom of the screen.

<img src="/images/tutorials/ui/buttons/bottom-anchor-pivot.png" width="300px">

After anchoring the button we give it an offset from the bottom by simply moving it up.

<img src="/images/tutorials/ui/buttons/offset-position.png" width="300px">

We also have Use Input enabled in order to interact with the button.

<img src="/images/tutorials/ui/buttons/use-input-element.png" width="300px">

### Changing how the button looks on interaction

We can change how the button looks when the user interacts with the button for the following states:

- **Hover** - When the mouse cursor is over the button.
- **Pressed** - When the user presses on the button.
- **Inactive** - When the button is inactive.

This can be done via two Transition Modes:

#### Tinting the color

Tinting the button color in each state is the easiest method to add some user feedback when they interact with it. In the project, the High Quality button has the following setup:

<img src="/images/tutorials/ui/buttons/high-quality-button-setup.png" width="300px">

With the following effect:

<img src="/images/tutorials/ui/buttons/high-quality-button-effect.gif">

#### Changing the Sprite

We can also change the sprite image of the button in the different states for cases where you may want the button to change shape or want to give a look of the button being 'pressed' into the screen. The Low Quality button has the following setup:

<img src="/images/tutorials/ui/buttons/low-quality-button-setup.png" width="300px">

With the following effect:

<img src="/images/tutorials/ui/buttons/low-quality-button-effect.gif">

### Button events

We have a script in the project that listens for when the user clicks on the button and updates the text in the UI to the quality setting that they've selected.

```javascript
var ButtonLogic = pc.createScript('buttonLogic');
ButtonLogic.attributes.add('textEntity', {
    type: 'entity',
    description: 'The entity that we want to update when the button is clicked'
});
ButtonLogic.attributes.add('description', {type: 'string'});

// initialize code called once per entity
ButtonLogic.prototype.initialize = function() {
    this.entity.button.on('click', function(event) {
        this.textEntity.element.text = this.description;
    }, this);
};
```
This script is attached to the button entities in the scene.

The Button component has a [`click` event][click-event-api] against which a callback function can be registered that works for both mouse and touch input.

```javascript
this.entity.button.on('click', function(event) {
    this.textEntity.element.text = this.description;
}, this);
```

There are other events that can be listened to such as `mouseenter` and `mouseleave`. A full list can be found in the [API documentation][click-event-api].

These events will only fire if Use Input is enabled on the Element component so make sure that has been ticked in the inspector.

<img src="/images/tutorials/ui/buttons/use-input-element.png" width="300px">

[1]: https://playcanvas.com/editor/scene/547900
[2]: /user-manual/user-interface/elements/
[3]: /user-manual/user-interface/screens/
[4]: /images/tutorials/ui/buttons/hierarchy.png
[5]: /images/tutorials/ui/buttons/screen.png
[6]: /images/tutorials/ui/buttons/button.png
[elements-tutorial]: /user-manual/user-interface/elements/
[click-event-api]: /api/pc.ButtonComponent.html#event:click
