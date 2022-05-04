1)HashMap in Java works on hashing principles. It is a data structure that allows us to store object and retrieve it in constant time O(1) provided we know the key. In hashing, hash functions are used to link keys and values in HashMap. Objects are stored by the calling put(key, value) method of HashMap and retrieved by calling the get(key) method. When we call the put method, the hashcode() method of the key object is called so that the hash function of the map can find a bucket location to store the value object, which is actually an index of the internal array, known as the table.

Read more: https://javarevisited.blogspot.com/2011/02/how-hashmap-works-in-java.html#ixzz7SJfliAKQ


2)JVM architecture.
JVM Architecture:-

JVM (Java Virtual Machine) is an abstract machine. It is a specification that provides runtime environment in which java bytecode can be executed.
JVM provides the following features:-
1.Loads code
2.Verifies code
3.Executes code
4.Provides runtime environment

1) Classloader
Classloader is a subsystem of JVM which is used to load class files. Whenever we run the java program, it is loaded first by the classloader. There are three built-in classloaders in Java.

Bootstrap ClassLoader: This is the first classloader which is the super class of Extension classloader. It loads the rt.jar file which contains all class files of Java Standard Edition like java.lang package classes, java.net package classes, java.util package classes, java.io package classes, java.sql package classes etc.
Extension ClassLoader: This is the child classloader of Bootstrap and parent classloader of System classloader. It loades the jar files located inside $JAVA_HOME/jre/lib/ext directory.
System/Application ClassLoader: This is the child classloader of Extension classloader. It loads the classfiles from classpath. By default, classpath is set to current directory. You can change the classpath using "-cp" or "-classpath" switch. It is also known as Application classloader.
//Let's see an example to print the classloader name  
public class ClassLoaderExample  
{  
    public static void main(String[] args)  
    {  
        // Let's print the classloader name of current class.   
        //Application/System classloader will load this class  
        Class c=ClassLoaderExample.class;  
        System.out.println(c.getClassLoader());  
        //If we print the classloader name of String, it will print null because it is an  
        //in-built class which is found in rt.jar, so it is loaded by Bootstrap classloader  
        System.out.println(String.class.getClassLoader());  
    }  
}     
Test it Now
Output:

sun.misc.Launcher$AppClassLoader@4e0e2f2a
null
These are the internal classloaders provided by Java. If you want to create your own classloader, you need to extend the ClassLoader class.

2) Class(Method) Area
Class(Method) Area stores per-class structures such as the runtime constant pool, field and method data, the code for methods.

3) Heap
It is the runtime data area in which objects are allocated.

4) Stack
Java Stack stores frames. It holds local variables and partial results, and plays a part in method invocation and return.

5) Program Counter Register
PC (program counter) register contains the address of the Java virtual machine instruction currently being executed.

6) Native Method Stack


7) Execution Engine
It contains:


A virtual processor
Interpreter: Read bytecode stream then execute the instructions.
Just-In-Time(JIT) compiler: It is used to improve the performance. JIT compiles parts of the byte code that have similar functionality at the same time, and hence reduces the amount of time needed for compilation. Here, the term "compiler" refers to a translator from the instruction set of a Java virtual machine (JVM) to the instruction set of a specific CPU.
8) Java Native Interface
Java Native Interface (JNI) is a framework which provides an interface to communicate with another application written in another language like C, C++, Assembly etc. Java uses JNI framework to send output to the Console or interact with OS libraries.
It contains all the native methods used in the application.

********************************************************************************************************************
3)Garbage Collection in java
Garbage collection in Java is the process by which Java programs perform automatic memory management. Java programs compile to bytecode that can be run on a Java Virtual Machine, or JVM for short. When Java programs run on the JVM, objects are created on the heap, which is a portion of memory dedicated to the program. 

But in Java, the programmer need not care for all those objects which are no longer in use. Garbage collector destroys these objects. The main objective of Garbage Collector is to free heap memory by destroying unreachable objects. The garbage collector is the best example of the Daemon thread as it is always running in the background. 

How Does Garbage Collection in Java works?
Java garbage collection is an automatic process. Automatic garbage collection is the process of looking at heap memory, identifying which objects are in use and which are not, and deleting the unused objects. An in-use object, or a referenced object, means that some part of your program still maintains a pointer to that object. An unused or unreferenced object is no longer referenced by any part of your program. So the memory used by an unreferenced object can be reclaimed. The programmer does not need to mark objects to be deleted explicitly. The garbage collection implementation lives in the JVM. 



Ways to make an object eligible for Garbage Collector
Even though the programmer is not responsible for destroying useless objects but it is highly recommended to make an object unreachable(thus eligible for GC) if it is no longer required.
There are generally four ways to make an object eligible for garbage collection.
Nullifying the reference variable
Re-assigning the reference variable
An object created inside the method
Island of Isolation


Island of Isolation
Ways for requesting JVM to run Garbage Collector
Once we make an object eligible for garbage collection, it may not destroy immediately by the garbage collector. Whenever JVM runs the Garbage Collector program, then only the object will be destroyed. But when JVM runs Garbage Collector, we can not expect.
We can also request JVM to run Garbage Collector. There are two ways to do it : 
Using System.gc() method: System class contain static method gc() for requesting JVM to run Garbage Collector.
Using Runtime.getRuntime().gc() method: Runtime class allows the application to interface with the JVM in which the application is running. Hence by using its gc() method, we can request JVM to run Garbage Collector.
There is no guarantee that any of the above two methods will run Garbage Collector.
The call System.gc() is effectively equivalent to the call : Runtime.getRuntime().gc()

Just before destroying an object, Garbage Collector calls finalize() method on the object to perform cleanup activities. Once finalize() method completes, Garbage Collector destroys that object.
finalize() method is present in Object class with the following prototype.
protected void finalize() throws Throwable


Based on our requirement, we can override finalize() method for performing our cleanup activities like closing connection from the database. 

The finalize() method is called by Garbage Collector, not JVM. However, Garbage Collector is one of the modules of JVM.
Object class finalize() method has an empty implementation. Thus, it is recommended to override the finalize() method to dispose of system resources or perform other cleanups.
The finalize() method is never invoked more than once for any object.
If an uncaught exception is thrown by the finalize() method, the exception is ignored, and the finalization of that object terminates.



Advantages of Garbage Collection in Java
The advantages of Garbage Collection in Java are:

It makes java memory-efficient because the garbage collector removes the unreferenced objects from heap memory.
It is automatically done by the garbage collector(a part of JVM), so we don’t need extra effort.
***********************************************************************************************************
A Wrapper class is a class which contains the primitive data types (int, char, short, byte, etc). In other words, wrapper classes provide a way to use primitive data types (int, char, short, byte, etc) as objects. These wrapper classes come under java. util package.
