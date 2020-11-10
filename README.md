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
  Printer p = new Printer();
  PrinterThread t1 = new PrinterThread(p, "thread1");
  PrinterThread t2 = new PrinterThread(p, "thread2");
  t1.start();
  t2.start();
}
```







