---
layout: default
title: QCustomQToolTip
parent: Available Widgets
nav_order: 12
permalink: /docs/widgets/custom-qtooltip
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomQToolTip

## QCustomQToolTip

![Custom QToolTip GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-qtooltip.gif)

### Overview
The QCustomQToolTip widget provides a customizable tooltip overlay for PyQt/PySide applications. It allows developers to create tooltip overlays with custom text, icons, duration, and tail positions.

### Features
- **Customizable Text**: Users can set custom text content for the tooltip overlay.
- **Custom Icons**: Support for displaying custom icons alongside the tooltip content.
- **Duration Control**: Developers can specify the duration for which the tooltip remains visible before automatically closing.
- **Tail Positioning**: Offers various tail positions for the tooltip overlay, allowing it to adapt to different target widget positions.

## Usage

### Importing
```python
from Custom_Widgets.QCustomQToolTip import QCustomQToolTip
```

### Creating a Tooltip Overlay
```python
tooltip = QCustomQToolTip(
    text="Tooltip text",
    parent=myParentWidget,
    target=myWidget,
    duration=1500,
    icon="icon.png",
    tailPosition="auto"
)
```
**Check the full example below which will install the custom tooltip across your `QApplication`.**

### Customization Options
- **Text**: Set the text content of the tooltip overlay.
- **Icon**: Specify an icon to be displayed alongside the tooltip content.
- **Duration**: Set the duration for which the tooltip remains visible before automatically closing.
- **Tail Position**: Choose from various tail positions for the tooltip overlay.

### Tooltip Positioning
The QCustomQToolTip widget provides flexibility in positioning the tooltip overlay relative to a target widget or a specific point on the screen. Here's an explanation of the available tail positions:

- **Top-Left (top-left)**: Positions the tooltip overlay at the top-left corner of the target widget.
- **Top-Center (top-center)**: Positions the tooltip overlay at the top-center of the target widget.
- **Top-Right (top-right)**: Positions the tooltip overlay at the top-right corner of the target widget.
- **Bottom-Left (bottom-left)**: Positions the tooltip overlay at the bottom-left corner of the target widget.
- **Bottom-Center (bottom-center)**: Positions the tooltip overlay at the bottom-center of the target widget.
- **Bottom-Right (bottom-right)**: Positions the tooltip overlay at the bottom-right corner of the target widget.
- **Left-Center (left-center)**: Positions the tooltip overlay at the left-center of the target widget.
- **Right-Center (right-center)**: Positions the tooltip overlay at the right-center of the target widget.
- **Auto (auto)**: Automatically determines the best position based on available space around the target widget.

*By specifying one of these tail positions when creating a QCustomQToolTip widget, developers can control where the tooltip appears relative to the target widget, ensuring a tailored user experience.*

## Example
Auto positioned tooltip:

```python
import sys
from PySide6.QtCore import Qt
from PySide6.QtGui import QColor
from PySide6.QtWidgets import QApplication, QMainWindow, QVBoxLayout, QHBoxLayout, QPushButton, QWidget, QGraphicsDropShadowEffect
from Custom_Widgets.QCustomQToolTip import QCustomQToolTipFilter

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QCustomQToolTip Tail Position Test")
        self.central_widget = QWidget()
        self.setCentralWidget(self.central_widget)
        self.layout = QVBoxLayout(self.central_widget)

        self.setStyleSheet("""
            QMainWindow, * {
                background-color: #f0f0f0;
            }
            QCustomQToolTip *{
                color: #000
            }
            QPushButton {
                background-color: #4CAF50;
                color: white;
                padding: 8px 16px;
                border: none;
                border-radius: 4px;
            }
            QPushButton:hover {
                background-color: #45a049;
            }
            QPushButton:pressed {
                background-color: #3e8e41;
            }
        """)

        button = QPushButton("HOVER: Auto-positioned Tool-Tip")
        self.layout.addWidget(button)
        self.addShadow(button)
        button.setToolTip("Testing Auto-positioned Tool-Tip.  Try resizing the window then hover again!")

        widget = QWidget()
        widgetLayout = QHBoxLayout()

        button = QPushButton("HOVER: Auto-positioned Tool-Tip")
        self.layout.addWidget(button)
        self.addShadow(button)
        button.setToolTip("Testing Auto-positioned Tool-Tip.  Try resizing the window then hover again!")

        widgetLayout.addWidget(button)

        button = QPushButton("HOVER: Auto-positioned Tool-Tip")
        self.layout.addWidget(button)
        self.addShadow(button)
        button.setToolTip("Testing Auto-positioned Tool-Tip.  Try resizing the window then hover again!")
        
        widgetLayout.addWidget(button)

        widget.setLayout(widgetLayout)
        self.layout.addWidget(widget)
        
        button = QPushButton("HOVER: Auto-positioned Tool-Tip")
        self.layout.addWidget(button)
        self.addShadow(button)
        button.setToolTip("Testing Auto-positioned Tool-Tip.  Try resizing the window then hover again!")


    def addShadow(self, widget):
        effect = QGraphicsDropShadowEffect(widget)
        effect.setColor(QColor(30, 30, 30, 200))
        effect.setBlurRadius(20)
        effect.setXOffset(0)
        effect.setYOffset(0)
        widget.setGraphicsEffect(effect)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    # Install the QCustomQToolTipFilter event to your app in order to use the custom tooltip
    app_tooltip_filter = QCustomQToolTipFilter(tailPosition="auto")
    app.installEventFilter(app_tooltip_filter)
    window = MainWindow()
    window.resize(500, 300)
    window.show()
    sys.exit(app.exec())
```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version 0.8.5 and above)