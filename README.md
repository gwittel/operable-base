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

## Maven Configuration

### Repositories

By default, no repository is explicitly specified for dependencies.

Your Maven configuration should include the following repositories:

```xml

    <repositories>
        <repository>
            <id>sonatype-nexus-snapshots</id>
            <name>Sonatype Nexus Snapshots</name>
            <url>https://oss.sonatype.org/content/repositories/snapshots</url>
            <releases>
                <enabled>false</enabled>
            </releases>
            <snapshots>
                <enabled>true</enabled>
            </snapshots>
        </repository>
    </repositories>
```