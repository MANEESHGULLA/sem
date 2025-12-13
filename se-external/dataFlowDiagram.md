# Data Flow Diagram

**Description**  
→ It is a graphical representation of how  
data flows across a information system  

→ DFD shows incoming data, outgoing data and  
data stored  

→ DFD designed to show how a system is divided  
into smaller portions and how is stored data flows  
between those paths  

## Level 0 – DFD : project system scope & boundaries
→ shows entire system in single process  
→ shows external entities and major dataflows  
→ does not show internal details  

## Level 1 – DFD : project understanding main system functions
→ decomposes the level 0 DFD by breaking single process  
into major processes  
→ includes data stores and internal dataflows  

## Level 2 DFD
→ further decomposes level-1 DFD processes into detailed  
sub processes  
→ shows detailed logic and data movement  

## Components

1) **External Entity**  → rectangle  
   defines source and destination of data  

2) **Process** → rounded rectangle  
   represents activities & actions performed on data  
   converts incoming dataflow into outgoing dataflow  

3) **Data store**  
   → where data is stored or temporary repository of data  

4) **Data flow** →  
   represents movement of data, it is a pipeline  
   through which data flows  

## Rules & Relationships

→ External ↔ External entity : Data cannot flow  
→ P ↔ P : Data can flow  
→ Datastore ↔ Datastore : Data cannot flow  
→ External E ↔ P : Data can flow  
→ External E ↔ Datastore : Data cannot flow  
→ Process ↔ Datastore : Data can flow  
→ process must have 1 input dataflow &  
   1 outgoing dataflow  
→ Datastore  
→ 2 dataflows cannot cross each other  

## Disadvantages
1) Time consuming and costly  
2) Requires knowledge of programmer’s language  

## Advantages
1) To find a variable that is used but not defined  
2) To find a variable that is defined but not used  
3) To find a variable which is defined multiple times  
   before its use  
4) unallocating variable before its use
