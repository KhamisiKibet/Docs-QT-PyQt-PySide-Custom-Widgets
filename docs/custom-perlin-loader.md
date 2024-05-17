---
layout: default
title: QCustomPerlinLoader
parent: Available Widgets
nav_order: 17
permalink: /docs/widgets/custom-perlin-loader
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomPerlinLoader

## QCustomPerlinLoader

![QCustomArcLoader GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-perlin-loader.gif)

### Overview
The `QCustomPerlinLoader` widget provides a customizable loading animation based on Perlin noise for PyQt/PySide applications. It offers a visually appealing way to indicate loading progress to users, with options for customization such as size, message, colors, font, duration, and Perlin noise parameters.

### Features
- **Customizable Appearance**: Customize the size, message, colors, font, and background of the loading animation.
- **Dynamic Animation**: The loading animation dynamically changes based on Perlin noise, creating an organic and fluid motion.
- **Duration Control**: Adjust the duration of the loading animation to suit the application's needs.
- **Perlin Noise Parameters**: Fine-tune the Perlin noise parameters such as octaves and seed for different visual effects.
- **Message Display**: Display a custom message alongside the loading animation to provide context to users.

## Usage
### Importing
```python
from Custom_Widgets.QCustomLoadingIndicators import QCustomPerlinLoader
```

### Creating a Custom Perlin Loader
```python
loader = QCustomPerlinLoader(
    parent=myParentWidget,
    size=QSize(600, 600),
    message="LOADING...",
    color=QColor("white"),
    fontFamily="Ebrima",
    fontSize=30,
    rayon=200,
    duration=60 * 1000,
    noiseOctaves=0.8,
    noiseSeed=int(time.time()),
    backgroundColor=QColor("transparent"),
    circleColor1=QColor("#ff2e63"),
    circleColor2=QColor("#082e63"),
    circleColor3=QColor(57, 115, 171, 100)
)
```

### Customization Options
- **Parent**: Specify the parent widget of the loading animation.
- **Size**: Set the size of the loading animation.
- **Message**: Display a custom message alongside the loading animation.
- **Color**: Set the color of the custom message.
- **Font Family**: Specify the font family of the custom message.
- **Font Size**: Set the font size of the custom message.
- **Rayon**: Set the radius of the loading animation circles.
- **Duration**: Adjust the duration of the loading animation in milliseconds.
- **Noise Octaves**: Set the number of octaves for Perlin noise.
- **Noise Seed**: Set the seed for Perlin noise generation.
- **Background Color**: Set the background color of the loading animation.
- **Circle Colors**: Set the colors of the concentric circles in the loading animation.

### Example
```python
import sys
import time
from PySide6.QtGui import QColor
from PySide6.QtCore import QSize, Qt
from PySide6.QtWidgets import QApplication, QMainWindow, QWidget, QVBoxLayout
from PySide6.QtGui import QColor
from Custom_Widgets.QCustomLoadingIndicators import QCustomPerlinLoader

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        # Create a loader widget with the main window as parent
        self.loader = QCustomPerlinLoader()

        # self.loader = QCustomPerlinLoader(
        #     parent=self,
        #     size=QSize(400, 400),
        #     message="LOADING...",
        #     color=QColor("white"),
        #     fontFamily="Ebrima",
        #     fontSize=30,
        #     rayon=200,
        #     duration=60 * 1000,
        #     noiseOctaves=0.8,
        #     noiseSeed=int(time.time()),
        #     backgroundColor=QColor("transparent"),
        #     circleColor1=QColor("#ff2e63"),
        #     circleColor2=QColor("#082e63"),
        #     circleColor3=QColor(57, 115, 171, 100)
        # )

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
- Custom_Widgets
