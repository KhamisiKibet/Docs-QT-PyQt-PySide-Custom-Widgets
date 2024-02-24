---
layout: default
title: JSON Stylesheet Cheatsheet
nav_order: 7
description: "An update on new features being added to the Custom Widgets Module."
permalink: /docs/json-stylesheet-cheatsheet
has_children: true
---

# JSON Stylesheet Cheatsheet
## Overview:
This JSON stylesheet is used to customize the appearance and behavior of PyQt/PySide custom widgets in the QT-PyQt-PySide-Custom-Widgets module.

## Loading JSON files

Import the Custom Widgets

```python
from Custom_Widgets import *
from Custom_Widgets.QAppSettings import QAppSettings
```

Load the JSon files

```python
# self = QMainWindow class
# self.ui = Ui_MainWindow / user interface class

#Use this if you only have one json file named "style.json" inside the root directory, "json" directory or "jsonstyles" folder.
loadJsonStyle(self, self.ui) 

# OR

# Use this to specify your json file(s) path/name
loadJsonStyle(self, self.ui, jsonFiles = {
    "json-styles/style.json"
}) 
```

If you're using QSettings and App-theme, apply the settings:

```python
########################################################################
# UPDATE APP SETTINGS LOADED FROM JSON STYLESHEET 
# ITS IMPORTANT TO RUN THIS AFTER SHOWING THE WINDOW
# THIS PROCESS WILL RUN ON A SEPARATE THREAD WHEN GENERATING NEW ICONS
# TO PREVENT THE WINDOW FROM BEING UNRESPONSIVE
########################################################################
# self = QMainWindow class
QAppSettings.updateAppSettings(self)
```

## Format:
The JSON stylesheet consists of the following section:

1. `ShowLogs`:

```json
{
  "ShowLogs": true
}
```

or

```json
{
  "ShowLogs": false
}

```

2. `LiveCompileQss`:

Specifies whether live compilation of QSS and JSON stylesheet files should be enabled or disabled.

Example:

```json
{
  "LiveCompileQss": true
}

```

or

```json
{
  "LiveCompileQss": false
}
```

3. `CheckForMissingicons`:

Specifies whether to generate missing icons, including Qt Designer icons.

Example:

```json
{
  "CheckForMissingicons": true
}
```

or

```json
{
  "CheckForMissingicons": false
}
```

4. `ThemeSettings`:

Specifies custom themes and their settings.

Example:

```json
{
  "ThemeSettings": [
    {
      "CustomTheme": [
        {
          "Theme-name": "CustomTheme1",
          "Background-color": "#FFFFFF",
          "Text-color": "#000000",
          "Accent-color": "#FF0000",
          "Icons-color": "#333333",
          "Default-Theme": true,
          "Create-icons": true
        },
        {
          "Theme-name": "CustomTheme2",
          "Background-color": "#F0F0F0",
          "Text-color": "#333333",
          "Accent-color": "#00FF00",
          "Icons-color": "#FFFFFF",
          "Default-Theme": false,
          "Create-icons": false
        }
      ]
    }
  ]
}
```

5. `QCard`:

Specifies settings for QCard widgets and their cards, including shadow effects.

Example:

```json
{
  "QCard": [
    {
      "cards": [
        "card1",
        "card2"
      ],
      "shadow": [
        {
          "color": "#000000",
          "blurRadius": 10,
          "xOffset": 5,
          "yOffset": 5
        }
      ]
    }
  ]
}
```

6. `QPushButtonGroup`:

Specifies settings for QPushButtonGroup objects, including buttons and their styles.

Example:

```json
{
  "QPushButtonGroup": [
    {
      "Buttons": ["button1", "button2"],
      "ActiveButton": "button1",
      "Style": [
        {
          "Active": {
            "background-color": "#FFFFFF",
            "font-color": "#000000"
          },
          "NotActive": {
            "background-color": "#CCCCCC",
            "font-color": "#666666"
          }
        }
      ]
    }
  ]
}
```

7. `AnalogGaugeWidget`:

Specifies settings for Analog Gauge Widget objects, including various properties such as min/max values, gauge theme, colors, fonts, etc.

