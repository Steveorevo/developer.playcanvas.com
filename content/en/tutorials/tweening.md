---
title: Using the Tween library
template: tutorial-page.tmpl.html
tags: animation, scripts
thumb: https://s3-eu-west-1.amazonaws.com/images.playcanvas.com/projects/12/452634/BDFB7E-image-75.jpg
---

Often we want to animate an Entity or some arbitrary value between two points. This is called tweening. We have created a tweening library for that exact purpose. You can find the library at [https://github.com/playcanvas/playcanvas-tween][1].

To use the library just upload the `tween.js` file to your project. This will allow you to tween Entity properties like position, rotation, scale etc like so:

```javascript
entity.tween(entity.getLocalPosition()).to({x: 10, y: 0, z: 0}, 1, pc.SineOut);
```

Here is an example on how to tween the local position of an Entity:

<iframe src="https://playcanv.as/b/wEftzstB/"></iframe>

Here are links to the [Project][2] and the [Editor][3] for this example.

Here is an example on how to tween the local rotation of an Entity:

<iframe src="https://playcanv.as/b/H8553dGa/"></iframe>

Here are links to the [Project][2] and the [Editor][4] for this example.

Here's how to tween the local scale of an Entity:

<iframe src="https://playcanv.as/b/ndTiHCpD/"></iframe>

Here are links to the [Project][2] and the [Editor][5] for this example.

And finally here's a way to tween colors:

<iframe src="https://playcanv.as/b/aoRYsYrc/"></iframe>

Here are links to the [Project][2] and the [Editor][6] for this example.


[1]: https://github.com/playcanvas/playcanvas-tween
[2]: https://playcanvas.com/project/452634/overview/using-the-tween-library
[3]: https://playcanvas.com/editor/scene/491504
[4]: https://playcanvas.com/editor/scene/491558
[5]: https://playcanvas.com/editor/scene/491585
[6]: https://playcanvas.com/editor/scene/491559