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
| TimeTakenMS | ```555``` | ```542``` | 
| Mean | ```0.28``` | ```0.32``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```2``` | ```2``` | 


![Chart of Deno hello_world](charts/deno__hello_world__1.png)
![Chart of Node.js hello_world](charts/node__hello_world__1.png)

Deno is ```2.34%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1703``` | ```1619``` | 
| Mean | ```1.08``` | ```1.02``` | 
| Median | ```1.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```11``` | ```19``` | 


![Chart of Deno hello_world](charts/deno__hello_world__10.png)
![Chart of Node.js hello_world](charts/node__hello_world__10.png)

Deno is ```4.93%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4030``` | ```3827``` | 
| Mean | ```2.99``` | ```2.43``` | 
| Median | ```3.00``` | ```2.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```17``` | ```12``` | 


![Chart of Deno hello_world](charts/deno__hello_world__25.png)
![Chart of Node.js hello_world](charts/node__hello_world__25.png)

Deno is ```5.04%``` faster than  Node.js

### Hello world with frameworks - oak and express
Hello world program using the popular frameworks: Oak/Deno, Express/Node.js
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world_oak_exp.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world_oak_exp.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```673``` | ```589``` | 
| Mean | ```0.41``` | ```0.35``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```2``` | ```2``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__1.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__1.png)

Deno is ```12.48%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2333``` | ```1801``` | 
| Mean | ```1.73``` | ```1.16``` | 
| Median | ```2.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```20``` | ```12``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__10.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__10.png)

Deno is ```22.80%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5653``` | ```4093``` | 
| Mean | ```4.51``` | ```2.69``` | 
| Median | ```4.00``` | ```3.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```24``` | ```15``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__25.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__25.png)

Deno is ```27.60%``` faster than  Node.js

### Echo name over HTTPS
A simple echo name program that runs over HTTPS
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_https_hello_name.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_https_hello_name.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```694``` | ```659``` | 
| Mean | ```0.41``` | ```0.40``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```3``` | ```2``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__1.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__1.png)

Deno is ```5.04%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1957``` | ```1938``` | 
| Mean | ```1.34``` | ```1.33``` | 
| Median | ```1.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```11``` | ```20``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__10.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__10.png)

Deno is ```0.97%``` faster than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4827``` | ```4606``` | 
| Mean | ```3.71``` | ```3.24``` | 
| Median | ```4.00``` | ```3.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```16``` | ```17``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__25.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__25.png)

Deno is ```4.58%``` faster than  Node.js

### Five hundred random integers
Generate five hundred random integers and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```882``` | ```909``` | 
| Mean | ```0.39``` | ```0.41``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```3``` | ```2``` | 


![Chart of Deno random_int](charts/deno__random_int__1.png)
![Chart of Node.js random_int](charts/node__random_int__1.png)

Deno is ```2.97%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2486``` | ```2653``` | 
| Mean | ```1.46``` | ```1.62``` | 
| Median | ```1.00``` | ```2.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```12``` | ```14``` | 


![Chart of Deno random_int](charts/deno__random_int__10.png)
![Chart of Node.js random_int](charts/node__random_int__10.png)

Deno is ```6.29%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6128``` | ```6218``` | 
| Mean | ```4.42``` | ```3.84``` | 
| Median | ```4.00``` | ```4.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```18``` | ```21``` | 


![Chart of Deno random_int](charts/deno__random_int__25.png)
![Chart of Node.js random_int](charts/node__random_int__25.png)

Deno is ```1.45%``` slower than  Node.js

### Five hundred random 16 character hex string
Generate five hundred random 16 character hex strings and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_hex.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_hex.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2344``` | ```2524``` | 
| Mean | ```1.03``` | ```1.09``` | 
| Median | ```1.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```3``` | ```3``` | 


![Chart of Deno random_hex](charts/deno__random_hex__1.png)
![Chart of Node.js random_hex](charts/node__random_hex__1.png)

Deno is ```7.13%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6183``` | ```9127``` | 
| Mean | ```4.20``` | ```5.33``` | 
| Median | ```3.00``` | ```5.00``` | 
| Min | ```0``` | ```1``` | 
| Max | ```15``` | ```30``` | 


![Chart of Deno random_hex](charts/deno__random_hex__10.png)
![Chart of Node.js random_hex](charts/node__random_hex__10.png)

Deno is ```32.26%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```16157``` | ```22854``` | 
| Mean | ```12.81``` | ```14.95``` | 
| Median | ```12.00``` | ```15.00``` | 
| Min | ```0``` | ```1``` | 
| Max | ```37``` | ```37``` | 


![Chart of Deno random_hex](charts/deno__random_hex__25.png)
![Chart of Node.js random_hex](charts/node__random_hex__25.png)

Deno is ```29.30%``` slower than  Node.js

### One hundred V1 UUIDs
Generate one hundred V1 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v1.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v1.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1173``` | ```1469``` | 
| Mean | ```0.49``` | ```0.75``` | 
| Median | ```0.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```2``` | ```3``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__1.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__1.png)

Deno is ```20.15%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3058``` | ```3896``` | 
| Mean | ```1.90``` | ```2.77``` | 
| Median | ```2.00``` | ```3.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```12``` | ```18``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__10.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__10.png)

Deno is ```21.51%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7759``` | ```10355``` | 
| Mean | ```5.75``` | ```7.94``` | 
| Median | ```5.00``` | ```8.00``` | 
| Min | ```0``` | ```1``` | 
| Max | ```19``` | ```26``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__25.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__25.png)

