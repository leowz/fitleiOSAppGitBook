# Model View Controller

Embedded into the `HomeViewController`, `ModelViewController` is the key to present OpenGL content. It is a layer between application behavior and OpenGL functions as it is a subclass of `GLKViewController`.

---

## OverView

We can see and interact with `ModelViewController` through `HomeViewController` since the `ModelViewController` is added to the `HomeViewController`, and the main view, which is the avatar, in `HomeViewController` belongs to the `ModelViewController`.

Since this controller is a lower layer controller, there is no obvious user interaction events, so we will discuss it in term of methods it contains. In order to have a context of what will be discussed below, it is recommended to have a knowledge of `GLKViewController` and OpenGL basics, specially transformation.

![](/assets/gl_transform02.png)

### initialAvatarTransform: transformation

This is the method to set the initial values for transformation property of Model View Controller. Edit this method to change the initial stats of 3D avatar. It returns a transformation object initiated by the value set in the method.

The transformation property is used to compute `modelViewMatrix` that will be applied to 3D model.

This method can also be viewed to have stored an initial state of the avatar, by calling this method to set the value of transformation property, the avatar can be transformed to the initial state.

### calculateMatrices:

ModelViewController call this method to calculate transformation matrices. In the method, 3 kinds of matrices are calculated, including projection matrices, ModelView matrices, normal matrices.

In creating the projection matrix, we can set the value for the front plain and the back plain of the projection matrix in the function `GLKMatrix4MakePerspective` . We can also set the value for X axis rotation by setting the radius in the function `GLKMatrix4RotateX` .

In creating the modelView matrix, we can change the position and rotation of the avatar by setting the params of functions `GLKMatrix4Translate` ,  `GLKMatrix4RotateX` ,  `GLKMatrix4RotateZ` .

### Touch Events

* **pan**
  * change the z position of the avatar
* **pinch**

  * change the scale of the avatar

* **rotation**

  * rotate the avatar by y axis

* **tap**

  * tap twice to reset the avatar transformation to the initial value



