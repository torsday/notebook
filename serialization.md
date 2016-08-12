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
