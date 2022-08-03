# WebWorkers-Pool
Multithreading computations using Web Workers Pool direct from Functions

Usage:

```javascript
// Create expensive function
let fun = (x) => {
    for (var i = 0; i < 100000*x; i++) {}
    return i
}

// list of arguments
let args = [
    [1],
    [2],
    [3],
    [4],
    [5],
    [6],
    [7],
    [8],
    [9],
    [10]
]

// starting time
let ini = performance.now()

// create new working pool for function
let wp = new workerPool(fun)

// run for defined arguments
.run(args)

// results from returning promises
.then(results => {    
    console.log(results)
    console.log('Total time for workerPool (ms): ', performance.now()-ini)

    // We can do the same simulation without worker pool to compare
    ini = performance.now()
    let results2 = args.map(fun)
    console.log(results2)
    console.log('Total time without workerPool (ms): ', performance.now()-ini)
}).catch((err) => {
    console.log('Erro!:', err)
})

```
