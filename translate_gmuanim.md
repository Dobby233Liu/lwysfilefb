GMU_Anim (v2.1.0)
=====
*[Original document](https://github.com/GamemakerChina/GMU_Anim/blob/master/README.md)*. I only added the `In Undertale Engine` section.
Description
-----
This plugin is for simplifying easing of an instance variable.
Designed to accomplish complex easing processes using a single function.

For: GameMaker: Studio (referred as GM:S below) and GameMaker Studio 2 (referred as GMS2 below)

Installation
-----
YYMP extension pack install method (GMS2)
-----
Download the extension pack from [Releases](https://github.com/GamemakerChina/GMU_Anim/releases)
 (in `.yymp` format, don't forget to expand the assets section), then import all resources from it.

GMEZ extension pack install method (GM:S)
-----
Download the extension pack from [Releases](https://github.com/GamemakerChina/GMU_Anim/releases)
 (in `.gmez` format, don't forget to expand the assets section), then import all resources from it.
[GM:S version branch](https://github.com/LiarOnce/GMU_Anim/tree/gms1)

Manual installation
-----
After downloading the files to your local workspace:
1. Manually add all files in the Scripts folder.
2. Manaully create a Object named `_gmu_anim`, and create the same event of the file in `Objects\\_gmu_anim\\` folder, and copy the file contents in the corresponding event.

Simple usage
-----
If you want to add easing for a room instance or a object, you only run the GMU_Anim_New(...) function *once* to add easing to specified object.
```cpp
GMU_Anim_New(target, "x", GMU_ANIM.QUAD, GMU_ANIM.OUT, 100, 200, 15, 30);
```
Let the `x` variable in all instances of the `target` object, using the `EaseOutQuart` effect, increment from 100 to 200 in 15 frames, run after 30 frames.<br>
`GMU_ANIM.QUAD` and `GMU_ANIM.OUT` are custom constants in the plugin, see the `Constants` part.<br>
This plugin supports all the effects listed in [https://easings.net](https://easings.net).

Functions
-----
**Bold**: New in TML's UNDERTALE Engine (as UNDERTALE Engine below)
* GMU_Anim_Init();
	* Description
		* This function declares the constants. You don't need to call it.
	* In UNDERTALE Engine
		* Anim_Init();

* GMU_Anim_New(target, var_name, tween, ease, start, change, duration, delay*, arg1*, arg2*);
	* Description
		* Create a easing instance
	* target
		* Target instance/object/global
	* var_name
		* Variable name (self-explanatory)
	* tween
		* Tween effect, see the `Constants` part
	* ease
		* Ease effect, see the `Constants` part
	* start
		* Start value (self-explanatory)
	* change
		* Change value (self-explanatory)
	* duration
		* Duration (self-explanatory)
	* delay (Optional)
		* Delay (self-explanatory)
	* arg1 (Optional)
		* Additional argument 1 
	* arg2 (Optional)
		* Additional argument 2
	* Return value
		* Easing object; If there is multiple target instance, then returns a array
	* In UNDERTALE Engine
		* Anim_Create(target, var_name, tween, ease, start, change, duration, delay*, arg1*, arg2*);

* GMU_Anim_Stop(target, var_name*);
	* Description
		* Stop target easing instance
	* target
		* Target easing instance/object/global
	* var_name (Optional)
		* Variable name, if you fill it, then it will only stop the easing instance for the specified variable.
	* Return value
		* Is there a easing instance stopped by this function call
	* In UNDERTALE Engine
		* Anim_Destroy(target, var_name*, **skip\***);
			* skip (Optional)
				* Stops the easing instance early
					* Works like GMU_Anim_Skip

* GMU_Anim_Skip(target, var_name*);
	* Description
		* Stops the easing instance early
	* target
		* Target easing instance/object/global
	* var_name (Optional)
		* Variable name, if you fill it, then it will only stop the easing instance for the specified variable early.
	* Return value
		* Is there a easing instance stopped early by this function call
	* In UNDERTALE Engine
		* See Anim_Destroy

* GMU_Anim_IsExists(target, var_name*);
	* Description
		* Check if the target easing instance exists.
	* target
		* Target easing instance/object/global
	* var_name (Optional)
		* Variable name, if you fill it, then it will only query the easing instance for the specified variable.
	* Return value
		* Is the easing instance exists.

Constants
-----
Tween effect
-----
0. GMU_ANIM.LINEAR
1. GMU_ANIM.SINE
2. GMU_ANIM.QUAD
3. GMU_ANIM.CUBIC
4. GMU_ANIM.QUART
5. GMU_ANIM.QUINT
6. GMU_ANIM.EXPO
7. GMU_ANIM.CIRC
8. GMU_ANIM.BACK
9. GMU_ANIM.ELASTIC
10. GMU_ANIM.BOUNCE

Ease effect
-----
11. GMU_ANIM.IN
12. GMU_ANIM.OUT
13. GMU_ANIM.IN_OUT

You can watch these ease effects at https://easings.net