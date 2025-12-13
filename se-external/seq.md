# A Sequence Diagram

A sequence diagram shows how objects in a system interact with each other over time, focusing on the order of events.

## Components

### Object
It is drawn as a rectangle containing the name of the object.

### Message
These are the horizontal arrows drawn between objects indicating interactions or method calls, i.e., sender and receiver.

### Lifelines
These are the vertical lines that represent the lifespan of objects during the sequence.

### Activation Bars
These are bars on the lifeline showing when an object is active (processing).

## Messages

### Synchronous Message
It is shown as a solid line with a filled arrowhead. It is a regular message call used for normal communication between sender and receiver.

### Asynchronous Message
It has a solid line with an open arrowhead. A signal is an asynchronous message that has no reply.

An asynchronous message in a UML sequence diagram represents a communication where the sender does not wait for the receiver to finish processing the message and continues its own execution immediately.

The sender does not block after sending the message  

No immediate return message is expected

### Constructor Message
A constructor message creates its receiver. The sender that already exists at the start of the interaction is placed at the top of the diagram. Targets that are created during the interaction by a constructor call are automatically placed further down the diagram.

Lifelines with constructor

### Destructor Message
A destructor message destroys its receiver. There are other ways to indicate that a target is destroyed during an interaction. Only when a target's destruction is set to “after destructor” do you have to use a destructor.

### Non-instantaneous Message
The messages are often considered to be instantaneous, thus the time it takes to arrive at the receiver is negligible. To indicate that it takes a certain while before the receiver actually receives a message, a slanted arrow is used.

## Purpose of a Sequence Diagram

- To model high-level interaction among active objects within a system.

- Developers use sequence diagrams as a debugging tool. It is the most commonly used interaction diagram.

- They help clarify complex interactions and ensure everyone has a shared understanding.
