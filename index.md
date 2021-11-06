<link rel="icon" href="https://i2.wp.com/www.icon0.com/wp-content/uploads/2021/05/stock-photo-tick-icon-sign-design-13148.jpg?fit=400%2C400&ssl=1" />
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
```cpp
class mywindow:public QWidget
{
public:
     mywindow(QWidget*parents=nullptr):QWidget(parents){

   setWindowTitle("QHBoxLayout");
    name =new QLabel("Name:");
    name->setStyleSheet("font:bold 15px");
    line=new QLineEdit;
    button=new QPushButton("search");
    button->setStyleSheet("font:bold 15px");

    auto layout=new QHBoxLayout;
               setLayout(layout);
               layout->addWidget(name);
               layout->addWidget(line);
               layout->addWidget(button);
    };

protected:
    QLabel *name;
    QLineEdit *line;
    QPushButton * button;

};
```
```cpp
int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    mywindow w;
    w.show();
    return a.exec();
}

```
![qhboxlayouts](https://user-images.githubusercontent.com/93833171/140616506-8e02ac1b-a25a-459f-94aa-a1cfc69d0337.PNG)


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

