# Homework for the course
## Collections
### Compare time between different operations:
* ArrayList and LinkedList (insertion at the end, insertion at the beginning or middle, deleting, iteration)
* ArrayList/LinkedList and HashMap/HashSet (search)
* HashMap/HashSet vs TreeMap/TreeSet (search)
```java
public class Example {
    public static void main(String[] args) {
        // filling collections
        
        LocalDateTime start = LocalDateTime.now();

        // your operations here

        LocalDateTime end = LocalDateTime.now();
        long difference = ChronoUnit.MILLIS.between(start, end);

        System.out.println("Difference = " + difference);
    }
}
```
You can use different time units, check ChronoUnit for it. For searching also try to use more complex types like Strings 
or your own complex class (For generating random strings you can use: https://mvnrepository.com/artifact/org.apache.maven.surefire/surefire-shared-utils, or try to write your own generator).
Complex class example (don't forget to override hashCode and equals methods): 
```java
public class ComplexObject {
    private String name;
    private String differentName;
    private List<String> names;
    private int count;
    private int[] values;
    private SomeAnotherClass anotherClass;
    // other fields
}
```
### *** Try to write your own collections with hierarchy (Task for the future)
## Generics
### Pair class
Try to write generic Pair class with basic methods like equals, toString, etc.
```java
public class Example {
    public static void main(String[] args) {
        Pair<String, Integer> firstPair = new Pair<>("Hello World", 10);
        Pair<String, Integer> secondPair = new Pair<>("Bye World", 50);

        boolean equals = firstPair.equals(secondPair);
        String format = "First pair: %s and second pair: %s are equals: %s";

        System.out.println(String.format(format, firstPair, secondPair, equals));
    }
}
```
### * Read about "type erasure" (стирание типов)
## Generic & Collections
### List wrapper
Write generic list wrapper. Methods that the wrapper should contain:
```java
public abstract class ListWrapper<T> {
    /**
     * Add other collection to the current list 
     * @param otherCollection
     */
    public abstract void addOtherCollection(Collection<? extends T> otherCollection);

    /**
     * Remove elements contained in the incoming collection
     * @param collection
     * @return count deleted elements
     */
    public abstract int removeElementsByCollection(Collection<? extends T> collection);

    /**
     * @param collection
     * @return count elements contained in the list and in the incoming collection
     */
    public abstract int countDuplicates(Collection<? extends T> collection);

    /**
     * @return existing list
     */
    public abstract List<T> getList();

    /**
     * @param index
     * @return element by index from list
     */
    public abstract T getElement(int index);

    /**
     * @return beauty string by list
     */
    public abstract String beautyString();
    
    /**
     * Create ListWrapper with incoming elements
     * @param elements
     * @return ListWrapper by elements
     * @param <E>
     */
    public static <E> ListWrapper<E> fromElements(E... elements) {}
}
```
