---
layout: default
title: QCustomCodeEditor
parent: Available Widgets
nav_order: 21
permalink: /docs/widgets/custom-code-editor
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomCodeEditor

## QCustomCodeEditor

![Custom Embeded Window GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-code-editor.gif)

### Overview
The QCustomCodeEditor widget provides a customizable code editor for PyQt/PySide applications. It supports syntax highlighting for various programming languages and offers features such as line numbering, cursor position display, and theme customization.

### Features
- **Syntax Highlighting**: Supports syntax highlighting for Python, C++, and plain text files.
- **Theme Customization**: Users can customize the appearance of the code editor by selecting different themes.
- **Line Numbering**: Displays line numbers alongside the code for easy navigation.
- **Cursor Position Display**: Shows the current cursor position in the code.
- **File Loading**: Allows loading code from files with automatic language detection based on file extension.

## Usage
### Importing
```python
from Custom_Widgets.QCustomCodeEditor import QCustomCodeEditor
```

### Creating a Code Editor
```python
code_editor = QCustomCodeEditor()
```

### Setting Theme
```python
code_editor.setTheme("default")
```

### Setting Language
```python
code_editor.setLang("python")
```
### Loading File
```python
code_editor.loadFile("path/to/file.py")
```

### Customization Options
- **Theme**: Set the theme of the code editor.
- **Language**: Set the language mode of the code editor (e.g., Python, C++, plain text).
- **File Loading**: Load code from files with automatic language detection.

### Example
```python
import sys
import os
from functools import partial
from PySide6.QtCore import Qt
from PySide6.QtWidgets import QApplication, QMainWindow, QToolBar, QPushButton, QVBoxLayout, QWidget, QLabel
from Custom_Widgets.QCustomCodeEditor import QCustomCodeEditor

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()

        # Main container widget
        self.container = QWidget()
        self.layout = QVBoxLayout()
        self.container.setLayout(self.layout)
        self.setCentralWidget(self.container)

        # First editor
        self.editor1_label = QLabel("Primary Code Editor")
        self.editor1 = QCustomCodeEditor()
        self.editor1.setTheme("default")  # Set default theme
        self.editor1.setLang("python")

        # Second editor
        self.editor2_label = QLabel("Embedded Code Editor")
        self.editor2 = QCustomCodeEditor()
        self.editor2.setTheme("default")  # Set default theme
        self.editor2.loadFile(os.path.join(os.path.dirname(__file__), "hello.cpp"))

        # Add widgets to layout
        self.layout.addWidget(self.editor1_label)
        self.layout.addWidget(self.editor1)
        self.layout.addWidget(self.editor2_label)
        self.layout.addWidget(self.editor2)

        self.create_toolbar()

    def create_toolbar(self):
        toolbar = QToolBar("Themes", self)
        self.addToolBar(Qt.TopToolBarArea, toolbar)

        themes = ["Default", "One Light", "One Dark", "Monokai", "Oceanic", "Zenburn"]
        for theme in themes:
            button = QPushButton(theme, self)
            button.clicked.connect(partial(self.set_theme, theme.lower().replace(" ", "-")))
            toolbar.addWidget(button)

    def set_theme(self, theme):
        self.editor1.setTheme(theme)
        self.editor2.setTheme(theme)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())
```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets
