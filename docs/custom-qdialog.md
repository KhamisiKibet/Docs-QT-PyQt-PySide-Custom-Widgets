---
layout: default
title: QCustomQDialog
parent: Available Widgets
nav_order: 13
permalink: /docs/widgets/custom-qdialog
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomQDialog

## QCustomQDialog

![Custom Dialog GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/custom-dialog.gif)

### Overview
The QCustomQDialog widget provides a customizable dialog box for PyQt/PySide applications. It features various customization options such as title, description, button icons, and animation effects, allowing developers to create tailored dialog boxes for their applications.

### Features
- **Customizable Appearance**: Users can customize the dialog's title, description, button text, and icons.
- **Closable**: Offers Yes and Cancel buttons with options to show or hide them.
- **Animation Effects**: Supports fade-in and fade-out animations for showing and hiding the dialog.
- **Movable**: Can be configured to be movable when frameless.
- **Shadow Effect**: Provides a drop shadow effect for the dialog.

## Usage

### Installation
Install the QT-PyQt-PySide-Custom-Widgets package using pip:

```cmd
pip install QT-PyQt-PySide-Custom-Widgets
```

### Importing
```python
from Custom_Widgets.QCustomQDialog import QCustomQDialog
```

### Creating a Custom Dialog
```python
custom_dialog = QCustomQDialog(
    title="Custom Dialog",
    description="This is a custom dialog.",
    padding=20,
    margin=60,
    yesButtonIcon=my_yes_icon,
    cancelButtonIcon=my_cancel_icon,
    yesButtonText="Yes",
    cancelButtonText="Cancel",
    animationDuration=500,
    showYesButton=True,
    showCancelButton=True,
    setModal=True,
    frameless=True,
    windowMovable=True,
    showForm=myFormWidget, #display a ui form inside the dialog box ie importing your form(from ui_form import myFormWidget)
    # to access the widgets inside your form (custom_dialog.shownForm.myWidgetName)
    parent=myParentWidget,
    addWidget=yourNewWidget #append another widget or widget container to the dialog
)
# alternative:
# to append another widget or widget container to the dialog
custom_dialog.addWidget(yourNewWidget)

custom_dialog.show()

# events
custom_dialog.accepted.connect(lambda: print("Accepted!")) #yes button clicked
custom_dialog.rejected.connect(lambda: print("Rejected!")) #cancel button clicked

```
### Customization Options
- **Title**: Set the title of the dialog.
- **Description**: Provide a description text for the dialog.
- **Yes Button Text**: Customize the text of the Yes button.
- **Cancel Button Text**: Customize the text of the Cancel button.
- **Yes Button Icon**: Specify an icon for the Yes button.
- **Cancel Button Icon**: Specify an icon for the Cancel button.
- **Show Yes Button**: Show or hide the Yes button.
- **Show Cancel Button**: Show or hide the Cancel button.
- **Set Modal**: Configure the dialog to be modal.
- **Frameless**: Enable or disable the frameless window style.
- **Window Movable**: Enable or disable the window movable feature.
- **Animation Duration**: Set the duration of the fade-in and fade-out animations.
- **Show Form**: Show a custom form widget within the dialog.
- **Add Widget**: Show a widget within the dialog.

#### Customization using SCSS/CSS
```scss
QCustomQDialog{
	#widget {
		background-color: $COLOR_BACKGROUND_1;
		min-width: 300px;
	}
	#cancelButton{
		background-color: $COLOR_BACKGROUND_3;
		font-weight: bold;
		icon: url($PATH_RESOURCES+'font_awesome/solid/circle-xmark.png');
		icon-size: 20px 20px;
	}
	#yesButton{
		background-color: $COLOR_ACCENT_1;
		font-weight: bold;
		icon: url($PATH_RESOURCES+'material_design/check_circle.png');
		icon-size: 20px 20px;
	}
	#mainBody{
		border-bottom: $BORDER_2;
		background-color: $COLOR_BACKGROUND_3;
		//***Other widgets you added to the dialog
	}
	#footer{
		background-color: transparent;
		border: none;
	}
}
```

### Example
```python
import sys
from PySide6.QtWidgets import QApplication, QMainWindow, QPushButton, QVBoxLayout, QWidget
from Custom_Widgets.QCustomQDialog import QCustomQDialog

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QCustomQDialog Example")
        self.central_widget = QWidget()
        self.setCentralWidget(self.central_widget)
        self.layout = QVBoxLayout(self.central_widget)

        self.button = QPushButton("Show Dialog")
        self.button.clicked.connect(self.show_dialog)
        self.layout.addWidget(self.button)

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

    def show_dialog(self):
        dialog = QCustomQDialog(
            parent = self,
            title="Dialog Title",
            description="Dialog Description",
            yesButtonText="Confirm",
            cancelButtonText="Cancel",
            # yesButtonIcon="yes_icon.png",
            # cancelButtonIcon="cancel_icon.png",
            showYesButton=True,
            showCancelButton=True,
            setModal=True,
            frameless=True,
            windowMovable=True,
            animationDuration=500
        )
        dialog.show()

        # events
        dialog.accepted.connect(lambda: print("Accepted!")) #yes button clicked
        dialog.rejected.connect(lambda: print("Rejected!")) #cancel button clicked

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MainWindow()
    window.resize(300, 200)
    window.show()
    sys.exit(app.exec())

```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version 0.8.5 and above)

