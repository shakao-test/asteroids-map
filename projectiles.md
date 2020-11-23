# Projectiles

## Introduction @unplugged

Now let's customize your ship! You can fire a projectile when the **A** button
is pressed, or add effects while your ship is moving.

## Add a button event

Find ``||controller:on A button pressed||`` in ``||controller:Controller||`` and drag it into the workspace.

```blocks
// @highlight
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
})
```

## Create a projectile

From ``||sprites:Sprites||`` drag ``||variables:projectile from mySprite||`` 
into the ``||controller:on A button pressed||``. Set the ``||sprites:vx||`` 
value to `0` and the ``||sprites:vy||`` to `-70`.

```blocks
let mySprite: Sprite = null
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    // @highlight
    let projectile = sprites.createProjectileFromSprite(img`.`, mySprite, 0, -70)
})
```

## Draw your projectile

Click on the grey square to open the image editor and draw your projectile. 
Try shooting the projectile in the simulator using your keyboard or click 
the **A** button.

```blocks
let mySprite: Sprite = null
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    // @highlight
    let projectile = sprites.createProjectileFromSprite(img`
3 3 3 3 3 3 3 3 
3 . . . . . . 3 
3 . 3 3 3 3 . 3 
3 . 3 . . 3 . 3 
3 . 3 . . 3 . 3 
3 . 3 3 3 3 . 3 
3 . . . . . . 3 
3 3 3 3 3 3 3 3 
    `, mySprite, 0, -70)
})
```

## Custom effects

Time for some special effects! From ``||sprites:Sprites||``, drag the 
``||sprites:mySprite start effects||`` block **after** 
``||variables:projectile from mySprite||``. Click on the dropdown and try out
some different effects! You can also use this block to set an effect on your
spaceship.

```blocks
let mySprite: Sprite = null
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    let projectile = sprites.createProjectileFromSprite(img`
3 3 3 3 3 3 3 3 
3 . . . . . . 3 
3 . 3 3 3 3 . 3 
3 . 3 . . 3 . 3 
3 . 3 . . 3 . 3 
3 . 3 3 3 3 . 3 
3 . . . . . . 3 
3 3 3 3 3 3 3 3 
    `, mySprite, 0, -70)
    // @highlight
    projectile.startEffect(effects.fire);
})
```

```template
effects.starField.startScreenEffect()
let mySprite = sprites.create(img`
    . . . . . . . 9 9 . . . . . . .
    . . . . . . 9 . . 9 . . . . . .
    . . . . . . 9 . . 9 . . . . . .
    . . . . . 9 . 9 9 . 9 . . . . .
    . . . . . 9 . 9 9 . 9 . . . . .
    . . . . 9 . 9 9 9 9 . 9 . . . .
    . . . . 9 . 9 9 9 9 . 9 . . . .
    . . . 9 . 9 9 9 9 9 9 . 9 . . .
    . . . 9 . 9 . . . . 9 . 9 . . .
    . . 9 . 9 9 . 9 9 . 9 9 . 9 . .
    . . 9 . 9 9 . . . . 9 9 . 9 . .
    . 9 . 9 9 9 . 9 9 9 9 9 9 . 9 .
    . 9 . 9 9 9 . 9 9 9 9 9 9 . 9 .
    9 . 9 9 9 9 9 9 9 9 9 9 9 9 . 9
    9 . . . . . . . . . . . . . . 9
    9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9
`, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setFlag(SpriteFlag.StayInScreen, true)
```
