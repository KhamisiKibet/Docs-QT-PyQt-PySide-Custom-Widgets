---
layout: default
title: QCustomEmbededWindow
parent: Available Widgets
nav_order: 11
permalink: /docs/widgets/custom-embeded-window
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomEmbededWindow

## QCustomEmbededWindow

### Overview
The `QCustomEmbededWindow` widget provides a versatile embedded window functionality for PyQt/PySide applications. It allows developers to create customizable embedded windows with headers, content areas, and interactive controls.

### Features

1. **Title**: Set the title of the embedded window.
2. **Icon**: Specify an icon to be displayed in the header area.
3. **Border Radius**: Customize the border radius of the embedded window through CSS style.
4. **Header Height**: Set the height of the header area.
5. **Animation Duration**: Set the duration of animations when showing/hiding the content area.
6. **Position**: Specify the initial position of the embedded window.
7. **Content Widgets**: Add widgets to the content area of the embedded window.
8. **Closable**: Enable or disable the close button for the embedded window.
9. **Show/Hide Button**: Customize the appearance of the button to show/hide the content area.
10. **Custom Styling**: Apply custom CSS styles to the embedded window, header, close button, and content area.

## Usage

### Installation
To use the `QCustomEmbededWindow` widget, ensure that you have PyQt or PySide installed.

### Importing
```python
from Custom_Widgets.QCustomEmbededWindow import QCustomEmbededWindow

```

### Creating an Embedded Window
```python
# my_icon is a QIcon object
embedded_window = QCustomEmbededWindow(parent_widget, title="My Embedded Window", icon=my_icon)
embedded_window.show()
```

Example

```python 
embedded_window = QCustomEmbededWindow(
    parent_widget,
    title="My Embedded Window",
    icon=my_icon,
    headerHeight=30,
    animationDuration=500,
    showForm=myForm, #display a UI form i.e importing the form before displaing (from ui_form import myForm),
    # to access the widgets inside the form (embedded_window.shownForm.widgetName)
    addWidget=myCustomWidget #add a widget container
    pos=(100, 100)
)
embedded_window.show()

# add another widget
label = QLabel("Content goes here")
embedded_window.addWidget(label)

```

### Styling
`QCustomEmbededWindow` can be styled using CSS. Below are some example styles for customizing various components:

```css
/* Header styles */
QCustomEmbededWindow > #header {
    background-color: #2c3e5022;
    padding: 10px;
}

/* Close button styles */
QCustomEmbededWindow >  #header QPushButton#close-button {
    background-color: transparent;
    border: none;
    margin-right: 5px;
}

/* Show/Hide button styles */
QCustomEmbededWindow >  #header QPushButton#hide-button {
    background-color: transparent;
    border: none;
    margin-right: 5px;
}

/* Content area styles */
QCustomEmbededWindow >  #content-area {
    background-color: #ecf0f1;
    padding: 10px;
}
```

## Full example
```python
import sys
from PySide6.QtWidgets import QApplication, QMainWindow, QLabel, QPushButton, QWidget, QVBoxLayout
from PySide6.QtGui import QIcon
from PySide6.QtCore import Qt
from Custom_Widgets.QCustomEmbededWindow import QCustomEmbededWindow

class MainWindow(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Main Window")
        self.setGeometry(100, 100, 400, 300)

        layout = QVBoxLayout(self)
        self.button = QPushButton("Create Embedded Window")
        self.button.clicked.connect(self.create_embedded_window)
        layout.addWidget(self.button)
        layout.setAlignment(Qt.AlignCenter)

    def create_embedded_window(self):
        label = QLabel("Content goes here")
        embedded_window = QCustomEmbededWindow(
            self,
            title="Embedded Window",
            icon=QIcon("icon.png"),  # Set your icon path here
            borderRadius=10,
            headerHeight=30,
            animationDuration=500,
            pos=(100, 100)
        )
        embedded_window.addWidget(label)
        embedded_window.show()

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())
```

## Dependencies
- PyQt or PySide
- Custom_Widgets package