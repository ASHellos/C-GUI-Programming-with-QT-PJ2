

# Cpp GUI Programming with QT HW2:Part2

![imageqtc++](https://user-images.githubusercontent.com/93833171/142740904-ae7f6458-f497-47b1-b81f-f530250d112c.png)
 * * *
# <span style="color:red">Introduction:</span>

  in this second part follows up to add interactive functionality to the calculator widgets written in the previous homework. The goal is to use **Signals** and **Slots** to simulate a basic calculator behavior. The supported operations are *, +, -, /.

> **Signal** : this is a message sent by a widget when an event occurs. 
            
              example: we clicked on a button.
> **Slot** : this is the function that is called when an event has occurred. It is said that the signal calls the slot. Concretely, a slot is a method of a class. 
            
              example:The quit() slot of the QApplication class invokes the termination of the program.

and at the end we will use the **QTimer** to simulate a traffic light .     
      
> **QTimer** : QTimer can also be used to request the execution of a function as soon as the event loop has processed all other pending events.
 * * *
 * * *
