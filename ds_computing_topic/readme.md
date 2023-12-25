# Naos: Serialization-free RDMA networking in Java 

## Terminology 
* OSD: Object Serialization/Deserialization 

## Background && Main Contribution 
This paper presents Naos, a JVM-based technique bypassing heap serialization boundaries that allows objects to be directly sent from a local heap to a remote one with minimal CPU involvement and over RDMA networks. 

Because data exchanges via the JVM heap directly via RDMA protocol, so there is no need to do the serialization/deserialization when send/receive network messages. And we know that serialization/deserialization cost lots of CPU resources, so when use Naos the CPU resource can be saved. 

| Research Questions         | Conclusion                  | Support Experiment Statistics | Experimental Design        |
|----------------------------|-----------------------------|------------------------------|---------------------------|
| - Question 1               | - Summary of Findings       | - Sample Size                | - Research Hypothesis     |
| - Question 2               | - Key Insights              | - Data Collection Method     | - Variables               |
| - Question 3               | - Implications              | - Data Analysis Techniques  |   - Independent Variables |
| ...                        | ...                         | - Results and Findings      |   - Dependent Variables   |
|                            |                             |                              | - Data Collection and Instruments |
| ...                        | ...                         | ...                          | ...                       |



## Summary 

## resources 
* [paper download link](https://www.usenix.org/system/files/atc21-taranov.pdf)
* [yt-video](https://www.usenix.org/conference/atc21/presentation/taranov)
* [source codes](https://github.com/spcl/naos)