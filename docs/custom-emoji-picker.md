---
layout: default
title: QCustomEmojiPicker
parent: Available Widgets
nav_order: 20
permalink: /docs/widgets/custom-emoji-picker
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomEmojiPicker

## QCustomEmojiPicker

![Custom Emoji Picker](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-emoji-picker.gif)

### Overview
The `QCustomEmojiPicker` widget is a specialized emoji picker built on top of `QCustomTipOverlay`. It allows users to select emojis through a visually appealing interface and supports customization options such as items per row, performance search, and more.

### Features
- **Customizable Appearance**: Inherits customization options from `QCustomTipOverlay` and adds its own for emoji selection.
- **Closable Option**: The emoji picker can be configured to be closable, allowing users to dismiss it manually.
- **Positioning**: Offers flexibility in positioning the emoji picker relative to a target widget.
- **Automatic Close**: The emoji picker remains open until the user makes a selection or manually closes it.
- **Performance Search**: Optimizes search performance by filtering emoji names based on the input text.

### Installation
Install the QT-PyQt-PySide-Custom-Widgets package using pip:

```cmd
pip install QT-PyQt-PySide-Custom-Widgets
```

### Importing
```python
from Custom_Widgets.QCustomEmojiPicker import QCustomEmojiPicker
```

### Creating an Emoji Picker
```python
emoji_picker = QCustomEmojiPicker(
    parent=myParentWidget,
    target=myTargetWidget,
    tailPosition="top-center",
    itemsPerRow=8,
    performanceSearch=True
)
emoji_picker.show()
```

### Customization Options
- **Parent**: Specify the parent widget of the emoji picker.
- **Target**: Set the target widget to which the emoji picker is associated.
- **Tail** Position: Position the tooltip tail at different locations around the tooltip.
- **Items Per Row**: Set the number of emoji items per row in the picker.
- **Performance Search**: Enable or disable performance-optimized search.

### Example
```python
from PySide6.QtWidgets import QApplication, QMainWindow, QWidget, QVBoxLayout, QHBoxLayout, QLineEdit, QTextEdit, QPushButton, QGraphicsDropShadowEffect
from PySide6.QtGui import QColor
from Custom_Widgets.QCustomEmojiPicker import QCustomEmojiPicker
import sys

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setWindowTitle("Emoji Picker Test")
        self.setGeometry(100, 100, 600, 400)

        central_widget = QWidget()
        self.setCentralWidget(central_widget)
        layout = QVBoxLayout()
        central_widget.setLayout(layout)

        # Create a container widget for the edit widgets and buttons
        container_widget = QWidget()
        container_layout = QHBoxLayout()
        container_widget.setLayout(container_layout)
        layout.addWidget(container_widget)

        # Create a QLineEdit widget
        line_edit = QLineEdit()
        container_layout.addWidget(line_edit)

        # Create a QPushButton for emoji picker for QLineEdit
        line_edit_btn = QPushButton("😀")
        line_edit_btn.clicked.connect(lambda: self.showEmojiPicker(line_edit))
        container_layout.addWidget(line_edit_btn)

        # Create a QTextEdit widget
        text_edit = QTextEdit()
        container_layout.addWidget(text_edit)

        # Create a QPushButton for emoji picker for QTextEdit
        text_edit_btn = QPushButton("😀")
        text_edit_btn.clicked.connect(lambda: self.showEmojiPicker(text_edit))
        container_layout.addWidget(text_edit_btn)

        self.show()

    def showEmojiPicker(self, target_widget):
        emoji_picker = QCustomEmojiPicker(target=target_widget, parent=self, itemsPerRow=16)
        emoji_picker.show()

        # Add shadow effect
        effect = emoji_picker.graphicsEffect()
        if effect is None:
            effect = QGraphicsDropShadowEffect(emoji_picker)
        effect.setColor(QColor(30, 30, 30, 200))
        effect.setBlurRadius(20)
        effect.setXOffset(0)
        effect.setYOffset(0)
        emoji_picker.setGraphicsEffect(effect)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MainWindow()
    sys.exit(app.exec_())
```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version 0.8.5 and above)