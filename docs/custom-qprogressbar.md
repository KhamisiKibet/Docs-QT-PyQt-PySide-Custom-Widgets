---
layout: default
title: QCustomQProgressBar
parent: Available Widgets
nav_order: 18
permalink: /docs/widgets/custom-qprogressbar
---

# PyQt-Fluent-Widgets - Customizing QCustomQProgressBar

## QCustomQProgressBar

![QCustomArcLoader GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-qprogressbar.gif)

### Overview
The `QCustomQProgressBar` widget is an indeterminate progress bar designed to provide a modern and customizable progress indication for PyQt/PySide applications. It offers smooth animations and options for customizing the appearance and behavior of the progress bar.

### Features
- **Customizable Bar Color**: Users can set custom bar colors for both light and dark theme modes.
- **Smooth Animations**: Smooth animations for progress indication.
- **Start/Stop/Pause/Resume**: Control methods to start, stop, pause, and resume the progress animation.
- **Error Indication**: Option to indicate an error state with a different color.
- **Theming Support**: Automatic theming support based on the application's theme mode.

## Usage
### Importing
```python
from Custom_Widgets.QCustomLoadingIndicators import QCustomQProgressBar
```

### Creating a CustomQProgressBar
```python
progress_bar = QCustomQProgressBar(parent=myParentWidget, start=True)
```

### Customization Options
- **Custom Bar Color**: Set custom bar colors for light and dark theme modes using the setCustomBarColor method.
- **Start**: Start the progress animation using the start method.
- **Stop**: Stop the progress animation using the stop method.
- **Pause**: Pause the progress animation using the pause method.
- **Resume**: Resume the progress animation using the resume method.
- **Error Indication**: Set an error state using the setError method.

### Example
```python
# coding:utf-8
import sys

from PySide6.QtCore import Qt
from PySide6.QtWidgets import QApplication, QWidget, QVBoxLayout, QPushButton
from Custom_Widgets.QCustomLoadingIndicators import QCustomQProgressBar


class Demo(QWidget):

    def __init__(self):
        super().__init__()
        self.vBoxLayout = QVBoxLayout(self)
    
        self.inProgressBar = QCustomQProgressBar(self)
        self.button = QPushButton("Pause")

        self.vBoxLayout.addWidget(self.inProgressBar)
        self.vBoxLayout.addWidget(self.button, 0, Qt.AlignHCenter)
        self.vBoxLayout.setContentsMargins(30, 30, 30, 30)
        self.resize(400, 400)

        self.button.clicked.connect(self.onButtonClicked)

    def onButtonClicked(self):
        if self.inProgressBar.isStarted():
            self.inProgressBar.pause()
            self.button.setText('Play')
        else:
            self.inProgressBar.resume()
            self.button.setText("Pause")


if __name__ == '__main__':
    app = QApplication(sys.argv)
    w = Demo()
    w.show()
    app.exec()
```

## Dependencies
- PyQt or PySide
- Custom_Widgets module