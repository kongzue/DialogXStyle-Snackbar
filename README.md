# DialogXStyle-Snackbar

此主题包适用于 [DialogX](https://github.com/kongzue/DialogX) 框架的 PopTip 组件，提供 Snackbar 样式（含亮、暗色）

![Snackbar](https://raw.githubusercontent.com/kongzue/DialogXStyle-Snackbar/master/readme/SnakebarStyle.png)

## 使用方式

警告：此主题包需要您升级 DialogX 的版本至 0.0.35 以上的版本。

1. 进入 build.gradle(Project) 文件，在`allprojects`代码快添加：

   ```
   allprojects {
       repositories {
           google()
           jcenter()
           maven{
               url 'https://jitpack.io'
           }
       }
   }
   ```

2. 在 build.gradle(app) 文件引入主题资源：

   ```
   implementation 'com.github.kongzue:DialogXStyle-Snackbar:1.0.5'
   ```

3. 找到 DialogX.globalStyle 设置，没有可以直接使用 MaterialStyle，如果有设置其他的主题，可使用该主题 Style 替代下边代码中的 MaterialStyle，重写 popTipSettings 即可完成设置：

   ```
   DialogX.globalStyle = new MaterialStyle(){
       @Override
       public PopTipSettings popTipSettings() {
           return new PopTipSettings() {
               @Override
               public int layout(boolean light) {
                   return light?R.layout.layout_dialogx_poptip_snackbar:R.layout.layout_dialogx_poptip_snackbar_dark;
               }
               @Override
               public ALIGN align() {
                   return ALIGN.BOTTOM;
               }
               @Override
               public int enterAnimResId(boolean light) {
                   return com.kongzue.dialogx.R.anim.anim_dialogx_default_enter;
               }
               @Override
               public int exitAnimResId(boolean light) {
                   return com.kongzue.dialogx.R.anim.anim_dialogx_default_exit;
               }
           };
       }
   };
   ```

4. 运行看效果。

## 额外配置

你可以在项目的 res 中添加 values 文件夹，并在其中建立一个资源 xml，在其中重写一些属性值，例如：

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="DialogXSnackBarStyleBottomMargin">10dp</dimen>
    <dimen name="DialogXSnackBarStyleShadow">5dp</dimen>
</resources>
```

DialogXSnackBarStyleBottomMargin 用于配置 SnackBar 距离屏幕底部的高度，注意，这个设置不包含非安全区（导航栏的高度）。

DialogXSnackBarStyleShadow 用于设置投影的厚度，请注意此设置不可以太大，不然导航栏会裁切阴影导致观感变差。

## 开源协议

DialogXStyle-Snackbar 遵循 Apache License 2.0 开源协议。

```
Copyright Kongzue DialogXStyle-Snackbar

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

 http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```