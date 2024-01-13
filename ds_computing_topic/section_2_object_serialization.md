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

Those well-defined messages can then be exchanged using any network protocol.

Even though those 3rd libraries remain the independent of programming languages or operating systems, but they also import low performance to the system. 

But the above 3rd librareis also have in-sufficient in performance. That's why Kryo those kind of designed specifically for JVM 3rd libraries are designed and are frequently adopted in the JVM-based big-data applications. 

### OSD of Kryo 
* What problem Kryo resolve ? 
1. When serialize/deserialize a data object, Kryo achives a more compact representation via registerring classes manually. This resolves some Java native serialize limitations. 
2. Represents all primitive types and classes using integer identifiers. This reducing the amout of space needed for storing type names. 


* Kryo's trade off
Classess registration may become cumbersome for applications with hundreds of data types.

* Compare to Kryo, Naos advantages 
Naos has defined more clearn and simpler interfaces, and do not need developers involvement. 

### Accelerated OSD
* What problem the Accelerated OSD resolve ? 
There are two OSD libraries Cereal and Optimus Prime they trying to resolve the overhead of data transformation via hardware accelerators during OSD period. 

Trying to speed up the process of data transformation by parallize the OSD process. But it has a prerequisite: 
The accelerator and the serialization format are co-designed which means developers have to customized process the hardware accelerator and the serialization strategy. Even though this co-designed accelerator and serialization format achieves 15x speedup in serialization throughput on average over Kryo. 

However, it at the expense of requiring specilized hardware and sacrifice the universality. 

* Accelerated OSD trade off
1. require specilized hardware, sacrifice the universality. 
2. co-design acelerator and serialize strategy increase maintenance and update costs. 

* Compare to Accelerated OSD libraries (Cereal, Optimus Prime), Naos advantages
Do not need any hardware specialized (well RDMA and the Infinbind also means expensive hardware to me :) )

### Zero-transformation OSD 

* What Zero-transformation OSD resolve ? 
By dropping portability, the Zero-transformation OSD library manages to partially avoid data transformation and object construction by serializing Java objects in their own specialized  JVM formats. 

Which means the serialized data objects are written to communication buffers in the same binary format as they stored in the heap.(zero-copy)

* Similarity between Zero-transformation OSD(Skyway) and Naos 
Like Skyway, Naos sends objects in the JVM heap format, assuming that communicating parties run on the same JVM software. 

* Difference between Zero-transformation OSD(Skyway) and Naos
Unlike Skyway, Naos is not a serialization library that requiring to copy objects between communication buffers and JVM heap.

* Zero-transfrormation OSD trade off 
1. Dropping the portability to exchange performance behavior during data serialize OSD period. 
2. Zero-transformation OSD Skyway's memory management prevents the use of RDMA networking. 

* Compare to Zero-transformation OSD library, Naos advantages 
1. Completely remove the process of serialization/deserializetion. Objects do not need to move between kernel buffern and JVM heap.
2. Do not take care of memory management. Instead by using RDMA to transfer data objects that are held in the JVM heap directly.  

### What Naos is not? and what Naos covers?  
* Naos is not: 
Naos is not a serilization library, it does not have serialize and deserialize implementation. 
Naos also cannot replace the OSD libraries in the systems that do not use the OSD for communication(like writing objects to disk). 

* Naos covers
Naos only covers end-to-end transfers via replacing the memory-JVM heap copy by RDMA-JVM heap copy.


### What Naos this library can be used ? and what Naos this library cannot be adopted ? 
* Can be used
Since Naos only covers end-to-end transfers, for future systems that want to take advantage of serialization-free zero-copy RDMA networking. 

* Cannot be adopted
But some of several exsiting Java framework the main obstable to using Naos is that some of these systems do not consider the possibility to 
send objects without serialization. 

Especially Hadoop and Spark those frameworks any associated interfaces are not remain and design for data transfer without serialziation/deserialization. 

Like Spark and Hadoop completely decouple serialization from communication: 
their serialization modules are designed to serialize objects only to files.
their shuffle modules are design to communicate only files. 

Such file-centric design simplifies inner-node communication. However, it makes integrating Naos very difficult. 



