---
layout: default
title: QCustomModals
parent: Available Widgets
nav_order: 9
permalink: /docs/widgets/custom-modals
---

# QT-PyQt-PySide-Custom-Widgets - Customizing QCustomModals

## QCustomModals
`QCustomModals` is a module that provides custom modal dialogs for PySide/PyQt applications. It includes various types of modal dialogs such as Information, Success, Warning, Error, and Custom modals. These modals are designed to be highly customizable and can be positioned according to the user's preference.

## Installation
Install the QT-PyQt-PySide-Custom-Widgets package using pip:

```cmd
pip install QT-PyQt-PySide-Custom-Widgets
```

## Usage
Importing the Module

```python
from Custom_Widgets.QCustomModals import QCustomModals
```

## Creating a Modal Dialog
```python
myModal = QCustomModals.InformationModal(
    title="Updating dashboard", 
    parent=self.main,
    position='top-right',
    closeIcon=self.main.theme.PATH_RESOURCES+"window_close.png",
     modalIcon=self.main.theme.PATH_RESOURCES+"custom_icon.png" 
    description="Refreshing dashboard information",
    isClosable=False,
    duration=3000
)
myModal.show()
```
## Available Modal Types
- InformationModal
- SuccessModal
- WarningModal
- ErrorModal
- CustomModal

## Customizing Modal Appearance
The modal appearance can be customized by passing various parameters such as `title`, `description`, closeIcon, `isClosable`, and `duration` while creating the modal dialog.

Additionally, users are strongly recommended to customize the modal using `CSS/SCSS` files to match their `dynamic app theme`. For example:

```scss
InformationModal {
    border-radius: 10px;
    border: 5px solid $COLOR_BACKGROUND_2;

    QPushButton#closeButton {
        background-color: transparent;
        icon: url($PATH_RESOURCES+'window_close.png'); //modal close icon, if its closable
    }

    QLabel#iconlabel {
        image: url($PATH_RESOURCES+"info.png"); // modal icon at top left side
        min-width: 20px;
        min-height: 20px;
        max-width: 20px;
        max-height: 20px;
    }
}

```

## Setting Modal Icon
You can set a custom icon for the modal by using `CSS` as shown above or by passing the `modalIcon` parameter while creating the modal dialog. For example:

```python
myModal = QCustomModals.InformationModal(
    # other parameters
    modalIcon= "custom_icon.png"  # Path to the custom modal icon image
)
myModal.show()
```

If the `modalIcon` parameter is provided, the modal will display the specified icon. Otherwise, it will default to the icon specified in the `CSS/SCSS` file.


## Positioning
Modals can be positioned at different locations on the screen by specifying the position parameter. Available positions include:

- top-right
- top-center
- top-left
- center-center
- center-right
- center-left
- bottom-right
- bottom-left
- bottom-center

## Features
- Customizable title, description, close icon, and duration.
- Various types of modals available: Information, Success, Warning, Error, and Custom.
- Support for positioning modals at different locations on the screen.
- Ability to customize modal appearance and behavior using CSS/SCSS files.

## Example
```python
myModal = QCustomModals.InformationModal(
    title="Updating dashboard",  # Title of the modal dialog
    parent=self.main,  # Parent widget to which the modal belongs
    position='top-right',  # Position to display the modal dialog
    closeIcon=self.main.theme.PATH_RESOURCES+"window_close.png",  # Path to the close icon image
    description="Refreshing dashboard information",  # Description text displayed in the modal dialog
    isClosable=False,  # Whether the modal dialog is closable (True or False)
    duration=3000  # Duration (in milliseconds) for which the modal dialog remains visible
)

# Show the modal
myModal.show()

```

### More Information:
- `title`: The title parameter specifies the title of the modal dialog. It can be any string that represents the title of the dialog.

- `parent`: The parent parameter specifies the parent widget to which the modal belongs. This determines the modal's position relative to its parent widget.

- `position`: The position parameter specifies where the modal dialog will be displayed on the screen. It can take values such as 'top-right', 'top-center', 'bottom-left', etc. to specify the position of the modal dialog.

- `closeIcon`: The closeIcon parameter specifies the path to the close icon image displayed in the modal dialog. It should be a valid path to the image file.

- `description`: The description parameter specifies the text displayed in the modal dialog, providing additional information or instructions to the user.

- `isClosable`: The isClosable parameter determines whether the modal dialog is closable by the user. If set to True, the close button will be displayed, allowing the user to close the modal dialog.

- `duration`: The duration parameter specifies the duration (in milliseconds) for which the modal dialog remains visible before automatically closing. If set to 0, the modal will not automatically close.

### More examples
These examples demonstrate how to create different types of modals (Success, Warning, Error, and Custom) with custom titles, descriptions, and positions using the QCustomModals module in PyQt/PySide applications.

#### Example 1: Success Modal
```python
# Creating a success modal with a custom title and description
myModal = QCustomModals.SuccessModal(
    title="Success!",
    description="Your action was successful.",
    parent=self.main
)
myModal.show()
```

#### Example 2: Warning Modal
```python
# Creating a warning modal with a custom title and description
myModal = QCustomModals.WarningModal(
    title="Warning!",
    description="Please proceed with caution.",
    parent=self.main
)
myModal.show()
```

#### Example 3: Error Modal
```python
# Creating an error modal with a custom title and description
myModal = QCustomModals.ErrorModal(
    title="Error!",
    description="An error occurred. Please try again.",
    parent=self.main
)
myModal.show()
```

#### Example 4: Custom Modal
```python
# Creating a custom modal with a custom title, description, and position
myModal = QCustomModals.CustomModal(
    title="Custom Modal",
    description="This is a custom modal dialog.",
    position='bottom-right',
    parent=self.main
)
myModal.show()
```

## Dependencies
PySide/PyQt
QT-PyQt-PySide-Custom-Widgets (version `0.7.5 and above`)