



# Programming Widget Layout

## Introduction:

_Qt inclut un ensemble de classes de gestion de disposition qui sont utilisées pour décrire comment les widgets sont disposés dans l'interface utilisateur d'une application. Ces dispositions positionnent et redimensionnent automatiquement les widgets lorsque la quantité d'espace disponible pour eux change, garantissant qu'ils sont organisés de manière cohérente et que l'interface utilisateur dans son ensemble reste utilisable._

> **widget** : Widgets are the primary elements for creating user interfaces in Qt. Widgets can display data and status information, receive user input, and provide a container for other widgets that should be grouped together. A widget that is not embedded in a parent widget is called a window.

* * *

> **Layout** :The Qt layout system provides a simple and powerful way of automatically arranging child widgets within a widget to ensure that they make good use of the available space.

### After using the acquired knowledge, the following models were created.

* [www.google.com] (Experimenting with QHBOXLayout" )
*   Nested Layouts
*   Bug report Form
*   Grid Layout

### Experimenting with QHBOXLayout

1.  We will start by using the main function in the data:

```cpp int main(int argc, char* argv[]) { QApplication app(argc, argv);

QWidget* window = new QWidget(); window->setWindowTitle("QHBoxLayout Test");

window->show();

return app.exec(); }

```

### Nested Layouts
Just as widgets can contain other widgets, layouts can be used to provide different levels of grouping for widgets. Here, we want to display a label alongside a line edit at the top of a window, above a table view showing the results of a query,Thats what we called **Nested Layout**
### Bug report Form
we need befaure using them to knew whats is the diffre
The QBoxLayout class lines up widgets horizontally or vertically. QHBoxLayout and QVBoxLayout are convenience subclasses of QBoxLayout. QGridLayout lays out widgets in cells by dividing the available space into rows and columns. 
***QFormLayout***, on the other hand, sets its children in a two-column form with labels in the left column and input fields in the right column.
### __****Grid Layout****__
 **QGridLayout** lays out widgets in cells by dividing the available space into rows and columns.
 QGridLayout takes the space made available to it (by its parent layout or by the parentWidget()), divides it up into rows and columns, and puts each widget it manages into the correct cell. 
 If the GridLayout is resized, all items in the layout will be rearranged. It is similar to the widget-based QGridLayout. All visible children of the GridLayout element will belong to the layout.















## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/ASHellos/C-GUI-Programming-with-QT-PJ2/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ASHellos/C-GUI-Programming-with-QT-PJ2/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
