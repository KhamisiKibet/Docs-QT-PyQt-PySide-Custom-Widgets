# Python: Updating old GUI app to work with the current Custom Widgets module update | PySide/PyQt
## _INTRO_
Join me for a special livestream: https://youtube.com/live/G6Af65xRihE?feature=share
In this livestream I am going to show you how you can easily convert your old PySide or PyQt desktop apps to work with the custom widgets module without any errors

We are going to update this old GUI tutorial from this video: https://youtu.be/adC48qZ8p5Y

## Steps
These are the steps were going to follow:

- Install the latest Custom Widgets module
    ```cmd
    pip install --upgrade QT-PyQt-PySide-Custom-Widgets
    ```
- Our GUI also uses an old version of ``PySideExtn`` that does not support ``PySide6`` so we will install the new updated version I made
    ```cmd
    pip install PySideExtn
    ```
- After installation, create an empty folder.
- Inside this folder, create a new Custom Widgets project by running the command below
    ```cmd
    Custom_Widgets --create-project
    ```
- Follow the onscreen prompt and feel the data you want.
- After the project has been created you can run it to ensure everything is working
- Now open your ``old project folder`` and copy every file to their respective folder inside the ``new project folder`` we just created. Ignore the following files:
    - The ``png icons`` files previously generated by the custom widget module, if available.
    - The interface ``ui_.... .py`` file genated from qt-designer or ``uic``
    - Qrc ``rc_..... .py`` files generated from ``.qrc`` files.
    - ``main.css, _style.scss, and _variables.scss`` file inside the ``QSS`` folder(if available). These files will be generated by the custom widgets module.
    
        > The custom widgets will generate new icons inside the `Qss` folder. New `ui` and other files will also be generated.
    
- When copying your files, please follow the folder structure described here: https://github.com/KhamisiKibet/QT-PyQt-PySide-Custom-Widgets?tab=readme-ov-file#version-069
    - Do not put anything inside the ``generated-files`` folder. This should only contain files created at run time.
    - Put all your ``JSon stylesheets`` for the custom widgets inside the ``json-styles`` folder.
    - ``logs`` folder is for log files.
    - The ``Qss`` folder is for ``Qt Stylesheet`` files. By default, this folder will contain ``icons`` and ``scss`` subfolders.
        - The ``scss(Sassy CSS)`` folder contains various scss files. Put your default css/scss code inside the ``defaultStyle.scss`` file.
        - The ``icons`` folder contains ``png icons`` and ``_icons.qrc`` files generated by the custom widgets module.
        - Remember to include the ``_icons.qrc`` file in your UI files if your want to use the icons. 
    
- Feel free to add other files and folders as you wish.
- Now generate new files from your ``ui`` files. Assuming that you put all your UI files inside the 'ui' folder, run the following command to convert the files:
    ```cmd
    Custom_Widgets --convert-ui ui-path --qt-library your-lib
    ```
    If youre tired of converting the UI files each time you make some changes, you can run a ``live files listener`` that will automatically convert the ui files for you.
    ```cmd
    Custom_Widgets --monitor-ui ui-path --qt-library your-lib
    ```
    
    Replace 'ui-path' with you ui path or folder, fo this case the ui folder is 'ui'.
    Repace 'your-lib' with your qt lib, or remove argument(--qt-library your-lib) if youre using ``PySide6``
    
- RUN your project.
    > Be patient, new missing icon files will be generated. View your terminal for `app theme` progress activities.

**That's all. HAPPY CODING**

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>