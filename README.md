# Programming Widget Layout                                                                                                                    

## <span style="color:red">Introduction:</span>

_Qt inclut un ensemble de classes de gestion de disposition qui sont utilisées pour décrire comment les widgets sont disposés dans l'interface utilisateur d'une application. Ces dispositions positionnent et redimensionnent automatiquement les widgets lorsque la quantité d'espace disponible pour eux change, garantissant qu'ils sont organisés de manière cohérente et que l'interface utilisateur dans son ensemble reste utilisable._

> **widget** : Widgets are the primary elements for creating user interfaces in Qt. Widgets can display data and status information, receive user input, and provide a container for other widgets that should be grouped together. A widget that is not embedded in a parent widget is called a window.

* * *

> **Layout** :The Qt layout system provides a simple and powerful way of automatically arranging child widgets within a widget to ensure that they make good use of the available space.

### <span style="color:orange">After using the acquired knowledge, the following models were created.</span>

* [Experimenting with QHBOXLayout](#Experimenting_with_QHBOXLayout)
* [Nested Layouts](#Nested_Layouts)
* [Bug report Form](#Bug_report_Form)
* [Grid Layout](#Grid_Layout)

#### <span style="color:blue">1-Experimenting with QHBOXLayout</span>  {#Experimenting_with_QHBOXLayout}
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
### <span style="color:blue">2-Nested Layouts</span>  {#Nested_Layouts}
```cpp
#include "mainwindow.h"

#include <QApplication>
#include<QWidget>
#include<QLabel>
#include<QLineEdit>
#include<QPushButton>
#include<QCheckBox>
#include<QHBoxLayout>
#include<QVBoxLayout>
#include<QGridLayout>
#include<QGroupBox>
#include<QLCDNumber>
#include<QColor>
#include<QLabel>
#include<QLineEdit>
#include<QSpacerItem>


class window:public QWidget{

  //constructeur
protected:
    QHBoxLayout *mainlayout;
    QVBoxLayout *leftlayout;
    QHBoxLayout *topleftlayout;
    QVBoxLayout *rightlayout;
    QLabel *name;
    QLineEdit *edit;
    QPushButton *search;
    QPushButton *close;
    QCheckBox *box;
    QCheckBox *box1;



public:
    window(QWidget *parents=nullptr):QWidget(parents){    
        setWindowTitle("Nested layout");
        mainlayout = new QHBoxLayout();
        leftlayout = new QVBoxLayout();
        topleftlayout = new QHBoxLayout();
        rightlayout = new QVBoxLayout();
        setLayout(mainlayout);
        mainlayout->addLayout(leftlayout);
        leftlayout->addLayout(topleftlayout);
        mainlayout->addLayout(rightlayout);
        leftlayout->addStretch(40);
        leftlayout->setSpacing(30);
        name =new QLabel("Name:");
        edit=new QLineEdit;
        topleftlayout->addWidget(name);
        topleftlayout->addWidget(edit);
        box=new QCheckBox("match case");
        box1=new QCheckBox("Search backward");
         leftlayout->addWidget(box);
         leftlayout->addWidget(box1);
        search=new QPushButton;
        close=new QPushButton;
        search=new QPushButton("Search");
        close=new QPushButton("Close");
        rightlayout->addWidget(close);
        rightlayout->addWidget(search);
        rightlayout->addStretch(40);

}
};
```
```cpp
 int main(int argc, char *argv[])
    {
        QApplication a(argc, argv);

    auto *p=new window();

        p->show();

        return a.exec();
    }
```
here is the following form:

![imagges](https://user-images.githubusercontent.com/93833171/140626490-565e104b-ed09-44e1-8f9c-9aa8248a3bb3.PNG)


### <span style="color:blue">3-Bug report Form</span>   {#Bug_report_Form}
*Before starting work, we need to know some necessary libraries in order to complete this work:*
Like,QFormlayout :This sets children widgets in a two-column form with labels in the left column and input fields in the right column.

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
### <span style="color:blue">4-Grid Layout</span> {#Grid_Layout}

 **QGridLayout** lays out widgets in cells by dividing the available space into rows and columns.
 QGridLayout takes the space made available to it (by its parent layout or by the parentWidget()), divides it up into rows and columns, and puts each widget it manages into the correct cell. 
 If the GridLayout is resized, all items in the layout will be rearranged. It is similar to the widget-based QGridLayout. All visible children of the GridLayout element will belong to the layout.

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
        
      for (int i=10;i>0 ;i-- ) {//This loop stores numbers in a variable (Grid button) with difference index after converting them from integer to strings and putting them in a pushbutton.   //(9-i)
          gridbutton[i]=new QPushButton(QString::number(i));
          
gridlayout->addWidget(gridbutton[i],((9-i)/3), (i-1)%3);//And here you put the numbers stored in the variable into a form by placing each number in a specific place in a specific order. 
 //addWidget(QWidget *widget, int row=(9-i)/3 , int column=(i-1)%3)  To start from the top right


            }
      gridlayout->addWidget(gridbutton[0]);
        enter = new QPushButton("Enter");
      gridlayout->addWidget(enter, 3, 1,1,2);
}
};

```

```cpp
//its present just how to show the window
int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
window p;
p.show();
    return a.exec();
}
```
 <span style="color:black">here is the following form:</span>
 
 ![2021-11-06 18_56_09-CS311 _ Signal and Slots](https://user-images.githubusercontent.com/93819249/140619234-62baf751-ad69-4ea7-937d-14a3e629db99.png)
 
 
 
 
 <span style="color:orange"> realized by : SAID EL OUARDI, ADIL ERAAD</span> 
 
 
 
 
> Someone did really his homework. Really well done! Pefect grade
> Since you used **githubpages** you should share the following link `https://ashellos.github.io/C-GUI-Programming-with-QT-PJ2/`
