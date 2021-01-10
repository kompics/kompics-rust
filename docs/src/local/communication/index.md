# Communication

In this chapter we are going to introduce Kompact's communication mechanisms in detail. We will do so by building up a longer example: A worker pool that, given an array of data, aggregates the data with a given function, while splitting the work over a predetermined number of worker components. The entry point to the pool is going to be a `Manager` component, which takes work requests and distributes them evenly over its worker pool, waits for the results to come in, aggregates the results, and finally responds to the original request. To make things a bit simpler, we will only deal with `u64` arrays and aggregation results for now, and we will assume that our aggregation functions are both [associative](https://en.wikipedia.org/wiki/Associative_property) and [commutative](https://en.wikipedia.org/wiki/Commutative_property). It should be easy to see how a more generic version can be implemented, that accepts other data types than `u64` and can avoid the commutativity requirement.