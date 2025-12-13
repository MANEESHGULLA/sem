A  
Sequerce Diaggram  

sequence diagram shows how dbjects ina  
System mteract with each other over time,  
focusing on the order of events  

Components:  

Object: It is drawn as a rectangle contairuing  
the name of object.  

Message: These are the honzontal amaus drawn  
between objects indicating interactions or  
method calls, i-e sender and recerver.  

Lifelines: These are the vertical lires that  
represents the ifespan of an obrects dunng  
the sequence  

ActirationBars: These are bars on the lifeline  
showing when in obrect is acbre Corocessing)  

Synchronous message: It is shown as a soluid  
tine with a filled amowhead. It is a regular  
message call used for nomal communication  
between sender and receiver  

Asynchronous tressage:- It has a solid tine with  
an open amowhead . A signal is an asyrchronous  
message that has no reply  

An asynchronous message in a UML sequence diagram represents a communication where the sender does not wait for the receiver to finish processing the message and continues its own execution immediately.  

The sender does not block after sending the message  

No immediate return message is expected  

A constructor message creates its receiver. The sender that already exist at the start of the interaction are placed at the top of the diagram. Targets that are created during the interaction by a constructor call are automatically placed further down the diagram.  

Lifelines with constructor  

A destructor message destroys its receiver. There are other ways to indicate that a target is destroyed during an interaction. Only when a target's destruction is set to 'after destructor' do you have to use a destructor.  

Non instahtaneous message:- The messages are often considered to be instantanedus thus the time it fakes to amve at the recever is negugible. To indicates that it talees a certoun while before the recever actualy, receives a message ,aa slanted anow is used.  

Purpose of a sequence dragram  

* To model high tevel mteraction among active  
objects writhin a system.  

+ Developers use sequence diagram as a debuвsub  
tool, It is the most commonly used interaction  
diagram.  

* They help clarify complex interactons and  
ensure everyone has a shared  
