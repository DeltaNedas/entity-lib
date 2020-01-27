# Entity Lib

Adds a global field `entityLib`.

You can extend classes `entityLib.Mech` or `entityLib.Unit`.

By default, it functions like a vanilla one.

# How to use

Add `entity-lib` to your `dependencies: []` in **mod.hjson**.

You may extend: (where Entity is Player or Unit)

* drawWeapon(Entity entity, float rotation, int number): draw weapons how you want.
* drawUnder(Entity entity): draw sprites underneath the weapons. Optional.
* drawOver(Entity entity): draw sprites above the weapons. Optional.


# Functions and fields

`trueRotation(Entity entity)`: get rotation after all limits are processed.

`trueRotation(Entity entity, float rotation)`: set the true rotation.

`rotationLimit` is maximum rotation per tick.

`weapons` are an array of `Weapon`s to be fired.

See example code below:
```js
const myMech = extendContent(entityLib.Mech, "my-mech", {
	drawUnder: function(player){
		Draw.rect(Core.atlas.find("error"), player.x, player.y, this.trueRotation);
	}
});
myMech.rotationLimit = 1; // 60' per second usually
myMech.rotationLerp = 0.02;
myMech.weapons = [
	Mechs.omega.weapon,
	Mechs.dart.weapon,
	Mechs.duo.weapon
];
```