Example:

```json
{
  "AnalogGaugeWidget": [
    {
      "name": "analogGauge1",
      "units": "km/h",
      "minValue": 0,
      "maxValue": 200,
      "scalaCount": 10,
      "startValue": 0,
      "gaugeTheme": 1,
      "offsetAngle": 0,
      "innerRadius": 70,
      "outerRadius": 100,
      "scaleStartAngle": 135,
      "totalScaleAngle": 270,
      "enableBarGraph": true,
      "enableValueText": true,
      "enableNeedlePolygon": true,
      "enableCenterPoint": true,
      "enableScaleText": true,
      "enableScaleBigGrid": true,
      "enableScaleFineGrid": true,
      "needleColor": "#FF0000",
      "needleColorOnDrag": "#00FF00",
      "scaleValueColor": "#0000FF",
      "displayValueColor": "#FFFF00",
      "bigScaleColor": "#FF00FF",
      "fineScaleColor": "#00FFFF",
      "customGaugeTheme": [
        {
          "color1": "#FF0000",
          "color2": "#00FF00",
          "color3": "#0000FF"
        }
      ],
      "scalePolygonColor": [
        {
          "color1": "#FF0000",
          "color2": "#00FF00",
          "color3": "#0000FF"
        }
      ],
      "needleCenterColor": [
        {
          "color1": "#FF0000",
          "color2": "#00FF00",
          "color3": "#0000FF"
        }
      ],
      "outerCircleColor": [
        {
          "color1": "#FF0000",
          "color2": "#00FF00",
          "color3": "#0000FF"
        }
      ],
      "valueFontFamily": [
        {
          "path": "fonts/MyFont.ttf",
          "name": "MyFont"
        }
      ],
      "scaleFontFamily": [
        {
          "path": "fonts/MyFont.ttf",
          "name": "MyFont"
        }
      ]
    }
  ]
}
```
8. `QCustomSlideMenu`:

Specifies settings for QCustomSlideMenu widgets.

Example:
```json
{
  "QCustomSlideMenu": [
    {
      "name": "customSlideMenu1",
      "floatPosition": [
        {
          "relativeTo": "parentWidget",
          "position": "bottom",
          "shadow": {
            "color": "#000000",
            "blurRadius": 10,
            "xOffset": 0,
            "yOffset": 5
          },
          "autoHide": true
        }
      ],
      "defaultSize": {
        "width": 300,
        "height": 200
      },
      "collapsedSize": {
        "width": 50,
        "height": 200
      },
      "expandedSize": {
        "width": 300,
        "height": 400
      },
      "menuTransitionAnimation": {
        "animationDuration": 500,
        "animationEasingCurve": "EaseInOutQuad",
        "whenCollapsing": [
          {
            "animationDuration": 300,
            "animationEasingCurve": "EaseOutQuad"
          }
        ],
        "whenExpanding": [
          {
            "animationDuration": 800,
            "animationEasingCurve": "EaseInCubic"
          }
        ]
      },
      "menuContainerStyle": {
        "whenMenuIsCollapsed": {
          "background-color": "#CCCCCC",
          "color": "#FFFFFF"
        },
        "whenMenuIsExpanded": {
          "background-color": "#FFFFFF",
          "color": "#000000"
        }
      },
      "toggleButton": [
        {
          "buttonName": "toggleButton1",
          "icons": {
            "whenMenuIsCollapsed": "icon_collapsed.png",
            "whenMenuIsExpanded": "icon_expanded.png"
          },
          "style": {
            "whenMenuIsCollapsed": {
              "background-color": "#CCCCCC",
              "color": "#FFFFFF"
            },
            "whenMenuIsExpanded": {
              "background-color": "#FFFFFF",
              "color": "#000000"
            }
          }
        }
      ]
    }
  ]
}
```

9. `QMainWindow`:

Specifies settings for QMainWindow objects, including window title, icon, frameless mode, transparent background, size grip, shadow effect, and window navigation options.

Example:

