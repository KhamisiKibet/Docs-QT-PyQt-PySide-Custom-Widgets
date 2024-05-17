---
layout: default
title: QCustom3CirclesLoader
parent: Loading Indicators/Progress Bars
nav_order: 1
permalink: /docs/widgets/custom-3-circles-loader
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustom3CirclesLoader

## QCustom3CirclesLoader

![Custom Embeded Window GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-3-circles-loader.gif)

### Overview
The `QCustom3CirclesLoader` widget is designed to create a custom loader with three animated circles for PyQt/PySide applications. It provides a visually appealing loading animation that can be customized in terms of color, pen width, and animation duration.

### Features
- **Customizable Appearance**: Users can customize the color and pen width of the circles in the loader animation.
- **Animation Duration**: Control the duration of the animation for a smoother or faster loading effect.

## Usage

### Importing
```python
from Custom_Widgets.QCustom3CirclesLoader import QCustom3CirclesLoader
```
### Creating a Custom 3 Circles Loader
```python
loader = QCustom3CirclesLoader(
    parent=myParentWidget,
    color=QColor("#333333"),
    penWidth=20,
    animationDuration=400
)
loader.show()
```
### Customization Options
- **Parent**: Specify the parent widget of the loader.
- **Color**: Set the color of the circles in the loader animation.
- **Pen Width**: Define the width of the pen used to draw the circles.
- **Animation Duration**: Control the duration of the animation in milliseconds.

### Example
```python
import sys
from PySide6.QtCore import Qt
from PySide6.QtWidgets import QApplication, QMainWindow, QWidget, QVBoxLayout
from PySide6.QtGui import QColor
from Custom_Widgets.QCustomLoadingIndicators import QCustom3CirclesLoader

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        # Create a loader widget with the main window as parent
        # self.loader = QCustom3CirclesLoader(self)
        self.loader = QCustom3CirclesLoader(color=QColor("#000"))

        self.centralwidget = QWidget(self)
        self.layout = QVBoxLayout(self.centralwidget)

        self.layout.addWidget(self.loader)
        self.layout.setAlignment(self.loader, Qt.AlignCenter)  # Align loader widget to the center of the layout

        self.setCentralWidget(self.centralwidget)
        self.resize(800, 450)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    
    # Create an instance of MainWindow
    main_window = MainWindow()
    main_window.show()
    
    sys.exit(app.exec())
```
## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version 0.8.5 and above)