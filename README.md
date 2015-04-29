#i915_backlight_freebsd

##Backlight support for the i915 driver via sysctl.

This patch is against **FreeBSD 11-CURRENT**.

You must know how to compile and install the kernel in FreeBSD :-).

Instructions:

* Download i915_backlight.patch
* Install the patch :
```
 # cd /
 # patch < i915_backlight.patch
```
* Rebuild and install the kernel.

Now you can control the backlight of your laptop via sysctl:

* set backlight to 10%
```
# sysctl hw.dri.0.i915_backlight=10
hw.dri.0.i915_backlight: 9 -> 10
```
* set backlight to 20%
```
# sysctl hw.dri.0.i915_backlight=20
hw.dri.0.i915_backlight: 10 -> 20
```
* increment the backlight
```
# sysctl -n hw.dri.0.i915_backlight=1000
20 -> 25
```
* decrement the backlight
```
# sysctl -n hw.dri.0.i915_backlight=-1000
25 -> 20
```
* decrement the backlight
```
# sysctl hw.dri.0.i915_backlight=-1000
hw.dri.0.i915_backlight: 20 -> 16
```
You can also set the initial backlight at boot in **/boot/loader.conf** :
```
drm.i915.init_backlight=10
```
or via **/etc/sysctl.conf**
```
hw.dri.0.i915_backlight=10
```
set a 10% backlight.
