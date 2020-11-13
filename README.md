# Performance Comparison of Deno and Node.js on over 30+ tests

## Introduction

Deno is a simple, modern, and secure runtime for JavaScript and TypeScript. Deno is sandboxed and supports Typescript out of the box.Deno is built over Google's V8 engine and uses Rust. The first major release of Deno was launched in May 2020.

Node.js is a very popular battle-tested runtime for Javascript. Node.js has been around for more than 11 years. Node.js is built over Google's V8 engine and uses C++.

Functionally, Deno is same as Node.js. 

Now onwards, there would always be two options to choose from: Node.js or Deno?

It is very unlikely that existing Node.js apps will be ported to Deno.
But it is very likely that people **could** consider Deno for new apps.

If both are functionally same, what are the primary factors to consider Deno over Node.js:
* Reliability
* Performance
* (could be more ....)

Reliability would be discussed separately. The focus of this page is performance.

So, is Deno ready for prime time? Can it perform as good as or better as Node.js?
If Deno can't perform as good as Node.js, it can never become a major runtime.

The purpose of this repository/page is to continually run and report 30+ on tests to compare Deno's performance against Node.js. The plan is to keep this repository/page updated as soon as there are new releases on either Deno or Node.js. The frequency would likely be weekly.

Finally, it's worth mentioning that, only readings would be presented. Coming to a conclusion is upto the reader.

```Work is still in progress```


### Versions
Deno: ```1.5.2```

Node.js: ```15.1.0```

### Environment
MacBook Pro 1.4Ghz Quad core i5 with 8G memory

### List of Tests

| Test | Description |
| ------- | ------- |
| ```Hello world!``` | This one is a very simple hello world program. It responds to a GET request with a JSON containing a string Hello World! |  
| ```Hello world with frameworks - oak and express``` | Hello world program using the popular frameworks: Oak/Deno, Express/Node.js |  
| ```Echo name over HTTPS``` | A simple echo name program that runs over HTTPS |  
| ```Five hundred random integers``` | Generate five hundred random integers and return them in a JSON array |  
| ```Five hundred random 16 character hex string``` | Generate five hundred random 16 character hex strings and return them in a JSON array |  
| ```One hundred V1 UUIDs``` | Generate one hundred V1 UUIDs and return them in a JSON array |  
| ```One hundred V4 UUIDs``` | Generate one hundred V4 UUIDs and return them in a JSON array |  
| ```One hundred V5 UUIDs``` | Generate one hundred V5 UUIDs and return them in a JSON array |  
| ```Parse five hundred strings``` | Parse five hundred strings containing integers and return parsed integers in a JSON array |  
| ```Calculate mean of 500 numbers``` | Calculate mean of 500 numbers and return it in response |  
| ```Calculate median of 500 numbers``` | Calculate median of 500 numbers and return it in response |  

## Tests and Results



### Hello world!
This one is a very simple hello world program. It responds to a GET request with a JSON containing a string Hello World!
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```596``` | ```632``` | 
| Mean | ```0.31``` | ```0.35``` | 
| Median | ```0.28``` | ```0.32``` | 
| Min | ```0.241``` | ```0.258``` | 
| Max | ```1.412``` | ```2.274``` | 


![Chart of Deno hello_world](charts/deno__hello_world__1.png)
![Chart of Node.js hello_world](charts/node__hello_world__1.png)

Deno is ```5.70%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1853``` | ```1891``` | 
| Mean | ```1.14``` | ```1.22``` | 
| Median | ```0.99``` | ```1.04``` | 
| Min | ```0.229``` | ```0.303``` | 
| Max | ```11.085``` | ```19.547``` | 


![Chart of Deno hello_world](charts/deno__hello_world__10.png)
![Chart of Node.js hello_world](charts/node__hello_world__10.png)

Deno is ```2.01%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4398``` | ```4127``` | 
| Mean | ```3.14``` | ```2.63``` | 
| Median | ```2.89``` | ```2.36``` | 
| Min | ```0.213``` | ```0.338``` | 
| Max | ```15.862``` | ```25.808``` | 


![Chart of Deno hello_world](charts/deno__hello_world__25.png)
![Chart of Node.js hello_world](charts/node__hello_world__25.png)

Deno is ```6.16%``` faster than  Node.js