```json
{
  "QMainWindow": [
    {
      "tittle": "My Custom Window",
      "icon": "path/to/icon.png",
      "frameless": true,
      "transluscentBg": true,
      "sizeGrip": "sizeGripWidget",
      "shadow": [
        {
          "centralWidget": "centralWidgetName",
          "color": "#000000",
          "blurRadius": 10,
          "xOffset": 5,
          "yOffset": 5
        }
      ],
      "navigation": [
        {
          "minimize": "minimizeButton",
          "close": "closeButton",
          "restore": [
            {
              "buttonName": "restoreButton",
              "normalIcon": "path/to/normal_icon.png",
              "maximizedIcon": "path/to/maximized_icon.png"
            }
          ],
          "moveWindow": "moveWindowHeader",
          "tittleBar": "tittleBarWidget"
        }
      ]
    }
  ]
}
```

10. `QPushButton`:

Specifies settings for QPushButton objects.

Example:

```json
{
  "QPushButton": [
    {
      "name": "button1",
      "theme": "customTheme1",
      "customTheme": [
        {
          "color1": "#FFFFFF",
          "color2": "#000000"
        }
      ],
      "animateOn": "hover",
      "animation": "fade",
      "animationDuration": 300,
      "animationEasingCurve": "in-out-cubic",
      "fallBackStyle": [
        "background-color: #CCCCCC;",
        "font-color: #666666;"
      ],
      "defaultStyle": [
        "background-color: #FFFFFF;",
        "font-color: #000000;"
      ],
      "iconify": [
        {
          "icon": "path/to/icon",
          "color": "#FF0000",
          "size": 24,
          "animateOn": "click",
          "animation": "spin"
        }
      ],
      "shadow": [
        {
          "color": "#000000",
          "applyShadowOn": "hover",
          "animateShadow": true,
          "animateShadowDuration": 200,
          "blurRadius": 5,
          "xOffset": 2,
          "yOffset": 2
        }
      ]
    }
  ]
}
```

11. `QCustomQStackedWidget`:

Specifies settings for a custom QStackedWidget, including transition animations and navigation buttons.

Example:

```json
{
  "QCustomQStackedWidget": [
    {
      "name": "customStackedWidget",
      "transitionAnimation": [
        {
          "fade": [
            {
              "active": true,
              "duration": 500,
              "easingCurve": "easeInOutQuad"
            }
          ],
          "slide": [
            {
              "active": true,
              "duration": 300,
              "easingCurve": "easeInOutCubic",
              "direction": "LeftToRight"
            }
          ]
        }
      ],
      "navigation": [
        {
          "nextPage": "nextButton",
          "previousPage": "prevButton",
          "navigationButtons": [
            {
              "button1": "page1",
              "button2": "page2"
            }
          ]
        }
      ]
    }
  ]
}
```

12. `QCustomProgressIndicator`:

Specifies settings for QCustomProgressIndicator widgets, including colors, sizes, and animation parameters.

Example:

```json
{
  "QCustomProgressIndicator": [
    {
      "name": "progressIndicator1",
      "color": "#FFFFFF",
      "fillColor": "#00FF00",
      "warningFillColor": "#FFFF00",
      "errorFillColor": "#FF0000",
      "successFillColor": "#00FF00",
      "formProgressCount": 5,
      "formProgressAnimationDuration": 1000,
      "formProgressAnimationEasingCurve": "easeInOutCubic",
      "height": 20,
      "width": 200,
      "startPercentage": 0,
      "theme": 1
    }
  ]
}
```

13. `QCustomCheckBox`:

Specifies settings for QCustomCheckBox widgets, including background color, circle color, active color, animation easing curve, and animation duration.

Example:

```json
{
  "QCustomCheckBox": [
    {
      "name": "customCheckBox1",
      "bgColor": "#FFFFFF",
      "circleColor": "#000000",
      "activeColor": "#FF0000",
      "animationEasingCurve": "Linear",
      "animationDuration": 500
    },
    {
      "names": ["customCheckBox2", "customCheckBox3"],
      "bgColor": "#F0F0F0",
      "circleColor": "#333333",
      "activeColor": "#00FF00",
      "animationEasingCurve": "OutQuad",
      "animationDuration": 1000
    }
  ]
}
```