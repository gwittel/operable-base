# Description


# Possible use patterns


## Bounded stream

```java

List<Integer> data = ImmutableList.of(1, 2,3);

// agg inline
Summarizer<IN, OUT> summarizer = Summarizers<>
    .withAggregators(....)
    .build().

summarizer.offer(data);
Summary summary = summarizer.read();

// Agg out of band
Summarizer<Integer> summarizer = Summarizers<>
    .withAggregators(....)
    .emittingEvery(someDuration)
    .to(someConsumer or someSubscriber)
    .build().

summarizer.offer(data);
```
# TODO

Interfaces

Package: aggregators
    Interfaces / Types        
        Cardinality
        Percentile
        TopN
    
    Classes:
        ???
        
Package: aggregators.approximate
    Same as aggregator but with error rates
    
    Interfaces:
        ApproximateAggregator
        
    Classes:
        
## TBD

1. What if we want to emit based on data time vs clock time?    

# Notes

# Known Issues

These are to be converted to Github Issues

1. Maven plugin broken due to ASM Java 9 bugs:
    * maven-dependency-plugin -- See [MDEP-559](https://issues.apache.org/jira/browse/MDEP-559)
    * modernizer -- gaul/modernizer-maven-plugin#60
    
    Workaround is to disable the plugins via properties:
   
    ```xml
    <op.check.skip-dependency>true</op.check.skip-dependency>
    <op.check.skip-modernizer>true</op.check.skip-modernizer>
    ```