### Hello world with frameworks - oak and express
Hello world program using the popular frameworks: Oak/Deno, Express/Node.js
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world_oak_exp.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world_oak_exp.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```720``` | ```633``` | 
| Mean | ```0.44``` | ```0.36``` | 
| Median | ```0.40``` | ```0.33``` | 
| Min | ```0.36``` | ```0.287``` | 
| Max | ```2.026``` | ```2.031``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__1.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__1.png)

Deno is ```12.08%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2577``` | ```1978``` | 
| Mean | ```1.91``` | ```1.30``` | 
| Median | ```1.60``` | ```1.16``` | 
| Min | ```0.38``` | ```0.33``` | 
| Max | ```20.039``` | ```10.933``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__10.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__10.png)

Deno is ```23.24%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6395``` | ```4704``` | 
| Mean | ```5.01``` | ```3.16``` | 
| Median | ```4.45``` | ```2.80``` | 
| Min | ```0.283``` | ```0.336``` | 
| Max | ```29.84``` | ```26.894``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__25.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__25.png)

Deno is ```26.44%``` faster than  Node.js

### Echo name over HTTPS
A simple echo name program that runs over HTTPS
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_https_hello_name.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_https_hello_name.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```714``` | ```695``` | 
| Mean | ```0.42``` | ```0.42``` | 
| Median | ```0.38``` | ```0.39``` | 
| Min | ```0.316``` | ```0.335``` | 
| Max | ```2.765``` | ```2.211``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__1.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__1.png)

Deno is ```2.66%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2168``` | ```2133``` | 
| Mean | ```1.44``` | ```1.45``` | 
| Median | ```1.27``` | ```1.32``` | 
| Min | ```0.294``` | ```0.397``` | 
| Max | ```11.413``` | ```9.648``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__10.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__10.png)

Deno is ```1.61%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5214``` | ```4863``` | 
| Mean | ```3.86``` | ```3.43``` | 
| Median | ```3.64``` | ```3.22``` | 
| Min | ```0.29``` | ```0.598``` | 
| Max | ```16.234``` | ```22.178``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__25.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__25.png)

Deno is ```6.73%``` faster than  Node.js

### Five hundred random integers
Generate five hundred random integers and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1008``` | ```985``` | 
| Mean | ```0.47``` | ```0.45``` | 
| Median | ```0.45``` | ```0.40``` | 
| Min | ```0.314``` | ```0.32``` | 
| Max | ```2``` | ```2.172``` | 


![Chart of Deno random_int](charts/deno__random_int__1.png)
![Chart of Node.js random_int](charts/node__random_int__1.png)

Deno is ```2.28%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2583``` | ```2756``` | 
| Mean | ```1.52``` | ```1.68``` | 
| Median | ```1.33``` | ```1.50``` | 
| Min | ```0.294``` | ```0.391``` | 
| Max | ```12.073``` | ```14.492``` | 


![Chart of Deno random_int](charts/deno__random_int__10.png)
![Chart of Node.js random_int](charts/node__random_int__10.png)

Deno is ```6.28%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6585``` | ```6469``` | 
| Mean | ```4.87``` | ```4.01``` | 
| Median | ```4.47``` | ```3.64``` | 
| Min | ```0.383``` | ```0.492``` | 
| Max | ```19.882``` | ```18.237``` | 


![Chart of Deno random_int](charts/deno__random_int__25.png)
![Chart of Node.js random_int](charts/node__random_int__25.png)

Deno is ```1.76%``` faster than  Node.js

### Five hundred random 16 character hex string
Generate five hundred random 16 character hex strings and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_hex.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_hex.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2384``` | ```2514``` | 
| Mean | ```1.06``` | ```1.09``` | 
| Median | ```1.00``` | ```1.03``` | 
| Min | ```0.853``` | ```0.849``` | 
| Max | ```3.773``` | ```3.339``` | 


![Chart of Deno random_hex](charts/deno__random_hex__1.png)
![Chart of Node.js random_hex](charts/node__random_hex__1.png)

Deno is ```5.17%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6239``` | ```8969``` | 
| Mean | ```4.16``` | ```5.20``` | 
| Median | ```3.23``` | ```5.37``` | 
| Min | ```0.817``` | ```0.99``` | 
| Max | ```14.224``` | ```10.922``` | 


