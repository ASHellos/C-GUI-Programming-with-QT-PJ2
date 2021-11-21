
![imageqtc++](https://user-images.githubusercontent.com/93833171/142740904-ae7f6458-f497-47b1-b81f-f530250d112c.png)
 * * *
# <span style="color:red">Introduction:</span>

   in this second part follows up to add interactive functionality to the calculator widgets written in the previous homework. The goal is to use **Signals** and **Slots** to simulate a basic calculator behavior. The supported operations are *, +, -, /.

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
Now we'll start wby:Calculator
main.cpp
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
