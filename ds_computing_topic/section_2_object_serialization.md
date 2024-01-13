## Section 2 Object Serialization 

Terminal OSD defined in the scope of this paper refers to a process that with 5 steps:

1. graph traversal 
2. data transformation 
3. transmission 
4. data traversal 
5. object construction 

during the process of data serialization/deserialization. 


Object serialization refers to the process of converting an object's state, including its fields and data, into a fomrat 
that can be easily stored or transmitted and later constructed. 

Object seirlaization allows objects to be saved to a file, sent via the network protocol, or stored in a database, among other use cases.

Section 2 introduces that many third party libraries have been developed to perform OSD in Java. Some of the 3rd provide Java building of popular cross-languages OSD approaches which allowing serializaing arbitrary data structures into well defined message. 

Those well-defined messages can then be exchanged using any network protocol and also remaines independent of programming languages or operating system. 

But the above 3rd librareis also have in-sufficient in performance. That's why Kryo those kind of designed specifically for JVM 3rd libraries are designed and are frequently adopted in the JVM-based big-data applications. 