![Chart of Deno random_hex](charts/deno__random_hex__10.png)
![Chart of Node.js random_hex](charts/node__random_hex__10.png)

Deno is ```30.44%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```17143``` | ```23310``` | 
| Mean | ```13.82``` | ```15.35``` | 
| Median | ```12.36``` | ```16.50``` | 
| Min | ```0.888``` | ```0.999``` | 
| Max | ```66.228``` | ```24.547``` | 


![Chart of Deno random_hex](charts/deno__random_hex__25.png)
![Chart of Node.js random_hex](charts/node__random_hex__25.png)

Deno is ```26.46%``` slower than  Node.js

### One hundred V1 UUIDs
Generate one hundred V1 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v1.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v1.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1314``` | ```1447``` | 
| Mean | ```0.59``` | ```0.71``` | 
| Median | ```0.55``` | ```0.68``` | 
| Min | ```0.402``` | ```0.498``` | 
| Max | ```2.364``` | ```2.339``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__1.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__1.png)

Deno is ```9.19%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3143``` | ```4077``` | 
| Mean | ```1.96``` | ```2.82``` | 
| Median | ```1.68``` | ```2.69``` | 
| Min | ```0.418``` | ```0.574``` | 
| Max | ```11.545``` | ```10.163``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__10.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__10.png)

Deno is ```22.91%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```8144``` | ```11092``` | 
| Mean | ```6.30``` | ```8.81``` | 
| Median | ```5.78``` | ```9.14``` | 
| Min | ```0.444``` | ```0.807``` | 
| Max | ```52.555``` | ```31.968``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__25.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__25.png)

Deno is ```26.58%``` slower than  Node.js

### One hundred V4 UUIDs
Generate one hundred V4 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v4.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v4.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1615``` | ```2555``` | 
| Mean | ```0.89``` | ```1.74``` | 
| Median | ```0.82``` | ```1.54``` | 
| Min | ```0.714``` | ```1.238``` | 
| Max | ```3.913``` | ```4.774``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__1.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__1.png)

Deno is ```36.79%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5005``` | ```12907``` | 
| Mean | ```3.60``` | ```11.21``` | 
| Median | ```3.08``` | ```9.19``` | 
| Min | ```0.615``` | ```3.519``` | 
| Max | ```12.05``` | ```22.155``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__10.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__10.png)

Deno is ```61.22%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```12349``` | ```36056``` | 
| Mean | ```9.85``` | ```32.57``` | 
| Median | ```9.24``` | ```29.17``` | 
| Min | ```0.666``` | ```1.865``` | 
| Max | ```27.352``` | ```69.114``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__25.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__25.png)

Deno is ```65.75%``` slower than  Node.js

### One hundred V5 UUIDs
Generate one hundred V5 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v5.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v5.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1813``` | ```2439``` | 
| Mean | ```1.06``` | ```1.60``` | 
| Median | ```0.93``` | ```1.55``` | 
| Min | ```0.818``` | ```1.187``` | 
| Max | ```4.283``` | ```5.949``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__1.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__1.png)

Deno is ```25.67%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7687``` | ```10845``` | 
| Mean | ```5.78``` | ```9.07``` | 
| Median | ```4.96``` | ```8.62``` | 
| Min | ```0.789``` | ```1.463``` | 
| Max | ```14.925``` | ```18.94``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__10.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__10.png)

Deno is ```29.12%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```16477``` | ```30257``` | 
| Mean | ```14.04``` | ```27.05``` | 
| Median | ```14.10``` | ```27.48``` | 
| Min | ```0.759``` | ```1.63``` | 
| Max | ```37.405``` | ```47.814``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__25.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__25.png)

Deno is ```45.54%``` slower than  Node.js

### Parse five hundred strings
Parse five hundred strings containing integers and return parsed integers in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_parse_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_parse_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```992``` | ```1129``` | 
| Mean | ```0.50``` | ```0.52``` | 
| Median | ```0.49``` | ```0.50``` | 
| Min | ```0.352``` | ```0.355``` | 
| Max | ```2.02``` | ```1.978``` | 


![Chart of Deno parse_int](charts/deno__parse_int__1.png)
![Chart of Node.js parse_int](charts/node__parse_int__1.png)

