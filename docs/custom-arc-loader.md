---
layout: default
title: QCustomArcLoader
parent: Available Widgets
nav_order: 16
permalink: /docs/widgets/custom-arc-loader
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomArcLoader

## QCustomArcLoader

![QCustomArcLoader GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-arc-loader.gif)

### Overview
The `QCustomArcLoader` widget provides a customizable arc loader for PyQt/PySide applications. It allows users to create visually appealing arc loaders with options for customization such as color and pen width.

### Features
- **Customizable Appearance**: Users can customize the color and pen width of the arc loader.
- **Animation**: The arc loader supports animation for a smooth visual effect.
- **Direction Control**: Users can control the direction of the arc loader animation.

## Usage

### Importing
```python
from Custom_Widgets.QCustomLoadingIndicators import QCustomArcLoader
```

### Creating an Arc Loader
```python
arc_loader = QCustomArcLoader(
    parent=myParentWidget,
    color=QColor("#ffffff"),
    penWidth=20
)
arc_loader.show()
```
### Customization Options
- **Color**: Set the color of the arc loader.
- **Pen Width**: Specify the width of the pen used to draw the arc.

### Example
```python
import sys
from PySide6.QtCore import Qt
from PySide6.QtWidgets import QApplication, QMainWindow, QWidget, QVBoxLayout
from PySide6.QtGui import QColor
from Custom_Widgets.QCustomLoadingIndicators import QCustomArcLoader

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        # Create a loader widget with the main window as parent
        # self.loader = QCustomArcLoader(self)
        self.loader = QCustomArcLoader(color=QColor("#000"))

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