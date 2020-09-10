# command-pattern
The Command Pattern: Encapsulating Invocation

Wikipedia says

> In object-oriented programming, the command pattern is a behavioral design pattern in which an object is used to encapsulate all information needed to perform an action or trigger an event at a later time.

##Intent
Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.

 ## BULLET POINTS
 - The Command Pattern decouples an object making a request from the one that knows how to perform it.
 - A Command object is at the center of this decoupling and encapsulates a receiver with an action (or set of actions) .
 - An invoker makes a request of a Command object by calling its execute() method, which invokes those actions on the receiver.
 - Invokers can be parameterized with Commands, even dynamically at runtime. Commands may support undo by implementing an undo method that restores the object to its previous state before the execute() method was last called.
 - Macro Commands are a simple extension of Command that allow multiple commands to be invoked. Likewise, Macro Commands can easily support undo(). In practice, it is not uncommon for “smart” Command objects to implement the request themselves rather than delegating to a receiver.
 - Commands may also be used to implement logging and transactional systems.
 
 ## Applicability
 Use the Command pattern when you want to
 
 * parameterize objects by an action to perform. You can express such parameterization in a procedural language with a callback function, that is, a function that's registered somewhere to be called at a later point. Commands are an object-oriented replacement for callbacks.
 * specify, queue, and execute requests at different times. A Command object can have a lifetime independent of the original request. If the receiver of a request can be represented in an address space-independent way, then you can transfer a command object for the request to a different process and fulfill the request there
 * support undo. The Command's execute operation can store state for reversing its effects in the command itself. The Command interface must have an added Unexecute operation that reverses the effects of a previous call to execute. Executed commands are stored in a history list. Unlimited-level undo and redo is achieved by traversing this list backwards and forwards calling unexecute and execute, respectively
 * support logging changes so that they can be reapplied in case of a system crash. By augmenting the Command interface with load and store operations, you can keep a persistent log of changes. Recovering from a crash involves reloading logged commands from disk and re-executing them with the execute operation
 * structure a system around high-level operations build on primitive operations. Such a structure is common in information systems that support transactions. A transaction encapsulates a set of changes to data. The Command pattern offers a way to model transactions. Commands have a common interface, letting you invoke all transactions the same way. The pattern also makes it easy to extend the system with new transactions
 
 ## Typical Use Case
 
 * to keep a history of requests
 * implement callback functionality
 * implement the undo functionality