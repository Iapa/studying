| abstract | interface |
| :--- | :--- |
| Abstract class can have abstract and non-abstract methods | Interface can have only abstract methods.Since Java8,it can have default and static methods also |
| Abstract calss doesn't support multiple inheritance  | Interface supports multiple inheritance |
| abstract class can have final, non-final,static and non-static variables  | interface has only static and final variables |



`Abstract` class achieves partial abstraction whereas interface achieves fully abstraction.

An `Abstract` class's purpose is tro provide an appropriate superclass from which other classes can inheift and thus share a common design 



An `intreface` descirbes a set of methods that can be called on an object but does not privide concrete implementations for all the methods. Once a class implements an interface, all objects of that have an is-a relationship with the interface type. and all objects of the class are guaranteed to provide the functionality described by the interface. This is true of all subcalsses of that class as well. Interfaces form a contract between the class and the outside world, and  thsi contract is enforced at build time by the compiler



