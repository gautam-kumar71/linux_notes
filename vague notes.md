There is no concrete class which implements collection directly

> `Collection` itself has no concrete implementation because it is a generic abstraction.  
> The actual concrete classes are `ArrayList`, `HashSet`, `TreeSet`, etc., which implement the specific behavioral sub-interfaces of `Collection`.


>What you said (slightly cleaned up):
> - `Collection` is an interface
> - `List` and `Set` are interfaces
> - `ArrayList` and `HashSet` are concrete classes
> - `List` and `Set` extend `Collection`
> - `ArrayList` implements `List`, `HashSet` implements `Set`
> - `Collection` has generic methods like add, remove, etc.     
> - There is **no concrete class that implements `Collection` directly**

