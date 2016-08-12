# Serialization

*From: [StackOverflow](http://stackoverflow.com/questions/447898/what-is-object-serialization)*

> Serialization is the conversion of an object to a series of bytes, so that the object can be easily saved to persistent storage or streamed across a communication link. The byte stream can then be deserialized - converted into a replica of the original object.

---

## [StackOverflow: What is Serializable? What does this mean?](http://stackoverflow.com/questions/3753413/what-is-serializable-what-does-this-mean)

```java
public class ExampleEntity implements Serializable
{
     @Id
     private long id;
     private int fieldInt;
     private long fieldLong;
     private String fieldString;
 }
```


> It means that the class can be serialized. This means that it can be converted into an stream of 0's and 1's and be sent to other service, like a webservice or and ORM (hibernate) or whatever. Then this service knows how store the stream.

> Also, your program can receive a serialized class and create an instance for it from the stream of 0's and 1's.

> It's the way to "save" instances of classes and "restore" them at any other moment in time.

> More info at

>  - http://download.oracle.com/javase/6/docs/api/java/io/Serializable.html
 - http://en.wikipedia.org/wiki/Serialization

> To be able to make a class serializable, you must implement the interface "Serializable".

>  - **Why so**? Because when the moment to serialize a class arrive, the function `writeObtject` will be called to convert the object into bytes. On the other hand, when you have the bytes and you want to get the instance of the class, the function `readObject` will be called.

>
 - **Why is not automatic? A variable value it's already represented by bytes.** Because the problem comes for example when a class holds instances of other classes. What do you do? You serialize the other classes as well? You just keep the reference address? It's pretty complex and it may be dependant on your type of project and design.

---

Another answer from a duplicate question: *From: [StackOverflow: What is object serialization?](http://stackoverflow.com/questions/447898/what-is-object-serialization/448233#448233)*


> You can think of serialization as the process of converting an object instance into a sequence of bytes (which may be binary or not depending on the implementation).

> It is very useful when you want to transmit one object data across the network, for instance from one JVM to another.

> In Java, the serialization mechanism is built into the platform, but you need to implement the *Serializable* interface to make an object serializable.

> You can also prevent some data in your object from being serialized by marking the attribute as *transient*.

> Finally you can override the default mechanism, and provide your own; this may be suitable in some special cases. To do this, you use one of the [hidden features in java][1].


> It is important to notice that what gets serialized is the "value" of the object, or the contents, and not the class definition. Thus methods are not serialized.


> Here is a very basic sample with comments to facilitate its reading:

```java
import java.io.*;
import java.util.*;

// This class implements "Serializable" to let the system know
// it's ok to do it. You as programmer are aware of that.
public class SerializationSample implements Serializable {

    // These attributes conform the "value" of the object.

    // These two will be serialized;
    private String aString = "The value of that string";
    private int    someInteger = 0;

    // But this won't since it is marked as transient.
    private transient List<File> unInterestingLongLongList;

    // Main method to test.
    public static void main( String [] args ) throws IOException  {

        // Create a sample object, that contains the default values.
        SerializationSample instance = new SerializationSample();

        // The "ObjectOutputStream" class have the default
        // definition to serialize an object.
        ObjectOutputStream oos = new ObjectOutputStream(
                               // By using "FileOutputStream" we will
                               // Write it to a File in the file system
                               // It could have been a Socket to another
                               // machine, a database, an in memory array, etc.
                               new FileOutputStream(new File("o.ser")));

        // do the magic
        oos.writeObject( instance );
        // close the writing.
        oos.close();
    }
}
```

> When we run this program, the file "o.ser" is created and we can see what happened behind.

> If we change the value of: **someInteger** to, for example **Integer.MAX_VALUE**, we may compare the output to see what the difference is.

> Here's a screenshot showing precisely that difference:

![alt text][2]

*<sub>Can you spot the differences? ;)</sub>*

> There is an additional relevant field in Java serialization: The [serialversionUID][3] but I guess this is already too long to cover it.


  [1]: http://stackoverflow.com/questions/15496/hidden-features-of-java/142676#142676
  [2]: http://i.stack.imgur.com/oIVA5.png
  [3]: http://www.google.com/search?q=serialversionUID
