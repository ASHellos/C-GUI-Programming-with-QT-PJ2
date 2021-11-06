<link rel="shortcut icon" type="image/x-icon" href="favicon.ico">

# Programming Widget Layout

## <span style="color:red">Introduction:</span>

_Qt inclut un ensemble de classes de gestion de disposition qui sont utilisées pour décrire comment les widgets sont disposés dans l'interface utilisateur d'une application. Ces dispositions positionnent et redimensionnent automatiquement les widgets lorsque la quantité d'espace disponible pour eux change, garantissant qu'ils sont organisés de manière cohérente et que l'interface utilisateur dans son ensemble reste utilisable._

> **widget** : Widgets are the primary elements for creating user interfaces in Qt. Widgets can display data and status information, receive user input, and provide a container for other widgets that should be grouped together. A widget that is not embedded in a parent widget is called a window.

* * *

> **Layout** :The Qt layout system provides a simple and powerful way of automatically arranging child widgets within a widget to ensure that they make good use of the available space.

### <span style="color:orange">After using the acquired knowledge, the following models were created.</span>

* [Nested](#a)
*   Nested Layouts
*   Bug report Form
*   Grid Layout

#### <span style="color:blue">1-Experimenting with QHBOXLayout</span> (#a)
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
 <span style="color:black">here is the following form:</span>

![qhboxlayouts](https://user-images.githubusercontent.com/93833171/140616506-8e02ac1b-a25a-459f-94aa-a1cfc69d0337.PNG)



### <span style="color:blue">3-Bug report Form</span>
```cpp
class window:public QWidget{

public:
    window(QWidget *parents=nullptr):QWidget(parents){// le constructeur

     setWindowTitle("Report Bug");


     //QVBoxLayout
        main_layouts=new QVBoxLayout();
        setLayout(main_layouts);

      //label&LineEdits_Name
     formlables_name=new QLabel("Name:",this);
     formEdits_name=new QLineEdit(this);
      //label&LineEdits_Campany
     formlables_company=new QLabel("Campany:",this);
     formEdits_company=new QLineEdit(this);
      //label&LineEdits_Phone
     formlables_phone=new QLabel("Phone:",this);
     formEdits_phone=new QLineEdit(this);
     //label&LineEdits_Email
     formlables_email=new QLabel("Email:",this);
     formEdits_email=new QLineEdit(this);
     //label&LineEdits_formlables_problem_title
     formlables_problem_title=new QLabel("Problem Title:",this);
     formEdits_problem_title=new QLineEdit(this);
      //label&LineEdits_Summary  
     formlables_summary=new QLabel("Summary Information:",this);
     formEdits_summary=new QTextEdit(this);
     //label&LineEdits_reproducibility
     lable_reproducibility=new QLabel("Reproducibility:",this);
     box_rep=new QComboBox();
     box_rep->addItem("Always");
       // form layouts
       formlayouts=new  QFormLayout(this);
       formlayouts->addRow(formlables_name,formEdits_name);
       formlayouts->addRow(formlables_company,formEdits_company);
       formlayouts->addRow(formlables_phone,formEdits_phone);
       formlayouts->addRow(formlables_email,formEdits_email);
       formlayouts->addRow(formlables_problem_title,formEdits_problem_title);
       formlayouts->addRow(formlables_summary,formEdits_summary);
       formlayouts->addRow(lable_reproducibility,box_rep);
 main_layouts->addLayout(formlayouts);


  //Qhboxlayout
   row_button1=new QHBoxLayout;

  //pUSHBUTTONBOS
   reset=new QPushButton("Reset");
   submet=new QPushButton("Submet Bug Report");
   Dontsubmit=new QPushButton("D'ont Submet");
   row_button1->addWidget(reset);
   row_button1->addSpacerItem(new QSpacerItem(50,10,QSizePolicy::Expanding));
   row_button1->addWidget(submet);
   row_button1->addWidget(Dontsubmit);


    main_layouts->addLayout(row_button1);
    }

protected:
 //QFormlayouts
 QFormLayout *formlayouts;

 //labels
 QLabel *formlables_name;
 QLabel *formlables_company;
 QLabel *formlables_phone;
 QLabel *formlables_email;
 QLabel *formlables_problem_title;
 QLabel *formlables_summary;
 QLabel *lable_reproducibility;
  //lineEdits
 QLineEdit *formEdits_name;
QLineEdit *formEdits_company;
QLineEdit *formEdits_phone;
QLineEdit *formEdits_email;
QLineEdit *formEdits_problem_title;
//text edit
QTextEdit *formEdits_summary;
//qgroupebox
QGroupBox *form_groups;
//QVBoxLayout
QVBoxLayout *main_layouts;
//QComboBox
QComboBox *box_rep;
//QPushButton
QPushButton *button1;
QPushButton *button2;
QPushButton *button3;
//QVBoxLayoutt
QVBoxLayout *mainlayouts;
//QhBoxLayout
QHBoxLayout *row_button1;
//QPushbutton
QPushButton *reset;
QPushButton *submet;
QPushButton *Dontsubmit;
};


```
```cpp
int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    window w;
    w.show();
    return a.exec();
}
```
<span style="color:black">here is the following form:</span>

![furmulaire](https://user-images.githubusercontent.com/93833171/140618191-7c602867-109b-4296-b2f5-7b01fea81709.PNG)
### <span style="color:blue">4-Grid Layout</span>


```c++
class window:public QWidget{

  //constructeur
protected:
    QVBoxLayout *mainlayout;
    QGridLayout *gridlayout;
    QPushButton* gridbutton[10]  //for the number of pushbutton;
    QGroupBox* gridgroup;
    QLCDNumber* qlcd;
    QPushButton* enter;

public:
    window(QWidget *parents=nullptr):QWidget(parents){
gridlayout= new QGridLayout;
        qlcd= new QLCDNumber(6);//for showing the number by the componnent LCDNumber with assume that at max it can contains 6 digits
        qlcd->setMinimumHeight(80);// to set a minimu height of 80 pixels for the lcd number
        setWindowTitle("Numeric Keypad");
        mainlayout = new QVBoxLayout();
        setLayout(mainlayout);
        mainlayout->setSpacing(2);
        mainlayout->addWidget(qlcd);// to add the lcd at the top of layout
        mainlayout->addLayout(gridlayout);
gridbutton[0]=new QPushButton(QString::number(0));

      for (int i=10;i>0 ;i-- ) {
          gridbutton[i]=new QPushButton(QString::number(i));
gridlayout->addWidget(gridbutton[i],((9-i)/3), (i-1)%3);
            }
      gridlayout->addWidget(gridbutton[0]);
        enter = new QPushButton("Enter");
      gridlayout->addWidget(enter, 3, 1,1,2);
}
};

```

```cpp
int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
window p;
p.show();
    return a.exec();
}
```
 ![2021-11-06 18_56_09-CS311 _ Signal and Slots](https://user-images.githubusercontent.com/93819249/140619234-62baf751-ad69-4ea7-937d-14a3e629db99.png)
Just as widgets can ![furmulaire](https://user-
contain other widgets, layouts can be used to provide different levels of grouping for widgets. Here, we want to display a label alongside a line edit at the top of a window, above a table view showing the results of a query,Thats what we called **Nested Layout**
### Bug report Form
we need befaure using them to knew whats is the diffre
The QBoxLayout class lines up widgets horizontally or vertically. QHBoxLayout and QVBoxLayout are convenience subclasses of QBoxLayout. QGridLayout lays out widgets in cells by dividing the available space into rows and columns. 
***QFormLayout***, on the other hand, sets its children in a two-column form with labels in the left column and input fields in the right column.
### __****Grid Layout****__
 **QGridLayout** lays out widgets in cells by dividing the available space into rows and columns.
 QGridLayout takes the space made available to it (by its parent layout or by the parentWidget()), divides it up into rows and columns, and puts each widget it manages into the correct cell. 
 If the GridLayout is resized, all items in the layout will be rearranged. It is similar to the widget-based QGridLayout. All visible children of the GridLayout element will belong to the layout.
 


