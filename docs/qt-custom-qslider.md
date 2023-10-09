---
layout: default
title: Custom QSlider
parent: Available Widgets
nav_order: 8
permalink: /docs/widgets/custom-qslider
---

# QT-PyQt-PySide-Custom-Widgets 

## Install the custom widgets
```
pip install QT-PyQt-PySide-Custom-Widgets

```

![Qt Custom slider](https://github.com/KhamisiKibet/QT-PyQt-PySide-Custom-Widgets/blob/main/images/Qt-Custom-slider.png?raw=true)

## Qt Custom QSlider

This function allows you to move the `QSlider` to the current click position.

Steps:

- Add  `QSlider` to the UI using Qt Designer
- Right click on the `QSlider` widget, select `Promoted widgets...`
- Under "Base class name" select `QSlider`
	- Under "Promote class name" enter `QCustomQSlider`
	- Under "Header file" enter `Custom_Widgets.QCustomQSlider.h`

- Then click on `promote`.

![QT Designer App](https://github.com/KhamisiKibet/QT-PyQt-PySide-Custom-Widgets/blob/main/images/Screenshot_20230924_030911.png?raw=true)

- Generate your UI python code.
- DONE!
