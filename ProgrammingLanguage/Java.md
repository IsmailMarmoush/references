# Lists

* https://github.com/akullpp/awesome-java

## Java Books

* ~~Servlet Specs~~
* ~~OCJP~~
* ~~OCEJWCD by charles lyons~~
* ~~Head First Servlets~~
* ~~OCA 8~~
* ~~OCP 8~~
* Functional Programming for Java Developers, Dean wampler
* Effective Java
* Java Generics
* Java Job Interview
* Java Performance 2012
* Java Reflection
* Java Web Services
* Covert Java
* Art of Java web dev
* Building Java

* Money
    * https://www.joda.org/joda-money/userguide.html
    * https://www.baeldung.com/java-money-and-currency
    * https://www.openbanking.org.uk/
        * https://github.com/OpenBankingUK
        * https://github.com/OpenBankProject/OBP-API/wiki/REST-API-V1.2.1
* Hot Deployment
    * [Hot Deployment variants](http://stackoverflow.com/questions/17419900/what-are-the-differences-between-the-various-java-plugins-for-hot-class-reloadin/17642585#17642585)

## General Tips

* catch with | makes e final
* The old catch which is without |, allows reassignment of `e`
* `float b=100;` doesn't produce error but `Float b = 100;`
* If Equal is true, hashcode must be true
* The index of an enum may change when you recompile the code and should not be used for comparison.
* Inner classes are not allowed to contain static methods or static variables.
    * Only nested static classes are permitted to contain statics.
* Eventually final: Java 8 doesn't require variable to be final if it's eventually final
* `instanceof` will be true for all super classes
* Class that has all constructors private is somehow final
* `volatile` prevents compiler when it tries to optimize the code such that the object is accessed before it is finished
  being constructed.
* Static methods in interface must have braces
* you cannot override a static method with a non-static method and vice-versa.

## JVM

* https://bell-sw.com/announcements/2020/10/28/JVM-in-Linux-containers-surviving-the-isolation/
* Profiling Tools for Java:
    * Guessing were the bottleneck is, is not as efficient as simply profiling to find it.
    * Types of profiling include: method profiling, allocation profiling, lock profiling, GC profiling, DB Query
      profiling.
    * Profilers include: async-profiler (alone or with jfrsync), JFR, VisualVM (but this last is affected by safepoint
      bias).
    * There are 2 main types of profilers: instrumenting profilers which change the bytecode to add in timing code (
      accurate but slows execution and can distort the optimizations in the application); and sampling profilers which
      get the stack trace at regular intervals (fast but approximate).
    * Safepoint bias is where profilers only report data at safepoints in the JVM (where all the application threads are
      paused) which means you get inaccurate data.
    * There are 3 types of JVM sampling profilers: GetCallTrace based (eg VisualVM, these are affected by safepoint
      bias); AsyncGetCallTrace based (eg async-profiler); JFR based (eg JMC).

## Volatile Keyword

http://stackoverflow.com/questions/2423622/volatile-vs-static-in-java
Declaring a static variable in Java, means that there will be only one copy, no matter how many objects of the class are
created. The variable will be accessible even with no Objects created at all. However threads may have locally cached
values of it. When a variable is volatile and not static, there will be one variable for each Object. So on the surface
it seems there is no difference from a normal variable, and totally different from static. However, even with Object
fields, a thread may cache a variable value locally. This means that if two threads update a variable of the same Object
concurrently, and the variable is not declared volatile, there could be a case in which one of the thread has in cache
an old value. Even if you access a static values through multiple thread each thread can have it's local cached copy! To
avoid this you can declare the variable as static volatile and this will force the thread to read each time the global
value. However, volatile is not a substitute for proper synchronisation! For instance:

```
private static volatile int counter = 0;
private void concurrentMethodWrong() {
         counter = counter + 5;
         //do something
         counter = counter - 5;
}
```

Executing concurrentMethodWrong concurrently many times may lead to a final value of counter different from zero! To
solve the problem, you've to implement a lock:
private static final Object counterLock = new Object();

```
private static volatile int counter = 0;
private void concurrentMethodRight() {
     synchronized (counterLock) {
         counter = counter + 5;
     }
     //do something
     synchronized (counterLock) {
         counter = counter - 5;
     }
}
```

Or use the AtomicInteger class.

http://stackoverflow.com/questions/106591/do-you-ever-use-the-volatile-keyword-in-java
volatile has semantics for memory visibility. Basically, the value of a volatile field becomes visible to all readers (
other threads in particular) after a write operation completes on it. Without volatile, readers could see some
non-updated value. To answer your question: Yes, I use a volatile variable to control whether some code continues a
loop. The loop tests the volatile value and continues if it is true. The condition can be set to false by calling a "
stop" method. The loop sees false and terminates when it tests the value after the stop method completes execution. The
book "Java Concurrency in Practice," which I highly recommend, gives a good explanation of volatile. This book is
written by the same person who wrote the IBM article that is referenced in the question (in fact, he cites his book at
the bottom of that article). My use of volatile is what his article calls the "pattern 1 status flag."
If you want to learn more about how volatile works under the hood, read up on the Java memory model. If you want to go
beyond that level, check out a good computer architecture book like Hennessy & Patterson and read about cache coherence
and cache consistency.

## Enums

* Enum ordinal can't be used in Switch case
* Enums are required to have a semicolon after the list of values if there is anything else in the enum.
* Enums are not allowed to have public constructor

## Immutable objects

1. Use a constructor to set all properties of the object.
2. Mark all of the instance variables private and final .
3. Don’t define any setter methods.
4. Don’t allow referenced mutable objects to be modified or accessed directly.
5. Prevent methods from being overridden

## Equal Method Contract (ReSTC)

* It is **reflexive**: For any non‐null reference value x , x.equals(x) should return true .
* It is **symmetric**: For any non‐null reference values x and y , x.equals(y) should return true if and only if
  y.equals(x) returns true .
* It is **transitive**: For any non‐null reference values x , y , and z , if x.equals(y) returns true and y.equals(z)
  returns true , then x.equals(z) should return true .
* It is **consistent**: For any non‐null reference values x and y , multiple invocations of x.equals(y) consistently
  return true or consistently return false , provided no information used in equals comparisons on the objects is
  modified.
* For any non‐null reference value x , x.equals(null) should return false .

## Switch

* int and Integer
* byte and Byte
* short and Short
* char and Character
* String
* enum values
* The variable must actually be marked as final. The new “effectively final” concept in Java 8 is insufficient.

## Strings

```
String s = "abcde ";
s.indexOf('e') // 4   idx=0
s.substring(2, 4) // cd  idx=0
s.replace('a', '1') // 1bcd   idx=1

StringBuilder b = new StringBuilder("12345-");
System.out.println(b.indexOf("-")); // 5

StringBuilder s = new StringBuilder("abcde");
s.insert(1, '-') // a-bcde          idx=0
s.delete(3, 4); // a-bde            idx=0  
s.substring(2, 4); // bd            idx=0     
```

## Literals

* long k= 2323L
* int octal= 017
* int hexa=0x23f or 0X23f
* int binary=0b01101 or 0B0101110
* double notByDecimal = 1000_.00; // DOES NOT COMPILE
* double annoyingButLegal = 1_00_0.0_0; // this one compiles

## Formatting

* `#` means to omit the position if no digit exists for it.
* 0 means to put a 0 in the position if no digit exists for it
* Germany uses a comma and the United States uses a period for the decimal point

```
// Java will round the last numbers DecimalFormat 
// and SimpleDateFormat use a constructor and 
// take a pattern format string as a parameter.
DecimalFormat df = new DecimalFormat("#00.00##"); 

double d = 1234567.437;
DecimalFormat one = new DecimalFormat("###,###,###.###");
System.out.println(one.format(d)); // 1,234,567.437

DecimalFormat two = new DecimalFormat("000,000,000.00000");
System.out.println(two.format(d)); // 001,234,567.43700

DecimalFormat three = new DecimalFormat("$#,###,###.##");
System.out.println(three.format(d)); // $1,234,567.44

DecimalFormat df = new DecimalFormat("#,000.0#");
double pi = 3.141592653; 
System.out.println(df.format(pi)); // 003.14
```

```
NumberFormat nf = NumberFormat.getInstance();
String one = "456abc";
String two = "-2.5165x10";
String three = "x85.3";
System.out.println(nf.parse(one)); // 456
System.out.println(nf.parse(two)); // -2.5165
System.out.println(nf.parse(three));// throws ParseException
```

```
helloByName=Hello, {0}
String format = rb.getString("helloByName");
String formatted = MessageFormat.format(format, "Tammy");
System.out.print(formatted);
```

## Inner Classes

### Member Inner classes

* Cannot declare static fields or methods
* Can access outer class members including private ones
* Inner inner = outer.new Inner();

### Local Inner Classes

* They have access to all fields and methods of the enclosing class.
* They do not have access to local variables of a method unless those variables are final or effectively final.
* In Java 8 variable doesn't have to be "final" but should be effectively final - meaning no assignments ever happen.

### Anonymous Inner Classes

* Can be defined in when declaring field, argument, or return.
* In Java 8 functional programming there is a shorter version

### Static Inner Classes

* The nesting creates a namespace because the enclosing class name must be used to refer to it.
* It can be made private or use one of the other access modifiers to encapsulate it.
* The enclosing class can refer to the fields and methods of the static nested class.

## Date Time

* LocalDate has toEpochDay() and toEpochSecond()
* LocalDateTime and ZonedDateTime have toEpochSecond() , which is the number of seconds since January 1, 1970.

### Period (for days)

* Doesn't work with LocalTime
* Max representation Y , minimum is D
* toString -> PnYnMnD

```
Period annually = Period.ofYears(1);
Period quarterly = Period.ofMonths(3);
Period everyThreeWeeks = Period.ofWeeks(3);
Period everyOtherDay = Period.ofDays(2);
Period everyYearAndAWeek = Period.of(1, 0, 7); // P1Y7D

Period wrong = Period.ofYears(1).ofWeeks(1);  //  VIP -> week
```

## Duration

* Doesn't work with LocalDate
* Maximum representation is H, Minimum is S
* toString ->  PTnHnMnS ISO-8601

```
Duration daily = Duration.ofDays(1); // PT24H
Duration hourly = Duration.ofHours(1); // PT1H
Duration everyMinute = Duration.ofMinutes(1);  // PT1M
Duration everyTenSeconds = Duration.ofSeconds(10); // PT1S
Duration everyMilli = Duration.ofMillis(1);  // PT0.001S
Duration everyNano = Duration.ofNanos(1); // PT0.000000001S

Duration daily = Duration.of(1, ChronoUnit.DAYS);
Duration hourly = Duration.of(1, ChronoUnit.HOURS);
Duration everyMinute = Duration.of(1, ChronoUnit.MINUTES);
Duration everyTenSeconds = Duration.of(10, ChronoUnit.SECONDS);
Duration everyMilli = Duration.of(1, ChronoUnit.MILLIS);
Duration everyNano = Duration.of(1, ChronoUnit.NANOS);

Duration d=Duration.ofDays(2).ofDays(3).ofHours(20); // 20H
```

### LocalTime

```
LocalTime one = LocalTime.of(5, 15);
LocalTime two = LocalTime.of(6, 30);
LocalDate date = LocalDate.of(2016, 1, 20);
System.out.println(ChronoUnit.HOURS.between(one, two)); // 1
System.out.println(ChronoUnit.MINUTES.between(one, two)); // 75
System.out.println(ChronoUnit.MINUTES.between(one, date)); // DateTimeException
```

### Instant

```
Instant instant = zonedDateTime.now();
Instant instant = zonedDateTime.toInstant() ; // 2015–05–25T15:55:00Z
Instant instant = Instant.ofEpochSecond(epochSeconds);
Instant nextDay = instant.plus(1, ChronoUnit.DAYS);

// Older stuff
LocalDateTime.ofInstant(date.toInstant(), ZoneId.systemDefault());
LocalDateTime.ofInstant(calendar.toInstant(),ZoneId.systemDefault());
LocalDateTime.ofEpochSecond(1465817690,0, ZoneOffset.UTC);

```

## Localisation

**Internationalization:** is the process of designing your program so it can be adapted. This involves placing strings
in a property file and using classes like DateFormat so that the right format is used based on user preferences. You do
not actually need to support more than one language or country to internationalize the program. Internationalization
just means that you can.

**Localization:** means actually supporting multiple locales.

```
System.out.println(Locale.GERMAN); // de
System.out.println(Locale.GERMANY); // de_DE

Locale myLocale = Locale.getDefault();
Locale myLocale = Locale.US;
Locale myLocale = new Locale("ru", "RU");

Locale l1 = new Locale.Builder()
.setLanguage("en")
.setRegion("US")
.build();

System.out.println(Locale.getDefault()); // en_US
Locale locale = new Locale("fr");
Locale.setDefault(locale);
// change the default
System.out.println(Locale.getDefault()); // fr

// Exa
df = DateFormat.getDateInstance(DateFormat.DEFAULT, Locale.UK);  
df.format(d);

```

## Exceptions

* try with resources makes elements final
* Resources are closed at the end of the try block and before any catch or finally block.
* Resources are not even accessible in the catch or finally block.
* When multiple exceptions are thrown, all but the first are called suppressed exceptions. The idea is that Java treats
  the first exception as the primary one and tacks on any that come up while automatically closing.
    * if the close() method throws an exception as well, then this exception is added to the original exception as a
      supressed exception.

#### Checked Exceptions

* Exception
* java.io.IOException
* java.io.FileNotFoundException
* java.io.NotSerializable
* java.text.ParseException
* java.sql.SQLException

#### Unchecked Exceptions

* java.lang.ArrayStoreException
* java.lang.IllegalStateException
* java.lang.UnsupportedOperationException
* java.time.DateTimeException
* java.util.MissingResourceException

```
// A multi-catch statement does not allow redundancy
catch (FileNotFoundException | IOException e) { } // DOES NOT COMPILE 
```

* A try-with-resources statement does not require a catch or finally block. A traditional try statement requires at
  least one of the two.
* The auto-closeable variables defined in the try-with-resources statement are implicitly final. Thus, they cannot be
  reassigned. **vip**
* Just like “regular” catch blocks, any runtime exception may be caught. However, only checked exceptions that have the
  potential to be thrown are allowed to be caught.
* Resources are closed after the try clause ends and before any catch / finally clauses.
* Resources are closed in the reverse order from which they were created.
* Remember that Java needs to be backward compatible. try and finally were both allowed to throw an exception long
  before Java 7. When this happened, the finally block took precedence. This behavior needs to continue. Since automatic
  resource management was new with Java 7, the try-with-resources part was allowed to behave differently. Regular
  finally blocks could not change.

#### Closeable extends AutoClossable

```
AutoCloseable#close () throws Exception
Closeable#close() throws IOException
```

## Assertions

* `java -ea:com.wiley.demos... my.programs.Main` The three dots means any class in the specified package or subpackages.
* **Internal Invariants** You assert that a value is within a certain constraint. assert x < 0 is an example of an
  internal invariant.
* **Class Invariants** You assert the validity of an object’s state. Class invariants are typically private methods
  within the class that return a boolean . The upcoming Rectangle class demonstrates a class invariant.
* **Control Flow Invariants** You assert that a line of code you assume is unreachable is never reached. The upcoming
  TestSeasons class demonstrates a control fl ow invariant.
* **Preconditions** You assert that certain conditions are met before a method is invoked.
* **Post Conditions** You assert that certain conditions are met after a method executes successfully.

## Generics and Collections

* What you can't do with generics:
    * new T() is not allowed because at runtime it would be new Object() .
    * Create an array of that static type. This one is the most annoying, but it makes sense because you’d be creating
      an array of Object s.
    * Call instanceof . This is not allowed because at runtime List<Integer> and List<String> look the same to Java
      thanks to type erasure.
    * Use a primitive type as a generic type parameter. This isn’t a big deal because you can use the wrapper class
      instead. If you want a type of int , just use Integer .
    * Create a static variable as a generic type parameter. This is not allowed because the type is linked to the
      instance of the class.
* Generic method optional syntax
    * `Box.<String>ship("package"); `
    * `Box.<String[]>ship(args);`
* Stack methods:
    * push()
    * peek(returns null if none)
    * pop(returns null if none)
* Queue methods: * throws exception
    * boolean add(E)*
    * E element()*
    * boolean offer()*
    * E remove()*
    * void push()
    * E peek()
    * E poll()
* collections.binarySearch(), collection should be in same order as comparator
* comparator -> compareTo, comparable-> compare
* There are four formats for method references:
    * Static methods
        * `Consumer<List<Integer>> lambda1 = l -> Collections.sort(l)`
    * Instance methods on a particular instance
        * String str="ABC"
        * `Predicate<String> lambda2 = s -> str.startsWith(s)`
    * Instance methods on an instance to be determined at runtime
        * `Predicate<String> lambda3 = s -> s.isEmpty()`
    * Constructors
        * `Supplier<ArrayList> methodRef4 = ArrayList::new;`
* Map#merge(k,v, BiFunction)  // Merges with current but with rules
    * BiFunction deals with 2 values
    * The mapping function is used only when there are two actual values to decide between, not when any of them is null
    * When it returns null `BiFunction<String, String, String> mapper = (v1, v2) -> null; `
        * If k exists , it will be removed
        * If k doesn't exist it will be added
* Map#computeIfPresent(k, mapper)
    * mapper deals with the key and value and returns a new value:
    * `BiFunction<String, Integer, Integer> mapper = (k, v) -> v + 1;`
    * `Integer jenny = counts.computeIfPresent("Jenny", mapper);`
    * returns the computed value or null
* Map#computeIfAbsent(k,mapper)
    * The functional interface runs only when the key isn’t present or is null :
    * `Function<String, Integer> mapper = (k) -> 1;`
    * `Integer jenny = counts.computeIfAbsent("Jenny", mapper); // 15`
    * `Integer sam = counts.computeIfAbsent("Sam", mapper); // 1`
    * `Integer tom = counts.computeIfAbsent("Tom", mapper); // 1`
      Notes

```
// ArrayList<String> is not compatible with List<String> in this case. Both the sides must have the same type.
Map<String, List<String>> stateCitiesMap = new HashMap<String, ArrayList<String>>(); 


```

## Functional Programming

### Functional Interfaces **VIP**

```
Supplier<T> 		 T 		get()
Consumer<T> 		 void 	accept(T)
BiConsumer<T, U> 	 void 	accept(T,U)
Predicate<T> 		 boolean test(T)
BiPredicate<T, U> 	 boolean test(T,U)
Function<T, R> 		 R 		apply(T)
BiFunction<T, U, R>  R 		apply(T,U)
UnaryOperator<T> 	 T 		apply(T)
BinaryOperator<T> 	 T 		apply(T,T)


		 			Intermediate Ops 	Terminal Opsf
-----------------------------------------------------
Useful pipeline? 		No					Yes

Executed upon 
method call? 			No 					Yes

Can exist multiple 
times in a pipeline? 	Yes 				No

Return type is a 
stream type? 			Yes 				No

Stream valid 
after call? 			Yes 				No




Method 			Infinite Streams 		Return 		Reduction
--------------------------------------------------------------
collect() 		Never terminate 		Varies 			Yes

reduce() 		Never terminate 		Varies 			Yes

count() 		Never terminate 		long 			Yes

min()/max() 	Never terminate 		Optional<T> 	Yes

forEach() 		Never terminate 		void 			No

allMatch()
/anyMatch()
/noneMatch() 	Sometimes terminates 	boolean 		No

findAny()
/findFirst() 	Terminates 				Optional<T> 	No

```

### reduce

```
T reduce(T identity, BinaryOperator<T> accumulator)
Optional<T> reduce(BinaryOperator<T> accumulator)
<U> U reduce(U identity, BiFunction<U,? super T,U> accumulator,BinaryOperator<U> combiner)
```

### Collect

```
// The combiner is in case  parallel processing of many collections
<R> R collect(Supplier<R> supplier, BiConsumer<R, ? super T> accumulator,
BiConsumer<R, R> combiner)
<R,A> R collect(Collector<? super T, A,R> collector)
```

### Printing a stream

```
Code 							Works with				Destructive
								Infinite Stream
-------------------------------------------------------------------								
s.forEach(System.out::println); No 							Yes

System.out.println(
s.collect(Collectors.toList())  
); 								No 							Yes

s.peek(System.out::println).count(); No 					No

s.limit(5).forEach(System.out::println); Yes 				Yes
```

### Primitive Streams and Primitive Functional Interfaces

* Only IntStream, LongStream, DoubleStream
* Only OptionalInt , OptionalLong, OptionalDouble
* There is a interface BooleanSupplier{ boolean getAsBoolean();}
* BiConsumer , BiPredicate , and BiFunction are not written

### Primitive Streams table **VIP**

```
Stream map mapToDouble mapToInt mapToLong
IntStream mapToObj map intToDouble mapToLong

Stream Function ToDoubleFunction ToIntFunction ToLongFunction
IntStream IntFunction IntToDoubleFunction IntUnaryOperator IntToLongFunction
```

### Primitive Stream Stats

```
private static int range(IntStream ints) {
	IntSummaryStatistics stats = ints.summaryStatistics();
	if (stats.getCount() == 0) throw new RuntimeException();
	return stats.getMax()—stats.getMin();
}
```

### Common functional interfaces for primitives

```
Functional Interfaces 			# Parameters 		Return Type 			Single Abstract Method
IntSupplier							0							int						getAsInt
IntConsumer						1							void						accept
IntPredicate							1							boolean				test
```

### Primitive-specific functional interfaces

```
ToIntFunction<T>                 1(T)                      int 						applyAsInt
ToIntBiFunction<T, U>          2(T,U)					int						applyAsInt
IntToDoubleFunction           1							double					applyAsDouble
IntToLongFunction				1							long						applyAsLong
ObjIntConsumer<T>				2 (T, int)				void						accept
```

### Collectors

```
averagingDouble(ToDoubleFunction f)
averagingInt(ToIntFunction f)
averagingLong(ToLongFunction f)								Double

counting() 													Long

groupingBy(Function f)
groupingBy(Function f,Collector dc)
groupingBy(Function f,Supplier s, Collector dc)				Map<K, List<T>>

joining()							
joining(CharSequence cs) 									String

maxBy(Comparator c)											Optional<T>
minBy(Comparator c) 

mapping(Function f,Collector dc) 							Collector

partitioningBy(Predicate p)			
partitioningBy(Predicate p,Collector dc) 					Map<Boolean,List<T>>

summarizingDouble(ToDoubleFunction f)						DoubleSummaryStatistics
summarizingInt(ToIntFunction f)								IntSummaryStatistics
summarizingLong(ToLongFunction f)							LongSummaryStatistics


summingDouble(ToDoubleFunction f) 							Double
summingInt(ToIntFunction f) 								Integer
summingLong(ToLongFunction f) 								Long

toList()													List
toSet() 													Set
toCollection(Supplier s) 									Collection

toMap(Function k, Function v)
toMap(Function k, Function v,BinaryOperator m)
toMap(Function k, Function v,BinaryOperator m, Supplier s)  Map
```

## Resource bundle

```
Zoo_en.properties
Zoo_fr.properties
ResourceBundle rb = ResourceBundle.getBundle("Zoo", locale);

# one comment
! another comment
key =
value\tafter tab
long = abcdefghijklm\
nopqrstuvwxyz
Printing out these two properties in a program gives us this:
value → after tab
abcdefghijklmnopqrstuvwxyz
```

### Properties

```
getProperty("key") Value null
getProperty("key", "default") Value "default"
```

### Java Resource Bundle

```
ResourceBundle.getBundle("name");
ResourceBundle.getBundle("name", locale);
```

### Resource bundle search

```
ResourceBundle.getBundle("Zoo", new Locale("en"));

// Matching
Zoo_fr_FR.java
Zoo_fr_FR.properties

// remove country
Zoo_fr.java
Zoo_fr.properties

// Check the default
Zoo_en_US.java
Zoo_en_US.properties

// remove country
Zoo_en.java
Zoo_en.properties

// no locale the default bundle
Zoo.java
Zoo.properties
```

### Resource bundle keys filling

```
Zoo_fr_FR.java: 		Zoo_fr_FR.java > Zoo_fr.java > Zoo.java
Zoo_fr.properties: 		Zoo_fr.properties > Zoo.properties

Note: Once a bundle is chosen, only resources in that hierarchy are
allowed.
```

## Concurrency

Thread.MIN_PRIORITY 1 Thread.NORM_PRIORITY 5 Thread.MAX_PRIORITY 10

* Thread.sleep() throws the checked InterruptedException
* shutdownNow() returns a List<Runnable> of tasks that were submitted to the thread executor but that were never started
* `use((Callable<Integer>)() -> {throw new IOException("");}); // COMPILES`
* `synchronized(this) `  is same as `private synchronized void blabla(){}`
* `synchronized(SheepManager.class)` is same as `public static synchronized void printDaysWork() {}`

### Locking

* we can only synchronize on an object that implements the Lock interface.
* The Lock framework ensures that once a thread has called the lock() method, all other threads that call lock() will
  wait until the thread that acquired the lock calls the unlock() method.
* it is considered a good code practice to put the unlock() method in a finally block
* If you attempt to release a lock that you do not have, you will get an exception at runtime in the form of an
  IllegalMonitorStateException .

## Locks

* https://dzone.com/articles/what-are-reentrant-locks

```
Lock lock = new ReentrantLock();
lock.unlock(); // Throws IllegalMonitorStateException at runtime
```

* overloaded try lock returns true as soon as the lock is acquired within the time specified, and it returns false after
  the time elapses.

```
if(lock.tryLock(10,TimeUnit.SECONDS)) {
```

* The unlock() method must be called the same number of times as the lock() method in order to release the lock.
* ReentrantLock(true); fairness is enabled and the longest waiting thread is guaranteed to obtain the lock the next time
  it is released.
* ReadWriteLock readWriteLock = new ReentrantReadWriteLock();
    * Lock lock =readWriteLock.readLock();
    * Lock lock =readWriteLock.writeLock();
    * When write lock is reach the readlock is also locked but when on readlock case it's as if it's not there.

### Liveness Issues: deadlock, starvation, and livelock.

#### Deadlock ??!

#### Starvation

Starvation occurs when a single thread is perpetually denied access to a shared resource or lock. The thread is still
active, but it is unable to complete its work as a result of other threads constantly taking the resource that they
trying to access.

#### Livelock ??!

#### Race Conditions

### Atomic Classes

**AtomicBoolean** A boolean value that may be updated atomically
**AtomicInteger** An int value that may be updated atomically
**AtomicIntegerArray** An int array in which elements may be updated atomically
**AtomicLong** A long value that may be updated atomically
**AtomicLongArray** A long array in which elements may be updated atomically
**AtomicReference** A generic object reference that may be updated atomically
**AtomicReferenceArray** An array of generic object references in which elements may be updated atomically

### Concurrent Collections

```
// BlockingQueue
offer(E e, long timeout,TimeUnit unit)
poll(long timeout, TimeUnit unit)

// BlockingDeque
offerFirst(E e, long timeout, TimeUnit unit)
offerLast(E e, long timeout, TimeUnit unit)
pollFirst(long timeout, TimeUnit unit)
pollLast(long timeout, TimeUnit unit)
```

* The SkipList classes, ConcurrentSkipListSet and ConcurrentSkipListMap , are con- current versions of their sorted
  counterparts, TreeSet and TreeMap , respectively.
* `CopyOnWriteArrayList, CopyOnWriteArraySet`

### Cycling Barriers

If you are using a thread pool, make sure that you set the number of available threads to be at least as large as your
CyclicBarrier limit value.

### Fork Join

Tips for Reviewing a Fork/Join Class

* The class should extend RecursiveAction or RecursiveTask .
* If the class extends RecursiveAction , then it should override a protected compute() method that takes no arguments
  and returns void .
* If the class extends RecursiveTask , then it should override a protected compute()
  method that takes no arguments and returns a generic type listed in the class definition.
* The invokeAll() method takes two instances of the fork/join class and does not return a result.
* The fork() method causes a new task to be submitted to the pool and is similar to the thread executor submit() method.
* The join() method is called after the fork() method and causes the current thread to wait for the results of a
  subtask.
* Unlike fork() , calling compute() within a compute() method causes the task to wait for the results of the subtask.
* The fork() method should be called before the current thread performs a compute() operation, with join() called to
  read the results afterward.
* Since compute() takes no arguments, the constructor of the class is often used to pass instructions to the task.

## Streams

* `Arrays.asList(1,2,3,4,5,6).stream().parallel()`
* `Arrays.asList(1,2,3,4,5,6).parallelStream()`
* flatMap() creates a new stream that is not parallel by default, regardless of whether the underlying elements were
  parallel.

### Unordered streams , parallel reductions, parallel collect ??!

## JAVA IO

### Characteristics

* FileInputStream(rw of data in binary/bytes) class as well as a FileReader(rw data in chars)
* PrintWriter has no accompanying PrintReader class. Likewise, the PrintStream class has no corresponding InputStream
  class.
* FileReader is the low-level stream reader, whereas BufferedReader is the high-level stream that takes a FileReader as
  input
* Base abstract Classes: InputStream , OutputStream , Reader , and Writer
* printStream extends filterOutputStream extends OutputStream

```
BufferedReader bufferedReader = new BufferedReader(new FileReader("zoo-data.txt")))

new BufferedInputStream(new FileReader("zoo-data.txt")); // DOES NOT COMPILE
new BufferedWriter(new FileOutputStream("zoo-data.txt")); // DOES NOT COMPILE
new ObjectInputStream(new FileOutputStream("zoo-data.txt")); // DOES NOT COMPILE
new BufferedInputStream(new InputStream()); // DOES NOT COMPILE
```

### Classes

* **ObjectInputStream** High Deserializes primitive Java data types and graphs of Java objects from an existing
  InputStream
* **ObjectOutputStream** High Serializes primitive Java data types and graphs of Java objects to an existing
  OutputStream
* **InputStreamReader** High Reads character data from an existing InputStream
* **OutputStreamWriter** High Writes character data to an existing OutputStream
* **PrintStream** High Writes formatted representations of Java objects to a binary stream
* **PrintWriter** High Writes formatted representations of Java objects to a text-based output stream

### Common Strema operations

* Do not use flush many times, only few times with large files, and once for small file
* Marking streams : it’s not actually putting the data back into the stream but storing the data that was already read
  into memory for you to read again. Therefore, you should not call the mark() operation with too large a value as this
  could take up a lot of memory.  `mark(int) and reset()`
* For skipping a large number of bytes, skip() will often be faster, because it will use arrays to read the data.

### ObjectInputStream, ObjectOutputStream (Serialization)

* InputStream available() only tells you the number of blocks that can be read without blocking the next caller. In
  other words, it can return 0 even if there are more bytes to be read. So available() method shouldn't be used to check
  for the end of the stream, instead use try Catch(EOFException)
* It is important to check for null values when, reading from a serialized data stream, you can rely on instance of to
  return false
* When Desrializing:
    * Java calls the first no-arg constructor for the first nonserializable parent class, skipping the constructors of
      any serialized class in between.
    * Furthermore, any static variables or default initializations are ignored.

### The PrintStream and PrintWriter Classes

* The PrintStream class operates on OutputStream instances the writes data as bytes
* The PrintWriter class operates on Writer instances and writes data as characters.
* System.out and System.err are actually PrintStream objects.
* Unlike the underlying write() method, which throws a checked IOException that must be caught in your application,
  these print-based methods do not throw any checked exceptions
* checkError() , that can be used to detect the presence of a problem after attempting to write data to the stream.
* PrintWriter.print() is overloaded with all java primitives + String + object and it's using PrintWrite.write()
  underneath.
* public PrintWriter format(String format, Object args. . .)
* public PrintWriter printf(String format, Object args. . .)
* It is recommended that you call the flush() method prior to calling any readLine() or readPassword() methods in order
  to ensure that no data is pending during the read. Failure to do so could result in a user prompt for input with no
  preceding text, as the text prior to the prompt may still be in a buffer.
* console.readPassword() returns char [] because shared string pool could be malicious

### Java io Reviews

* Java would create c:\book\java exists, from new File("c://book//java"); since it corrects slashes
* Not all streams support mark !, so sometimes results are not determined

## NIO.2

* java.io was the first, In java 1.4 NIO was introduced (not in the exam), Java 7 introduced NIO.2 which replaces
  java.io.File and related classes
* NOFOLLOW_LINKS, FOLLOW_LINKS,
* COPY_ATTRIBUTES: copies meta data
* REPLACE_EXISTING
* ATOMIC_MOVE
* getFileName() returns a new Path instance rather than a String .
* getParent() , returns a Path instance representing the parent path or null if there is no such parent.
* The relativize() method requires that both paths be absolute or both relative, and it will throw an
  IllegalArgumentException if a relative path value is mixed with an absolute path value.
    * On Windows-based systems, it also requires that if absolute paths are used, then both paths must have the same
      root directory or drive letter.
* if `path1.resolve(rootPath)` then root path1 will be ignored
* `toRealPath()` throws IOException
* The isSameFile() method fi rst checks if the Path objects are equal in terms of equal() ,and if so, it automatically
  returns true without checking to see if either fi le exists. If the Path object equals() comparison returns false ,
  then it locates each fi le to which the path refers in the fi le system and determines if they are the same, throwing
  a checked IOException if either fi le does not exist.
* By default, the move() method will follow links, throw an exception if the file already exists, and not perform an
  atomic move.
* The Files.move() method can be applied to non-empty directories only if they are on the same underlying drive. While
  moving an empty directory across a drive is supported, moving a non-empty directory across a drive will throw an NIO.2
  DirectoryNotEmptyException .
* Files API that isDirectory() , isRegularFile() , and isSymbolicLink() , isReadable() and isExecutable() , do not throw
  an exception, then check existence also internally and return false if it doesn't
* The Files.size() method is defined only on files. Calling Files.size() on a directory is system dependent and
  undefined. If you need to determine the size of a directory and its contents, you’ll need to walk the directory tree,
* Files.readAttributes() , returns a read-only view of the file attributes.
* Files.getFileAttributeView() , returns the underlying attribute view, and it provides a direct resource for modifying
  file information.
* BasicFileAttributeView.setTimes(FileTime lastModifiedTime, FileTime lastAccessTime, FileTime createTime)

```
file.exists() 					Files.exists(path)
file.getName() 					path.getFileName()
file.getAbsolutePath() 			path.toAbsolutePath()
file.isDirectory() 				Files.isDirectory(path)
file.isFile() 					Files.isRegularFile(path)
file.isHidden() 				Files.isHidden(path)
file.length() 					Files.size(path)
file.lastModified() 			Files.getLastModifiedTime(path)
file.setLastModified(time) 		Files.setLastModifiedTime(path,fileTime)
file.delete() 					Files.delete(path)
file.renameTo(otherFile) 		Files.move(path,otherPath)
file.mkdir() 					Files.createDirectory(path)
file.mkdirs() 					Files.createDirectories(path)
file.listFiles() 				Files.list(path)
```

### Working with Directories

* The NIO.2 API includes an interface called DirectoryStream
* DirectoryStream<Path> stream = Files.newDirectoryStream(path);
* DirectoryStream instance represents a resource to a process that operates on a file system that, like an I/O stream,
  can access only one element at a time, and it must be closed when no longer used.
* DirectoryStream process traverses only a single directory and does not visit any subdirectories that it encounters.
* DirectoryStream does not inherit java.util.stream.Stream , we cannot apply any stream-based methods.
* FileVisitor<T> interface is used to visit an entire directory tree.
* We are supposed to implement `FileVisitor<Path>`

```
/*  is called when a fi le is visited, and it automatically includes the file’s attributes in a BasicFileAttributes object.*/
FileVisitResult visitFile(Path,BasicFileAttributes) throws IOException

/* This method is called when a file cannot be visited along with exception information about the reason for the failure.*/
FileVisitResult visitFileFailed(Path,IOException) throws IOException

/*This method is called before a directory’s contents are visited, and it automatically includes the directory’s attributes in a BasicFileAttributes object. */
FileVisitResult preVisitDirectory(Path,BasicFileAttributes) throws IOException

/* This method is called after a directory’s contents are visited, and it includes exception information when */
FileVisitResult postVisitDirectory(Path,IOException) throws IOException
```

* Each method return FileVisitResult enum:
    * FileVisitResult.CONTINUE
    * FileVisitResult.Terminate
    * FileVisitResult.SKIP_SUBTREE:
        * Used by the preVisitDirectory() method to indicate that the current directory and its descendants should be
          skipped.
    * FileVisitResult.SKIP_SIBLINGS
        * Used by the preVisitDirectory() and postVisitDirectory() methods to indicate that all remaining unvisited
          siblings should be skipped. If used in preVisitDirectory() , then the directory entries are also skipped.

```
/* The NIO.2 API provides an overloaded version of Files.walkFileTree() that takes the path and FileVisitor instance, along with two additional parameters: a Set of FileVisitOption parameters and maximum depth value.*/
Files.walkFileTree(Path, Set<FileVisitOption>, int, FileVisitor<? super Path>)

/*The NIO.2 API detects and stops this behavior by blocking the read of a file in which an infinite loop is detected and instead calls visitFileFailed() with a  FileSystemLoopException . It is important when enabling the FOLLOW_LINKS option in your application to account for this exception, since the default behavior of SimpleFileVisitor is to throw an exception and stop walking the tree on calling
visitFileFailed() . */
FileVisitOption.FOLLOW_LINKS option.

public FileVisitResult visitFileFailed(Path file, IOException exc) throws
IOException {
if (exc instanceof FileSystemLoopException) {
	System.err.println("Circular reference detected: "+file.toString());
} else if(exc != null) {
	throw exc;
}
return FileVisitResult.CONTINUE;
}

```

### Monitoring Directorieis

* Java NIO.2 API includes the WatchService framework for monitoring changes to directories in real time.
* Overview of WatchService API
    1. Create an instance of WatchService from the file system.
        * `try (WatchService service = FileSystems.getDefault().newWatchService()) {`
    2. Register each directory and event type.
        * zooData.register(service,StandardWatchEventKinds.ENTRY_CREATE, StandardWatchEventKinds.ENTRY_DELETE,
          StandardWatchEventKinds.ENTRY_MODIFY);
        * StandardWatchEventKinds.OVERFLOW An event may have been lost. It is possible to receive this event even if it
          is not registered for.
    3. Create a loop that repeatedly queries the WatchService for changes.
    4. Retrieve a WatchKey .
        * `WatchKey poll()` This method retrieves and removes the next WatchKey , returning null if none are present.
        * `WatchKey poll(long timeout, TimeUnit unit) throws InterruptedException` This method retrieves and removes the
          next WatchKey , waiting a specified amount of time if none are present. If the time limit is reached without
          any events, the method returns null .
        * `WatchKey take() throws InterruptedException;` This method retrieves and removes the next WatchKey , waiting
          indefinitely if none are present.
    5. Retrieve all pending events for the WatchKey and do something with them.
    6. Reset the WatchKey .
    7. Once you no longer need the WatchService , close the resource.

### Traversing Files

* Java 8
    * Files.walk(Path)
    * Files.find(Path,int,BiPredicate)
    * They return a Stream<Path> object, which we then processed in a lazy manner.
* Java 7
    * DirectoryStream<Path> stream = Files.newDirectoryStream(path);
        * `for(Path element: stream) { System.out.println(element.getFileName()+"\t"+Files.isDirectory(element)); }`
        * used to visit content of single directory
    * Files.walkFileTree(FileVisitor<T>f)
        * SimpleFileVisitor

### NIO Reviews

* deleteIfExists() would throw a DirectoryNotEmptyException if it had contents.
* calling resolve() with an absolute path as a parameter returns the absolute path,
* Files.move always preserves the metadata even if the COPY_ATTRIBUTES flag is not set.
* NIO.2 views can be used to access file system–dependent attributes.
* Path.equals() does not resolve the path within the file system !
* NIO.2 supports file system–dependent attributes.
* NIO.2 allows you to traverse a directory tree directly.
* NIO.2 supports symbolic links.
* relativize() will throw illegalArgumentException when different types are set
* The normalize() method does not convert a relative path into an absolute path;

## JDBC

* Starting with JDBC 4.0, driver implementations were required to provide the name of the class implementing Driver in a
  file named java.sql.Driver in the directory META-INF/service.
    * META-INF/services/java.sql.Driver  >>  com.home.mydriver.class
    * Class.forName() is not required in JDBC4.0
    * DriverManager.getConnection() throws a SQLException if the driver class is not found.
* location can be localhost or an IP address or a domain name.
* ResultSet Type:

```
ResultSet Type 			Can Backward 		Latest Data 	Supported
TYPE_FORWARD_ONLY 			No 					No 				Yes
TYPE_SCROLL_INSENSITIVE 	Yes 				No 				Yes
TYPE_SCROLL_SENSITIVE 		Yes 				Yes 			No
```

* Concurrency Mode

```
ResultSet Type 				Read  			Update			 Supported
CONCUR_READ_ONLY 			Yes 			Yes					 No
CONCUR_UPDATABLE 			Yes 			No					 Yes
```

* when resultset.getString(x) JDBC starts counting with one rather than zero.
* rs.getTime().toLocalTime
* rs.getDate().toLocalDate
* rs.getTimestamp().toLocalDateTime

### Scrolling ResultSet

* beforeFirst(), afterLast(), first(), last(), next(), previous()
* `absolute()`
    * A positive number moves the cursor to that numbered row.
    * Zero moves the cursor to a location immediately before the first row.
    * A negative number means to start counting from the end of the ResultSet rather than from the beginning.
* `relative(x)`  takes steps either positive or negative and returns boolean if it points to data
* next() is the only one that doesn't require scrollable resultset

### Closing

* close in order -> resultSet -> statement -> connection
* JDBC automatically closes a ResultSet when you run another SQL statement from the same Statement .

### JDBC Exceptions

System.out.println(e.getMessage()); System.out.println(e.getSQLState()); System.out.println(e.getErrorCode());

## Optional

* https://stackoverflow.com/questions/28796324/optional-vs-throwing-an-exception
* https://www.freecodecamp.org/news/optional-in-java-and-anti-patterns-using-it-7d87038362ba/
* https://dzone.com/articles/using-optional-correctly-is-not-optional

## Java 10

* [Trisha Gee](https://www.youtube.com/watch?v=H-LzZofU3zk)
*

## Java 9

* ~~[Trisha Gee GOTO Conf Real World Java 9 ](https://www.youtube.com/watch?v=watS54iWH9U)~~
* ~~[Trisha Gee Devox Conf Real World Java 9](https://www.youtube.com/watch?v=GkP83hvdeMk)~~
* jshell
* Private static default methods inside interfaces, in java 8 it was public only
* takeWhile, dropWhile
* jigsaw project

## Design

* https://github.com/tedyoung/awesome-java8#functional-libraries
* http://www.vavr.io/vavr-docs/
* http://cyclops-react.io/
* [Return of the Statically Typed Languages](http://beust.com/weblog2/archives/000483.html)
* http://blog.paralleluniverse.co/2014/02/04/littles-law/
* http://blog.paralleluniverse.co/2014/05/01/modern-java/
* http://blog.paralleluniverse.co/2014/05/08/modern-java-pt2/
* http://nurkiewicz.blogspot.fr/2012/10/java-features-applicability.html
* https://medium.com/@johnmcclean/powerful-extensible-code-with-tagless-final-in-java-4094f923cdea

# Fibers (Quasar) Green threads, Goroutines, actors

* https://openjdk.java.net/projects/loom/
    * [Project Loom Update with Alan Bateman and Rickard Bäckman](https://www.youtube.com/watch?v=NV46KFV1m-4)
    * https://github.com/lucav76/Fibry/
    * https://dzone.com/articles/a-new-java-with-a-stronger-fiber
* http://cr.openjdk.java.net/~rpressler/loom/Loom-Proposal.html
* https://zeroturnaround.com/rebellabs/what-are-fibers-and-why-you-should-care/
* https://www.jrebel.com/blog/jvm-fibers-and-threads
* http://docs.paralleluniverse.co/quasar/#fibers

## Checklist

* affinity/sticky sessions load balancing
* filters, servlet data compression filters
* filters, servlet encryption filters
* filters, servlet image conversion filters
* filters, servlet logging and auditing filters
* filters, servlet mimetype chain filters
* filters, servlet tokenizing filters
* filters, servlet xslt filters that transform xml content
* @WebServlet example : Declaring a servlet using servlet annotation, servlet annotation example
* absolute-ordering, ordering
* Another asynchronous support:

## Effective Java

*

~~[http://www.jamesward.com/2014/12/03/java-doesnt-suck-youre-just-using-it-wrong](http://www.jamesward.com/2014/12/03/java-doesnt-suck-youre-just-using-it-wrong)~~

*

~~[http://www.takipiblog.com/java-9-the-ultimate-feature-list/](http://www.takipiblog.com/java-9-the-ultimate-feature-list/)~~

* https://github.com/google/error-prone
*

## Github

* http://github.com/Adopt-a-JSR
* http://github.com/gary-rowe/MultiBitMerchant
* http://github.com/JakeWharton/hugo
* http://github.com/stickfigure/motomapia
* http://github.com/timboudreau/acteur
* http://github.com/vkostyukov/la4j
* https://github.com/aol/cyclops

## Algorithms In Java

* ~~[flatten binary tree](http://stackoverflow.com/questions/20957023/flattening-a-binary-tree-to-an-array-in-java)~~
* ~~[flatten binary tree2](http://www.programcreek.com/2013/01/leetcode-flatten-binary-tree-to-linked-list/)~~

## Libraries

* https://github.com/locationtech/spatial4j

## Maven

* http://maven.apache.org/guides/
    * ~~[Five Min Tutorial](http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)~~
    * ~~[30 min guide](http://maven.apache.org/guides/getting-started/index.html)~~
    * ~~[Creating Archetypes](http://maven.apache.org/guides/mini/guide-creating-archetypes.html)~~
* `mvn com.github.ekryd.echo-maven-plugin:echo-maven-plugin:echo -Decho.message='${spring-boot.version}'`

## JUnit 5

* https://junit.org/junit5/docs/current/user-guide/

## Other

http://ogp.me/

## Java Properties

* http://www.baeldung.com/java-properties
* https://stackoverflow.com/questions/10370989/how-to-configure-logging-when-running-a-jar

## Functional Programming

* [Java Functional Programming patterns](https://www.youtube.com/watch?v=YnzisJh-ZNI)
