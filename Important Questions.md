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
