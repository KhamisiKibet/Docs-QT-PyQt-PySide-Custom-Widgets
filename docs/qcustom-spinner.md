---
layout: default
title: QCustomSpinner
parent: Available Widgets
nav_order: 19
permalink: /docs/widgets/custom-spinner
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomSpinner

## QCustomSpinner

![Custom Embeded Window GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-spinner.gif)

### Overview
The `QCustomSpinner` widget provides a customizable spinner for PyQt/PySide applications. It offers a visually appealing way to indicate that a process is ongoing. Users can customize various aspects of the spinner, including line width, line color, direction of rotation, border radius, and animation type.

### Features
- **Customizable Appearance**: Users can customize the line width and color of the spinner.
- **Direction of Rotation**: Choose between clockwise and counterclockwise rotation.
- **Border Radius**: Adjust the border radius to control the curvature of the spinner.
- **Animation Type**: Select between smooth and bounce animations for the spinner.

## Usage
```python
from Custom_Widgets.QCustomLoadingIndicators import QCustomSpinner

spinner = QCustomSpinner(
    lineWidth=2,
    lineColor=None,  # Use default color if None
    direction="Clockwise",  # or "Counterclockwise"
    animationType="Bounce"  # or "Smooth"
)
spinner.show()
```

### Customization Options
- **Line Width**: Set the width of the spinner's lines.
- **Line Color**: Specify the color of the spinner's lines. If not provided, the default highlight color is used.
- **Direction**: Choose the direction of rotation for the spinner, either clockwise or counterclockwise.
- **Animation Type**: Select between smooth and bounce animations for the spinner.

### Example
```python
# coding:utf-8
import sys

from PySide6.QtCore import Qt
from PySide6.QtWidgets import QApplication, QWidget, QHBoxLayout, QVBoxLayout, QPushButton
from Custom_Widgets.QCustomLoadingIndicators import QCustomSpinner


class Demo(QWidget):

    def __init__(self):
        super().__init__()

        self.vBoxLayout = QVBoxLayout(self)
        self.hBoxLayout = QHBoxLayout()

        self.spinner = QCustomSpinner(lineWidth=10, lineColor="#FF0000", animationType="Bounce")
        self.spinner2 = QCustomSpinner(lineColor="#000", animationType="Smooth")
        self.spinner.setMinimumSize(100, 100)
        self.spinner.setMaximumSize(100, 100)
        self.spinner2.setMinimumSize(100, 100)
        self.spinner2.setMaximumSize(100, 100)

        self.vBoxLayout.setContentsMargins(30, 30, 30, 30)
        self.vBoxLayout.addLayout(self.hBoxLayout)
        self.vBoxLayout.addWidget(self.spinner, 0, Qt.AlignHCenter)
        self.vBoxLayout.addWidget(self.spinner2, 0, Qt.AlignHCenter)
        self.resize(400, 400)


if __name__ == '__main__':
    app = QApplication(sys.argv)
    w = Demo()
    w.show()
    app.exec()
```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets
