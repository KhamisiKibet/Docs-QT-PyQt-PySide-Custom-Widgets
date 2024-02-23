---
layout: default
title: QDraggableWidget
parent: Available Widgets
nav_order: 10
permalink: /docs/widgets/qdragable-widgets
---

# QT-PyQt-PySide-Custom-Widgets - QDraggableWidget

## Support Development
If you find these custom widgets helpful and would like to support their development, consider becoming a patron on our Patreon page:

[Support us on Patreon](https://www.patreon.com/spinntv)

Your support helps us maintain and improve these custom widgets for the community.

## QDraggableWidget
The QDraggableWidget module provides custom draggable widget functionality for PyQt applications. It includes two main classes: QDragItem and QDragWidget.

Installation
You can install the QT-PyQt-PySide-Custom-Widgets package via pip:

```cmd
pip install QT-PyQt-PySide-Custom-Widgets
```
### Usage
Creating Widgets
To create QDragItem and QDragWidget widgets directly from your Python script, follow these steps:

1. Import the required classes:
```python
from Custom_Widgets.QDraggableWidget import QDragItem, QDragWidget
```

2. Add Drag-and-Drop Functionality:
Inside your Python script, import the QDragItem class from the QDraggableWidget module. You can then create instances of QDragItem and add them to the promoted QDragWidget in your application.

#### Example Usage:
```python
# import qtpy,pyside or pyqt
from qtpy.QtWidgets import QApplication, QVBoxLayout
from Custom_Widgets.QDraggableWidget import QDragItem, QDragWidget

app = QApplication([])

# Create a draggable item
drag_item = QDragItem()
drag_item.setText("Drag me")

# Create a promoted QDragWidget from Qt Designer
drag_widget = QDragWidget()

# Add the draggable item to the drag widget
drag_widgetLayout = QVBoxLayout(drag_widget)
drag_widgetLayout.addWidget(drag_item)

# Show the drag widget
drag_widget.show()

app.exec_()

```

Using Qt Designer
- Alternatively, you can create and use these widgets in Qt Designer by promoting existing widgets.

- To make a widget draggable using Qt Designer by promoting a placeholder widget to QDragItem, follow these steps:

1. Open Qt Designer:
    - Launch Qt Designer to design your user interface.

2. Design Your User Interface:
    - Design your user interface as needed, including the placeholder widget that will contain the draggable widgets.

3. Promote a Placeholder Widget to QDragWidget:

    - Right-click on the placeholder widget that will act as the parent container for draggable widgets.
    - Select "Promote to..." from the context menu.
    - In the "Promote to" dialog:
        - Enter the base class name of the placeholder widget.
        - Enter the promoted class name as `QDragWidget`.
        - Enter the header file path as `Custom_Widgets.QDraggableWidget.h`.

    This promotion enables the placeholder widget to accept drag-and-drop functionality.

4. Promote a Placeholder Widget to QDragItem:

    - Right-click on the placeholder widget that you want to make draggable within the promoted `QDragWidget`.
    - Select "Promote to..." from the context menu.
    - In the "Promote to" dialog:
        - Enter the base class name of the placeholder widget.
        - Enter the promoted class name as `QDragItem`.
        Enter the header file path as `Custom_Widgets.QDraggableWidget.h`.

    This promotion makes the placeholder widget draggable within the parent QDragWidget.

By following these steps, you can create and use draggable widgets within Qt Designer by promoting existing widgets to QDragWidget and QDragItem.

### Further Customization
Customize the appearance and behavior of the draggable items and the drag widget as needed.
