# Performance Comparison of Deno and Node.js on over 30+ tests

## Introduction

Deno is a simple, modern, and secure runtime for JavaScript and TypeScript. 
Deno is sandboxed and supports Typescript out of the box.
Deno is built over Google's V8 engine and uses Rust.
The first major release of Deno was launched in May 2020.

Node.js is a very popular battle-tested runtime for Javascript.
Node.js has been around for more than 11 years.
Node.js is built over Google's V8 engine and uses C++.

Functionally, Deno is same as Node.js, with some extra sandboxing related enhancements.
So, is Deno ready for prime time? Can it perform as good as or better as Node.js?
If Deno can't perform as good as Node.js, it can never become a major runtime.

This repository continually runs 30+ tests to compare Deno's performance against Node.js. 
This repository would be updated as soon as there are new releases on either Deno or Node.js.

```Work is still in progress```


### Versions
Deno: ```deno 1.5.1```
Node.js: ```v15.1.0```
## Tests and Results



### Hello world - native
Hello world program without any frameworks
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```549``` | ```566``` | 
| Mean | ```0.34``` | ```0.35``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```23``` | ```16``` | 

Deno is ```3.00%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1590``` | ```1527``` | 
| Mean | ```1.06``` | ```1.02``` | 
| Median | ```1.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```19``` | ```18``` | 

Deno is ```3.96%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3874``` | ```3621``` | 
| Mean | ```2.96``` | ```2.42``` | 
| Median | ```3.00``` | ```2.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```39``` | ```37``` | 

Deno is ```6.53%``` faster than  Node.js

### Hello world - oak and express
Hello world program using the popular frameworks: Oak/Deno, Express/Node.js
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```653``` | ```559``` | 
| Mean | ```0.45``` | ```0.35``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```17``` | ```12``` | 

Deno is ```14.40%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2226``` | ```1687``` | 
| Mean | ```1.80``` | ```1.15``` | 
| Median | ```2.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```23``` | ```17``` | 

Deno is ```24.21%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5390``` | ```3882``` | 
| Mean | ```4.58``` | ```2.73``` | 
| Median | ```4.00``` | ```3.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```55``` | ```32``` | 

Deno is ```27.98%``` faster than  Node.js
## Next steps

There is a lot more work to be done! If you like to suggest more benchmarks, please add an issue with your suggestions.