Deno is ```25.07%``` slower than  Node.js

### One hundred V4 UUIDs
Generate one hundred V4 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v4.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v4.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1561``` | ```2516``` | 
| Mean | ```0.86``` | ```1.71``` | 
| Median | ```1.00``` | ```2.00``` | 
| Min | ```0``` | ```1``` | 
| Max | ```8``` | ```6``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__1.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__1.png)

Deno is ```37.96%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4845``` | ```13179``` | 
| Mean | ```3.57``` | ```11.50``` | 
| Median | ```3.00``` | ```10.00``` | 
| Min | ```0``` | ```2``` | 
| Max | ```9``` | ```23``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__10.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__10.png)

Deno is ```63.24%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```11713``` | ```35736``` | 
| Mean | ```9.35``` | ```32.10``` | 
| Median | ```8.00``` | ```29.00``` | 
| Min | ```0``` | ```2``` | 
| Max | ```26``` | ```55``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__25.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__25.png)

Deno is ```67.22%``` slower than  Node.js

### One hundred V5 UUIDs
Generate one hundred V5 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v5.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v5.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1889``` | ```2406``` | 
| Mean | ```1.13``` | ```1.60``` | 
| Median | ```1.00``` | ```2.00``` | 
| Min | ```0``` | ```1``` | 
| Max | ```4``` | ```4``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__1.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__1.png)

Deno is ```21.49%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7024``` | ```10277``` | 
| Mean | ```5.37``` | ```8.71``` | 
| Median | ```5.00``` | ```9.00``` | 
| Min | ```0``` | ```2``` | 
| Max | ```19``` | ```14``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__10.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__10.png)

Deno is ```31.65%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```16605``` | ```29275``` | 
| Mean | ```14.20``` | ```26.15``` | 
| Median | ```14.00``` | ```27.00``` | 
| Min | ```0``` | ```2``` | 
| Max | ```35``` | ```56``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__25.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__25.png)

Deno is ```43.28%``` slower than  Node.js

### Parse five hundred strings
Parse five hundred strings containing integers and return parsed integers in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_parse_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_parse_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```875``` | ```1014``` | 
| Mean | ```0.43``` | ```0.41``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```2``` | ```2``` | 


![Chart of Deno parse_int](charts/deno__parse_int__1.png)
![Chart of Node.js parse_int](charts/node__parse_int__1.png)

Deno is ```13.71%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2469``` | ```2963``` | 
| Mean | ```1.62``` | ```1.88``` | 
| Median | ```1.00``` | ```2.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```11``` | ```21``` | 


![Chart of Deno parse_int](charts/deno__parse_int__10.png)
![Chart of Node.js parse_int](charts/node__parse_int__10.png)

Deno is ```16.67%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6198``` | ```7379``` | 
| Mean | ```4.66``` | ```4.81``` | 
| Median | ```4.00``` | ```4.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```23``` | ```22``` | 


![Chart of Deno parse_int](charts/deno__parse_int__25.png)
![Chart of Node.js parse_int](charts/node__parse_int__25.png)

Deno is ```16.00%``` slower than  Node.js

### Calculate mean of 500 numbers
Calculate mean of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_mean.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_mean.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```645``` | ```673``` | 
| Mean | ```0.38``` | ```0.41``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```2``` | ```2``` | 


![Chart of Deno mean](charts/deno__mean__1.png)
![Chart of Node.js mean](charts/node__mean__1.png)

Deno is ```4.16%``` slower than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1904``` | ```1966``` | 
| Mean | ```1.22``` | ```1.37``` | 
| Median | ```1.00``` | ```1.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```13``` | ```10``` | 


![Chart of Deno mean](charts/deno__mean__10.png)
![Chart of Node.js mean](charts/node__mean__10.png)

Deno is ```3.15%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4597``` | ```4682``` | 
| Mean | ```3.34``` | ```3.32``` | 
| Median | ```3.00``` | ```3.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```16``` | ```13``` | 


![Chart of Deno mean](charts/deno__mean__25.png)
![Chart of Node.js mean](charts/node__mean__25.png)

Deno is ```1.82%``` slower than  Node.js

### Calculate median of 500 numbers
Calculate median of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_median.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_median.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```729``` | ```720``` | 
| Mean | ```0.46``` | ```0.47``` | 
| Median | ```0.00``` | ```0.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```2``` | ```2``` | 


![Chart of Deno median](charts/deno__median__1.png)
![Chart of Node.js median](charts/node__median__1.png)

Deno is ```1.23%``` faster than  Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2366``` | ```2500``` | 
| Mean | ```1.74``` | ```1.94``` | 
| Median | ```2.00``` | ```2.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```9``` | ```13``` | 


![Chart of Deno median](charts/deno__median__10.png)
![Chart of Node.js median](charts/node__median__10.png)

Deno is ```5.36%``` slower than  Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5695``` | ```6877``` | 
| Mean | ```4.56``` | ```5.76``` | 
| Median | ```4.00``` | ```6.00``` | 
| Min | ```0``` | ```0``` | 
| Max | ```16``` | ```33``` | 


![Chart of Deno median](charts/deno__median__25.png)
![Chart of Node.js median](charts/node__median__25.png)

Deno is ```17.19%``` slower than  Node.js
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