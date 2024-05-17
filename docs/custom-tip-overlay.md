---
layout: default
title: QCustomTipOverlay
parent: Available Widgets
nav_order: 10
permalink: /docs/widgets/custom-tip-overlay
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomTipOverlay


## QCustomTipOverlay

![Custom Tool Tip Overlay GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-tool-tip-overlay.gif)

### Overview
The QCustomTipOverlay widget is designed to provide customizable tooltip overlays for PyQt/PySide applications. It offers a convenient way to display informative messages or notifications to users, with options for customization such as title, description, icon, image, closability, and a close icon.

### Features
- **Customizable Appearance**: Users can customize the appearance of the tooltip overlay including title, description, icon, and image.
- **Closable Option**: The tooltip overlay can be configured to be closable, allowing users to dismiss it manually.
- **Close Icon**: Users can now provide a custom close icon for the tooltip overlay.
- **Animation Types**: Supports various animation types for showing and hiding the tooltip overlay.
- **Positioning**: Offers flexibility in positioning the tooltip overlay relative to a target widget or a specific point on the screen.
- **Automatic Close**: Provides an option to automatically close the tooltip overlay after a specified duration.

## Usage
## Installation
Install the QT-PyQt-PySide-Custom-Widgets package using pip:

```cmd
pip install QT-PyQt-PySide-Custom-Widgets
```

### Importing
```python
from Custom_Widgets.QCustomTipOverlay import QCustomTipOverlay
```

### Creating a Tooltip Overlay
```python
tooltip = QCustomTipOverlay(
    title="Title",
    description="Description",
    icon="icon.png",
    image="image.png",
    isClosable=True,
    target=myWidget,
    parent=myParentWidget,
    aniType="pull-up",
    isDeleteOnClose=True,
    duration=5000,
    tailPosition="bottom-center",
    showForm=myForm,
    addWidget=myCustomWidget,
    closeIcon="close_icon.png" # Add a close icon
)
tooltip.show()

```

### Customization Options
- **Title**: Set the title of the tooltip overlay.
- **Description**: Provide a description text for the tooltip overlay.
- **Icon**: Specify an icon to be displayed alongside the tooltip.
-  **Close Icon**: Specify an icon to be displayed alongside the close button.
- **Image**: Add an image to the tooltip overlay.
- **Closable**: Enable or disable the close button on the tooltip overlay.
- **Target**: Set the target widget to which the tooltip is associated.
- **Parent**: Specify the parent widget of the tooltip overlay.
- **Animation Type**: Choose from various animation types for showing and hiding the tooltip.
- **Delete On Close**: Decide whether the tooltip widget should be deleted upon closing.
- **Duration**: Set the duration for which the tooltip remains visible before automatically closing.
- **Tail Position**: Position the tooltip tail at different locations around the tooltip.
- **Show Form**: Display a custom form within the tooltip overlay.
- **Add Widget**: Add a custom widget to the tooltip overlay.

### Tooltip Positioning
The `QCustomTipOverlay` widget provides flexibility in positioning the tooltip overlay relative to a target widget or a specific point on the screen. Here's an explanation of all available positions:

- **Automatic (auto)**: The tooltip position will be determined automatically by the program.

- **Top-Left (top-left)**: This position places the tooltip overlay at the top-left corner of the target widget or screen point. The tooltip tail extends from the top-left corner of the tooltip, pointing downwards.

- **Top-Center (top-center)**: The tooltip overlay is positioned at the top-center of the target widget or screen point. The tooltip tail extends from the top-center of the tooltip, pointing downwards.

- **Top-Right (top-right)**: This position aligns the tooltip overlay with the top-right corner of the target widget or screen point. The tooltip tail extends from the top-right corner of the tooltip, pointing downwards.

- **Center-Left (center-left)**: The tooltip overlay is centered vertically and aligned to the left side of the target widget or screen point. The tooltip tail extends from the left side of the tooltip, pointing towards the right.

- **Center-Right (center-right)**: This position centers the tooltip vertically and aligns it to the right side of the target widget or screen point. The tooltip tail extends from the right side of the tooltip, pointing towards the left.

