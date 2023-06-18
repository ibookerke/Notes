# Protocol Buffers
Protocol Buffers are a language-neutral, platform-neutral extensible mechanism for serializing structured data.
The method involves an interface description language that describes the structure of some data and a program that generates source code from that description for generating or parsing a stream of bytes that represents the structured data.

It is being presented as a library that has an internal compiler and a certain format of describing the data structures. By the description files with the `.proto` extension we are serializing and deserializing data structures. 


The main difference between the JSON and Protobuf is that **JSON is just text, while Protocol Buffers are binary**. This difference can have a significant impact on the performance and speed of information transfer between different device


Example:
Here we are describing data structures in `book.proto` file
![[Pasted image 20230618235027.png]]

Then we are adding loading this structure into a for example a go lang application using this command:
![[Pasted image 20230618235332.png]]
Then is creates a go lang struct that corresponds to a described proto file
![[Pasted image 20230618235457.png]]
