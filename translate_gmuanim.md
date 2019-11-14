GMU_Anim (v2.1.0)
=====

*[Original document](https://github.com/GamemakerChina/GMU_Anim/blob/master/README.md)*. I only added the `In Undertale Engine` section.

---

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
2. Manaully create a Object named `_gmu_anim`, and create the same event of the file in `Objects/_gmu_anim` folder, and copy the file contents in the corresponding event.

Simple usage
-----
If you want to add easing for a room instance or a object, you only run the GMU_Anim_New(...) function *once* to add easing to specified object.
```cpp
GMU_Anim_New(target, "x", GMU_ANIM.QUAD, GMU_ANIM.OUT, 100, 200, 15, 30);
```
Let the `x` variable in all instances of the `target` object, using the `EaseOutQuart` effect, increment from 100 to 200 in 15 frames, run after 30 frames.<br>
`GMU_ANIM.QUAD` and `GMU_ANIM.OUT` are custom constants in the plugin, see the [Constants](#constants) part.<br>
This plugin supports all the effects listed in [https://easings.net](https://easings.net).

Functions
-----
**Bold**: New in TML's UNDERTALE Engine (as UNDERTALE Engine below)
<a id="gmu_anim_init"></a>
* GMU_Anim_Init(); [\[link\]](#gmu_anim_init)
	* Description
		* This function declares the constants. You don't need to call it.
	* In UNDERTALE Engine <a id="gmu_anim_init_ut_engine" href="#gmu_anim_init_ut_engine">\[link\]</a>
		* Anim_Init();

<a id="gmu_anim_new"></a>
* GMU_Anim_New(target, var_name, tween, ease, start, change, duration, delay*, arg1*, arg2*); [\[link\]](#gmu_anim_new)
	* Description
		* Create a easing instance
	* target
		* Target instance/object/global
	* var_name
		* Variable name (self-explanatory)
	* tween
		* Tween effect, see the [Constants](#constants) part
	* ease
		* Ease effect, see the [Constants](#constants) part
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
	* In UNDERTALE Engine <a id="gmu_anim_new_ut_engine" href="#gmu_anim_new_ut_engine">\[link\]</a>
		* Anim_Create(target, var_name, tween, ease, start, change, duration, delay*, arg_0*, arg_1*);

<a id="gmu_anim_stop"></a>
* GMU_Anim_Stop(target, var_name*); [\[link\]](#gmu_anim_stop)
	* Description
		* Stop target easing instance
	* target
		* Target easing instance/object/global
	* var_name (Optional)
		* Variable name, if you fill it, then it will only stop the easing instance for the specified variable.
	* Return value
		* Is there a easing instance stopped by this function call
	* In UNDERTALE Engine <a id="gmu_anim_stop_ut_engine" href="#gmu_anim_stop_ut_engine">\[link\]</a>
		* Anim_Destroy(target, var_name*, **skip\***);
			* skip (Optional)
				* Stops the easing instance early if specified as `false`
					* Works like GMU_Anim_Skip

<a id="gmu_anim_skip"></a>
* GMU_Anim_Skip(target, var_name*); [\[link\]](#gmu_anim_skip)
	* Description
		* Stops the easing instance early
	* target
		* Target easing instance/object/global
	* var_name (Optional)
		* Variable name, if you fill it, then it will only stop the easing instance for the specified variable early.
	* Return value
		* Is there a easing instance stopped early by this function call
	* In UNDERTALE Engine <a id="gmu_anim_skip_ut_engine" href="#gmu_anim_skip_ut_engine">\[link\]</a>
		* See Anim_Destroy

<a id="gmu_anim_isexists"></a>
* GMU_Anim_IsExists(target, var_name*); [\[link\]](#gmu_anim_isexists)
	* Description
		* Check if the target easing instance exists.
	* target
		* Target easing instance/object/global
	* var_name (Optional)
		* Variable name, if you fill it, then it will only query the easing instance for the specified variable.
	* Return value
		* Is the easing instance exists.
	* In UNDERTALE Engine <a id="gmu_anim_isexists_ut_engine" href="#gmu_anim_isexists_ut_engine">\[link\]</a>
		* Anim_IsExists(target, var_name*);

## Only in UNDERTALE Engine

<a id="ute_anim_step"></a>
* Anim_Step(); [\[link\]](#ute_anim_step)
	* Description
		* This function is for internal easing in GMU_Anim objects. You don't need (and better not to) to call it.
        * Return value
                * Always `true`

<a id="ute_anim_getvalue"></a>
* Anim_GetValue(tween, ease, time, arg_0*, arg_1*); [\[link\]](#ute_anim_getvalue)
	* Description
		* This function is for internal easing in [Anim_Step](#ute_anim_step). You don't need to call it.
        * tween
		* Tween effect, see the [Constants](#constants) part
	* ease
		* Ease effect, see the [Constants](#constants) part
	* time
                * Elapsed time
	* arg_0 (Optional)
		* Additional argument 1 
	* arg_1 (Optional)
		* Additional argument 2
        * Return value
                * A easing value for processing in Anim_Step(...)


<a id="ute_anim_uninit"></a>
* Anim_Uninit(); [\[link\]](#ute_anim_uninit)
	* Description
		* This function cleans up data created by GMU_Anim. You don't need (and better not to) to call it.
        * Return value
                * Always `true`

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