Deno is ```12.13%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2607``` | ```3053``` | 
| Mean | ```1.69``` | ```1.91``` | 
| Median | ```1.57``` | ```1.76``` | 
| Min | ```0.331``` | ```0.506``` | 
| Max | ```11.582``` | ```10.619``` | 


![Chart of Deno parse_int](charts/deno__parse_int__10.png)
![Chart of Node.js parse_int](charts/node__parse_int__10.png)

Deno is ```14.61%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6473``` | ```7501``` | 
| Mean | ```4.86``` | ```4.79``` | 
| Median | ```4.46``` | ```4.47``` | 
| Min | ```0.352``` | ```0.51``` | 
| Max | ```51.673``` | ```17.827``` | 


![Chart of Deno parse_int](charts/deno__parse_int__25.png)
![Chart of Node.js parse_int](charts/node__parse_int__25.png)

Deno is ```13.70%``` slower than  Node.js

### Calculate mean of 500 numbers
Calculate mean of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_mean.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_mean.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```669``` | ```677``` | 
| Mean | ```0.39``` | ```0.41``` | 
| Median | ```0.36``` | ```0.38``` | 
| Min | ```0.309``` | ```0.325``` | 
| Max | ```2.043``` | ```2.132``` | 


![Chart of Deno mean](charts/deno__mean__1.png)
![Chart of Node.js mean](charts/node__mean__1.png)

Deno is ```1.18%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1996``` | ```2164``` | 
| Mean | ```1.31``` | ```1.47``` | 
| Median | ```1.16``` | ```1.35``` | 
| Min | ```0.334``` | ```0.372``` | 
| Max | ```13.095``` | ```6.573``` | 


![Chart of Deno mean](charts/deno__mean__10.png)
![Chart of Node.js mean](charts/node__mean__10.png)

Deno is ```7.76%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4960``` | ```4864``` | 
| Mean | ```3.66``` | ```3.38``` | 
| Median | ```3.37``` | ```3.17``` | 
| Min | ```0.314``` | ```0.478``` | 
| Max | ```16.062``` | ```16.07``` | 


![Chart of Deno mean](charts/deno__mean__25.png)
![Chart of Node.js mean](charts/node__mean__25.png)

Deno is ```1.94%``` faster than  Node.js

### Calculate median of 500 numbers
Calculate median of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_median.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_median.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```798``` | ```798``` | 
| Mean | ```0.49``` | ```0.51``` | 
| Median | ```0.45``` | ```0.46``` | 
| Min | ```0.399``` | ```0.402``` | 
| Max | ```2.179``` | ```2.526``` | 


![Chart of Deno median](charts/deno__median__1.png)
![Chart of Node.js median](charts/node__median__1.png)

Deno is same as  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2376``` | ```2672``` | 
| Mean | ```1.71``` | ```2.08``` | 
| Median | ```1.43``` | ```2.06``` | 
| Min | ```0.377``` | ```0.477``` | 
| Max | ```13.4``` | ```21.993``` | 


![Chart of Deno median](charts/deno__median__10.png)
![Chart of Node.js median](charts/node__median__10.png)

Deno is ```11.08%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5986``` | ```7146``` | 
| Mean | ```4.49``` | ```5.79``` | 
| Median | ```4.31``` | ```5.91``` | 
| Min | ```0.343``` | ```0.561``` | 
| Max | ```17.876``` | ```22.269``` | 


![Chart of Deno median](charts/deno__median__25.png)
![Chart of Node.js median](charts/node__median__25.png)

Deno is ```16.23%``` slower than  Node.js
## Scenarios to be added

Following is the list of scenarios that would be added soon:
* Logger: console, file
* Api proxy: http, https
* JSON cloning: small and large
* Websocket
* File operations: create, write, delete
* TCP server
* UDP server
* Environment variables: get, set and delete
* Base64: text, image
* MD5, shal1,sha256, sha512, sha3
* Big JSON upload
* Multipart form data
* Image, PDF upload
* Workers
* Regexes
* Luhn check

## Next steps

There is a lot more work to be done! If you like to suggest more benchmarks, please add an issue with your suggestions.

Also, please add a star to this repository if it has been valuable. More stars means more readers and this would encourage us to keep the benchmarking running.