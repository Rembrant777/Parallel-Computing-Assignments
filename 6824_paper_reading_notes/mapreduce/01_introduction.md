# Introduction 

* Problem 
In the introduction section the wirter/research prompt a problem:

```txt
Over the past 5 years, the author and many other co-workers in Google have design and implemented hundres of specified purposed computation frameworks or tools to hanld large amount of raw data. Those computation frameworks trying to compute various kinds of  derived data.
But most of the computation frameworks or tools are conceputationally straightforward.

This problems become obvious when the amount of the data becomes very large.  
```

* Inspired by the Functional Model's Map & Reduce 

```txt
The research inspired by the functional like Lisp Map and Reduce operations.

Those kind of operations defined in the scope of the functional language allow uers to 
> parallize large computations easily
> adopt re-execution as the primary mechanism for fault tolerance
```

The parallize && and re-execution solve fault tolerance those two points can fit the large dataset's distributed computing scence very well. 

* Major contribution of this paper 

```txt 
Major contribution of this paper is prompt, design and implement a distributed framework 
based on a series of interfaces that inspired by the functional programming language like Lisp. 

> automatic parallelization 
> distribution of large-scale computations 
```

* Structure of this paper 
```
Section-2: introduce the map & reduce basic knowledge of the programming model with several examples.
Section-3: introduce how to implement MapReduce interfaces tailored towards distributed computing environment. 
Section-4: do some refinements based on the MapReduce programming model 
Section-5: performance measurements of the MapReduce framework 
Section-6: how MapReduce used in Google's production indexing system
Section-7: future work directions
```