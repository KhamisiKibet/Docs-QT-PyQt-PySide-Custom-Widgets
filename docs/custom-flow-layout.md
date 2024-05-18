---
layout: default
title: QCustomFlowLayout
parent: Available Widgets
nav_order: 22
permalink: /docs/widgets/custom-flow-layout
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomFlowLayout

## QCustomFlowLayout

![Custom Embeded Window GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-flow-layout.gif)

### Overview
The `QCustomFlowLayout` widget is designed to provide a flexible flow layout for PyQt/PySide applications. This layout arranges child widgets in a flow, adjusting their positions dynamically as the parent widget is resized. It is particularly useful for creating responsive and adaptive interfaces.

### Features
- **Flexible Layout**: Automatically arranges child widgets in a flow, wrapping to the next line when necessary.
- **Customizable Margins and Spacing**: Allows customization of margins and spacing between widgets.
- **Positioning Widgets**: Widgets can be added at specific positions within the layout.
- **Alignment Options**: Align child widgets within their allocated space.

### Installation
Install the QT-PyQt-PySide-Custom-Widgets package using pip:

```cmd
pip install QT-PyQt-PySide-Custom-Widgets
```

### Importing
```python
from Custom_Widgets.QCustomFlowLayout import QCustomFlowLayout
```

### Creating a Flow Layout
```python
flowLayout = QCustomFlowLayout(parent=myParentWidget, margin=10, spacing=5)
```
### Customization Options
- **Parent**: The parent widget of the flow layout.
- **Margin**: The margin around the layout. Default is 0.
- **Spacing**: The spacing between widgets. Default is -1.

### Methods
- **addWidget**: Add a widget to the flow layout.

    - Parameters:
       -  `w` (QtWidgets.QWidget): The widget to be added.
       - `position` (int, optional): The position at which to insert the widget.
       - `align` (QtCore.Qt.AlignmentFlag, optional): The alignment of the widget within its allocated space.

- **addItem**: Add a layout item to the flow layout.

    - **Parameters**:
        - `a0` (QtWidgets.QLayoutItem): The layout item to be added.

- **count**: Get the number of items in the layout.

    - **Returns**: int

- **expandingDirections**: Get the directions in which the layout can expand.

    - **Returns**: QtCore.Qt.Orientations

- **itemAt**: Get the layout item at a specified index.

    - **Parameters**:
        - `index` (int): The index of the item.
    - **Returns**: QtWidgets.QLayoutItem

- **hasHeightForWidth**: Check if the layout has height-for-width support.

    - **Returns**: bool

- **heightForWidth**: Get the height for a given width.

    - **Parameters**:
        - `width` (int): The width to calculate height for.
    - **Returns**: int

- **minimumSize**: Get the minimum size of the layout.

    - **Returns**: QtCore.QSize

- **removeItem**: Remove a layout item from the flow layout.

    - **Parameters**:
        - `a0` (QtWidgets.QLayoutItem): The layout item to be removed.

- **removeWidget**: Remove a widget from the flow layout.

    - **Parameters**:
        - `w` (QtWidgets.QWidget): The widget to be removed.

- **setGeometry**: Set the geometry of the layout.

    - **Parameters**:
        - `rect` (QtCore.QRect): The geometry to set.

- **sizeHint**: Get the preferred size of the layout.

    - **Returns**: QtCore.QSize

- **takeAt**: Take the layout item at a specified index.

    - **Parameters**:
        - `index` (int): The index of the item to take.
    - **Returns**: QtWidgets.QLayoutItem

### Example
```python
import sys
from PySide6 import QtCore, QtWidgets
from Custom_Widgets.QCustomFlowLayout import QCustomFlowLayout

class MainWindow(QtWidgets.QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QCustomFlowLayout Example")
        self.central_widget = QtWidgets.QWidget()
        self.setCentralWidget(self.central_widget)
        self.flow_layout = QCustomFlowLayout(parent=self.central_widget, margin=10, spacing=5)

        # Create and add buttons to the flow layout
        for i in range(10):
            button = QtWidgets.QPushButton(f"Button {i+1}")
            self.flow_layout.addWidget(button)

        self.central_widget.setLayout(self.flow_layout)

if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    window = MainWindow()
    window.resize(400, 300)
    window.show()
    sys.exit(app.exec())
```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version 0.8.5 and above)
