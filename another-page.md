
![imageqtc++](https://user-images.githubusercontent.com/93833171/142740904-ae7f6458-f497-47b1-b81f-f530250d112c.png)
 * * *
# <span style="color:red">Introduction:</span>

   in this second part follows up to add interactive functionality to the calculator widgets written in the previous homework. The goal is to use **Signals** and **Slots** to simulate a basic calculator behavior. The supported operations are *, +, -, /...etc.

> **Signal** : this is a message sent by a widget when an event occurs. 
            
              example: we clicked on a button.
              
              
              
> **Slot** : this is the function that is called when an event has occurred. It is said that the signal calls the slot. Concretely, a slot is a method of a class. 
            
              example:The quit() slot of the QApplication class invokes the termination of the program.

and at the end we will use the **QTimer** to simulate a traffic light .     
      

 * * *
 * * *

# <span style="color:red"> Summary:</span>
 * <span style="color:green"> Calculator</span>

 * <span style="color:green"> Traffic Light</span>

* * *
Now we'll start wby:**Calculator**

<span style="color:orange">main.cpp</span>
```cpp
#include "calculator.h"

#include <QApplication>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    Calculator w;
    w.setWindowTitle("Calculator");
    w.resize(500,500);
    w.show();
    return a.exec();
}
```
* *  *
here **Traffic Light**

<span style="color:orange">main.cpp</span>

```cpp
#include <QApplication>
#include "trafficlight.h"

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);


    //Creating the traffic light
    auto light = new TrafficLight;


    //showing the trafic light
    light->show();

    return a.exec();
}

```

<span style="color:orange">trafficlight.cpp</span>

```cpp
TrafficLight::TrafficLight(QWidget * parent): QWidget(parent){
    //Creatign the widgets
    createWidgets();
    //place Widgets
    placeWidgets();
}

//our createwidgets() function
void TrafficLight::createWidgets()
{
  QTime currentTime = QTime::currentTime();

  redlight = new QRadioButton;

  //this for the red color
  redlight->setEnabled(false);
  redlight->toggle();
  //redlight->isChecked();
  redlight->setStyleSheet("QRadioButton::indicator:checked { background-color: red;}");

  //this for the yellow color
  yellowlight = new QRadioButton;
  yellowlight->setEnabled(false);
  //yellowlight->toggle();
  yellowlight->setStyleSheet("QRadioButton::indicator:checked { background-color: yellow;}");

  //this for the green color
  greenlight = new QRadioButton;
  greenlight->setEnabled(false);
  //greenlight->toggle();
  greenlight->setStyleSheet("QRadioButton::indicator:checked { background-color: green;}");

  //here we add each element of the colors at the end ofQradiobutton
  lights.append(redlight);
  lights.append(yellowlight);
  lights.append(greenlight);

  index = 0;
  //here you want to change the value that exists between startTimer for example : startTimer(500)
  //starting the timer with an interval in milliseconds
  startTimer(200);
}

//our placeWidgets() function
void TrafficLight::placeWidgets()
{

  // Placing the widgets

  auto layout = new QVBoxLayout;//our QVboxlayout
  layout->addWidget(redlight);//we added redlight to layout
  layout->addWidget(yellowlight);//we added yellowight to layout
  layout->addWidget(greenlight);//we added greenlightto layout
  setLayout(layout);
}

void TrafficLight::timerEvent(QTimerEvent *e)
{

index = (index + 1)%3;
lights[index]->toggle();
    currentTime++;
    //if the yellow-light is on(checked) and pass his 4 second  active the redlight and initiate the currenttime 0

    if(redlight->isChecked()&& currentTime==4){
        yellowlight->toggle();
    currentTime=0;
    }
    //same thing for the yellow color
    if(yellowlight->isChecked()&& currentTime==3){
        greenlight->toggle();
    currentTime=0;
    }
    //same thing for the green color
    if(greenlight->isChecked()&& currentTime==1){
        redlight->toggle();
    currentTime=0;
    }
}

//our keyPressEvent() function
void TrafficLight::keyPressEvent(QKeyEvent *e){

//    if(e->key()==Qt::Key_Escape)
//        qApp->exit;
//    if(e->key()==Qt::Key_R)
//        index=0;
//    lights[index]->toggle();
//    if(e->key()==Qt::Key_G)
//        index=1;
//    lights[index]->toggle();
//    if(e->key()==Qt::Key_Y)
//        index=2;
//    lights[index]->toggle();

}
```
<span style="color:orange">trafficlight.h</span>
```h
#ifndef TRAFFIC_LIGHT_H
#define TRAFFIC_LIGHT_H

#include <QWidget>
#include <QLabel>
#include <QTime>
#include <QVector>
#include<QKeyEvent>

class QRadioButton;

class TrafficLight: public QWidget{
  Q_OBJECT

public:

  TrafficLight(QWidget * parent = nullptr);
  void timerEvent(QTimerEvent *e);
  void keyPressEvent(QKeyEvent *e);

protected:
     void createWidgets();
     void placeWidgets();

private:
     //our Qradiobutton
  QRadioButton * redlight;
  QRadioButton * yellowlight;
  QRadioButton * greenlight;
  //our qlable
  QLabel * timeLabel;
  //our vector of QRadioButton
  QVector <QRadioButton*> lights;
  int index ;
  int times[3]{4,1,2};
  int currentTime;

};


#endif
```
