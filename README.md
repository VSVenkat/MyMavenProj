# Multithreading

1. Single Task applications
2. Multi task applications

#### Single task applications

An application which performs only one operation at a time is single task application

#### Multi Task application

1. Threadbased (Windows)
2. Process based(Unix)

1. Simultaneous execution of multiple operations is called multi tasking.
2. Multitasking allows several activities to occur concurrently on the computer.
3. A distintion is made between 
- Threadbased Multitasking
- Processbased Multitasking

###### Advantages of multitasking

1. Allows to utilize CPU idle time effectively.
2. Increases the efficiency of the program/application.
3. Sharing resources.

###### What is process?

- A process is an instance of program.
- Whenever we execute a program a process is created.
- Process based multitasking , which allows multiple process to run concurrently on computer, for example : while we are working on spreadsheet we are allowed to also work on the word processor
- Thread based multitasking, which allows parts of the same program to run concurrently on the computer. A familar example is while we are printing the word document, the formatting of the text is also happening concurrently.
- This will only be fesable if two tasks are performed by two independent paths of execution at runtime

###### Synchronized methods

1. Synchronized is a modifier or a keyword used to define method
2. A method which is defined using the synchronized keyword is called synchronized method
3. If a thread invoke synchronized method it will aquire object lock.
4. Default value of lock is false. when we call t1.start() then it calls run() method.
5. It allows to develop thread safe applications.

```
Syntax : 

synchronized return_type method_name(parameters)
{
  //statements;
}
```
Example :
```
public class Printer{
  synchronized void print(String msg){
    for(int i=0;i<10;i++){
      System.out.println(msg);
    }
  }
}

public class PriterThread extends Thread{
  Printer p;
  String msg;
  PrinterThread(Printer p, String msg){
    this.p = p;
    this.msg = msg;
  }
  
  public void run(){
    p.print(msg);
  }
}

public class PrinterDemo{
  public static void main(String args[]){
    Printer p = new Printer();
    PrinterThread t1 = new PrinterThread(p, "thread1");
    PrinterThread t2 = new PrinterThread(p, "thread2");
    t1.start();
    t2.start();
  }
}
```

###### Synchronized block

Synchronized block places lock for the specified block where as Synchronized method places lock for the entire method.
###### Synchronized statements 
Synchronized statements are executed only after aquiring lock for the object or the class referenced in the synchronized statement

Example : 


```
class Bus{
  private int seats;
  Bus(){
    seats = 10;
  }
  synchronized void reverse(int n){
    if(seats < n){
      System.out.println("Seats are not available");
    }else{
      seats = seats - 1;
      System.out.println("Seats are avaiable");
    }
  }
}
class BusThread extends Thread{
  Bus b;
  int n;
  BustThread(Bus b, int n){
    this.b = b;
    this.n = n;
  }
  public void run(){
    b.reverse(n);
  }
}
public class BusDemo{
  public static void main(String args[]){
    Bus b = new Bus();
    
    BusThread t1 = new BusThread(b,2);
    BusThread t2 = new BusThread(b,2);
    t1.start();
    t2.start();
  }
}
```
Note : 
- If a method is declared with modifier as synchronized then that method is executed squencially by multiple threads.
- when the run() method is calling the synchronized method then lock value becomes true and when the run method returns then the lock value becomes false
- If we declare block of statements as synchronized then only those block of statements will be executed sequencially.
- If method is static than lock is obtained on the class
- If method is instance method then lock is obtained on the object.