- **Bottom-Left (bottom-left)**: The tooltip overlay is positioned at the bottom-left corner of the target widget or screen point. The tooltip tail extends from the bottom-left corner of the tooltip, pointing upwards.

- **Bottom-Center (bottom-center)**: This position places the tooltip overlay at the bottom-center of the target widget or screen point. The tooltip tail extends from the bottom-center of the tooltip, pointing upwards.

- **Bottom-Right (bottom-right)**: The tooltip overlay is aligned with the bottom-right corner of the target widget or screen point. The tooltip tail extends from the bottom-right corner of the tooltip, pointing upwards.

- **Left-Top (left-top)**: This position aligns the tooltip overlay to the top-left corner of the target widget or screen point. The tooltip tail extends from the top-left corner of the tooltip, pointing towards the right.

- **Left-Bottom (left-bottom)**: The tooltip overlay is aligned with the bottom-left corner of the target widget or screen point. The tooltip tail extends from the bottom-left corner of the tooltip, pointing towards the right.

- **Right-Top (right-top)**: This position aligns the tooltip overlay to the top-right corner of the target widget or screen point. The tooltip tail extends from the top-right corner of the tooltip, pointing towards the left.

- **Right-Bottom (right-bottom)**: The tooltip overlay is aligned with the bottom-right corner of the target widget or screen point. The tooltip tail extends from the bottom-right corner of the tooltip, pointing towards the left.

By specifying one of these positions when creating a QCustomTipOverlay widget, users can control where the tooltip appears relative to the target widget or screen point, providing a tailored user experience.

## Example
```python
import sys
from PySide6.QtCore import Qt
from PySide6.QtGui import QColor
from PySide6.QtWidgets import QApplication, QMainWindow, QHBoxLayout, QPushButton, QWidget, QGraphicsDropShadowEffect
from Custom_Widgets.QCustomTipOverlay import QCustomTipOverlay

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QCustomTipOverlay Tail Position Test")
        self.central_widget = QWidget()
        self.setCentralWidget(self.central_widget)
        self.layout = QHBoxLayout(self.central_widget)

        # Create buttons to test different tail positions
        self.create_button("Auto", "auto")
        self.create_button("Top-Left", "top-left")
        self.create_button("Top-Center", "top-center")
        self.create_button("Top-Right", "top-right")
        self.create_button("Bottom-Left", "bottom-left")
        self.create_button("Bottom-Center", "bottom-center")
        self.create_button("Bottom-Right", "bottom-right")
        self.create_button("Auto", "auto")
        self.create_button("Left-Top", "left-top")
        self.create_button("Left-Bottom", "left-bottom")
        self.create_button("Right-Top", "right-top")
        self.create_button("Right-Bottom", "right-bottom")
        self.create_button("Left-Center", "left-center")
        self.create_button("Right-Center", "right-center")
        self.create_button("Auto", "auto")

        self.setStyleSheet("""
            QMainWindow, * {
                background-color: #f0f0f0;
            }
            QCustomTipOverlay *{
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

    def create_button(self, text, tail_position):
        button = QPushButton(text)
        button.clicked.connect(lambda: self.show_tip(button, tail_position))
        self.layout.addWidget(button)
        self.addShadow(button)

    def show_tip(self, button, tail_position):
        tip = QCustomTipOverlay(
            target=button,
            title='Test Tip',
            description="This is a test tip",
            isClosable=True,
            tailPosition=tail_position,
            parent=self,
            duration=-1
        )

        self.addShadow(tip)

        tip.show()
    
    def addShadow(self, widget):
        effect = QGraphicsDropShadowEffect(widget)
        effect.setColor(QColor(0, 0, 0, 180))
        effect.setBlurRadius(10)
        effect.setXOffset(0)
        effect.setYOffset(0)
        widget.setGraphicsEffect(effect)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MainWindow()
    window.resize(500, 300)
    window.show()
    sys.exit(app.exec())

```


## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version `0.8.5 and above`)