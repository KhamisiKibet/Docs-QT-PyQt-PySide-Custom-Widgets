---
layout: default
title: QFlowProgressBar
parent: Available Widgets
nav_order: 23
permalink: /docs/widgets/flow-progress-bar
---

# QT-PyQt-PySide-Custom-Widgets - QFlowProgressBar

![Custom Embeded Window GIF](https://github.com/KhamisiKibet/Docs-QT-PyQt-PySide-Custom-Widgets/raw/main/images/flow-progress-bar.gif)

## Overview

The `QFlowProgressBar` widget provides a customizable progress bar with flow-style indicators for PyQt/PySide6 applications. It offers several visual styles, including circular, flat, square, and breadcrumb, allowing users to represent progress in various ways. This widget is suitable for displaying progress through a series of steps or stages, with each step being clickable for interaction.

### Features

- **Multiple Styles**: Choose from circular, flat, square, or breadcrumb styles to suit different design requirements.
- **Step Interaction**: Steps are clickable, allowing users to navigate between different stages of progress.
- **Customizable Appearance**: Customize colors, font sizes, and animation duration to match the application's visual theme.
- **Pointer Direction**: For flat-style progress bars, the pointer direction can be set to indicate progress direction.
- **Signal Emission**: Emit signals when a step is clicked, enabling interaction with other parts of the application.

### Installation

Install the QT-PyQt-PySide-Custom-Widgets package using pip:

```sh
pip install QT-PyQt-PySide-Custom-Widgets
```

### Importing
```python
from Custom_Widgets.QFlowProgressBar import QFlowProgressBar
```

## Class: QFlowProgressBar
### Constructor

```python
def __init__(self, strDetailList: List[str] = None, style: int = Styles.Circular, parent: QWidget = None,
             finishedNumberColor: QColor = QColor(255, 255, 255), finishedBackgroundColor: QColor = QColor(0, 136, 254),
             unfinishedBackgroundColor: QColor = QColor(228, 231, 237), numberFontSize: int = 9, textFontSize: int = 10,
             currentStep: int = 0, pointerDirection: Direction = Direction.Up,
             animationDuration: int = 1000, easingCurve: QEasingCurve.Type = QEasingCurve.OutQuad, stepsClickable: bool = True)

```

Constructs a QFlowProgressBar widget with the specified parameters.

- `strDetailList`: List of detail strings for each step.
- `style`: Style of the progress bar (Circular, Flat, Square, Breadcrumb).
- `parent`: Parent widget.
- `finishedNumberColor`: Color for finished step numbers.
- `finishedBackgroundColor`: Background color for finished steps.
- `unfinishedBackgroundColor`: Background color for unfinished steps.
- `numberFontSize`: Font size for step numbers.
- `textFontSize`: Font size for step descriptions.
- `currentStep`: The current step in the progress bar.
- `pointerDirection`: Pointer direction for flat progress bars (Up, Down).
- `animationDuration`: Duration of the animation in milliseconds.
- `easingCurve`: Easing curve for the animation.
- `stepsClickable`: Boolean indicating whether steps are clickable.

### Methods
- `getCurrentStep`(): Returns the current step.
- changeCurrentStep(step: int): Changes the current step of the progress bar.
- `getDrawTextSize`(text: str, font: QFont) -> QRect: Gets the size of the text to be drawn.
- `getBackgroundColor`() -> QColor: Gets the background color of the progress bar.
- `getFinishedBackgroundColor`() -> QColor: Gets the color for finished progress segments.
- `getFinishedNumberColor`() -> QColor: Gets the color for finished numbers in the progress bar.

### Signals
`onStepClicked`(int): Signal emitted when a step is clicked, providing the index of the clicked step.

### Example usage
```python
import sys
from PySide6.QtWidgets import QApplication, QMainWindow, QVBoxLayout, QPushButton, QWidget
from PySide6.QtCore import Qt
from PySide6.QtGui import QColor

from Custom_Widgets.QFlowProgressBar import QFlowProgressBar


class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Progress Bar Test")
        self.setGeometry(100, 100, 800, 600)

        main_layout = QVBoxLayout()

        # Initialize the QFlowProgressBase widget
        steps = ["Start: Step 1", "Step 2", "Step 3", "Final step: Step 4"]

        # Initialize different styles of QFlowProgressBar widgets with additional arguments
        self.flow_progress_bars = []
        styles = [
            QFlowProgressBar.Styles.Circular,
            QFlowProgressBar.Styles.Flat,
            QFlowProgressBar.Styles.Square
        ]

        for style in styles:
            # Customize colors for different progress bars
            if style == QFlowProgressBar.Styles.Circular:
                finished_color = QColor(0, 136, 254)  # Blue
                unfinished_color = QColor(228, 231, 237)  # Light gray
            elif style == QFlowProgressBar.Styles.Flat:
                finished_color = QColor(0, 176, 80)  # Green
                unfinished_color = QColor(255, 192, 0)  # Yellow
            else:
                finished_color = QColor(255, 0, 0)  # Red
                unfinished_color = QColor(128, 128, 128)  # Dark gray

            # Create progress bars with customized colors and labels
            progress_bar = QFlowProgressBar(
                steps,
                style,
                finishedBackgroundColor=finished_color,
                unfinishedBackgroundColor=unfinished_color,
                finishedNumberColor=Qt.white,  # White
                numberFontSize=12,  # Font size
                textFontSize=10,  # Font size
                pointerDirection=QFlowProgressBar.Direction.Down,  # Pointer direction for flat style
                animationDuration=1000,  # Animation duration
                stepsClickable=True  # Steps are clickable
            )

            progress_bar.setMaximumHeight(100)
            progress_bar.setMinimumHeight(70)
            progress_bar.onStepClicked.connect(self.on_step_clicked)
            self.flow_progress_bars.append(progress_bar)

        # Add buttons to control the progress bars
        self.next_button = QPushButton("Next Step")
        self.next_button.clicked.connect(self.next_step)

        self.prev_button = QPushButton("Previous Step")
        self.prev_button.clicked.connect(self.prev_step)

        # Add widgets to layout
        for progress_bar in self.flow_progress_bars:
            main_layout.addWidget(progress_bar)

        main_layout.addWidget(self.next_button)
        main_layout.addWidget(self.prev_button)

        container = QWidget()
        container.setLayout(main_layout)
        self.setCentralWidget(container)

    def next_step(self):
        # Move to the next step for each progress bar
        for progress_bar in self.flow_progress_bars:
            progress_bar.changeCurrentStep(progress_bar.getCurrentStep() + 1)

    def prev_step(self):
        # Move to the previous step for each progress bar
        for progress_bar in self.flow_progress_bars:
            progress_bar.changeCurrentStep(progress_bar.getCurrentStep() - 1)

    def on_step_clicked(self, step: int):
        # Handle step clicked event
        print(f"Step {step + 1} clicked")

        # Set the clicked step for each progress bar
        for progress_bar in self.flow_progress_bars:
            progress_bar.changeCurrentStep(step + 1)


if __name__ == "__main__":
    app = QApplication(sys.argv)

    window = MainWindow()
    window.show()

    sys.exit(app.exec())


```

## Dependencies
- PyQt or PySide
- QT-PyQt-PySide-Custom-Widgets (version 0.8.5 and above)
