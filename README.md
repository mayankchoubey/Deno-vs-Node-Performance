# Deno vs Node.js performance benchmarking

## Introduction

Deno is a simple, modern, and secure runtime for JavaScript and TypeScript. Deno is sandboxed and supports Typescript out of the box. Deno is built over Google's V8 engine and uses Rust. The first major release of Deno was in May 2020.

Node.js is a very popular battle-tested runtime for Javascript. Node.js has been around for more than 11 years. Node.js is built over the same Google's V8 engine, but uses C++.

Functionally, Deno is same as Node.js.

Until now, whenever there was a need for a JS based server runtime, there was only Node.js. However, now onwards, there would always be two options: Node.js or Deno?

It is very unlikely that existing Node.js apps will be ported to Deno. That's too much of work, and there won't be any significant gain. But it is very likely that people **could** consider Deno for newer apps.

If both are functionally same, what could the primary factors to consider Deno over Node.js? 
* Reliability
* Performance
* (could be more ....)

Reliability would be discussed separately. The focus of this page is performance.

So, is Deno ready for prime time? Can it perform as good as or better than Node.js? If Deno can't perform as good as Node.js, it can never become a major challenge to the Node.js empire.

The purpose of this repository/page is to continually run and report on tests that compares Deno's performance against Node.js. The plan is to keep this repository/page updated as soon as there are new releases on either Deno or Node.js. The frequency would likely be weekly.



### Versions
Deno: ```1.6.3```

Node.js: ```15.6.0```

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
| ```Write 500 console logs``` | Write 500 lines on the console, and return number of lines in response. |  
| ```A simple API proxy``` | Receive request, increment, and send it to a faux server. Receive response, increment, and send it back. |  
| ```Multipart/form-data with fields``` | Receive multipart/form-data and return parsed fields in JSON. |  
| ```A simple message exchange over UDP``` | Receive a message over UDP, and echo it back. |  
| ```A simple message exchange over WebSocket``` | Receive a message over WebSocket, and echo it back. |  

## Tests and Results



### Hello world!
This one is a very simple hello world program. It responds to a GET request with a JSON containing a string Hello World!
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```958``` | ```998``` | 
| ReqPerSec | ```1043``` | ```1002``` | 
| Mean | ```0.29``` | ```0.33``` | 
| Median | ```0.27``` | ```0.3``` | 
| Min | ```0.236``` | ```0.255``` | 
| Max | ```1.311``` | ```1.945``` | 


![Chart of Deno hello_world](charts/deno__hello_world__1.png)
![Chart of Node.js hello_world](charts/node__hello_world__1.png)

Deno is ```4.01%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3124``` | ```3085``` | 
| ReqPerSec | ```3201``` | ```3241``` | 
| Mean | ```1.13``` | ```1.03``` | 
| Median | ```1.02``` | ```0.92``` | 
| Min | ```0.223``` | ```0.245``` | 
| Max | ```13.776``` | ```20.579``` | 


![Chart of Deno hello_world](charts/deno__hello_world__10.png)
![Chart of Node.js hello_world](charts/node__hello_world__10.png)

Deno is ```1.25%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7507``` | ```7285``` | 
| ReqPerSec | ```3330``` | ```3431``` | 
| Mean | ```3.09``` | ```2.61``` | 
| Median | ```2.86``` | ```2.26``` | 
| Min | ```0.241``` | ```0.326``` | 
| Max | ```93.622``` | ```90.201``` | 


![Chart of Deno hello_world](charts/deno__hello_world__25.png)
![Chart of Node.js hello_world](charts/node__hello_world__25.png)

Deno is ```2.96%``` faster than Node.js

### Hello world with frameworks - oak and express
Hello world program using the popular frameworks: Oak/Deno, Express/Node.js
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world_oak_exp.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world_oak_exp.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1082``` | ```1008``` | 
| ReqPerSec | ```924``` | ```992``` | 
| Mean | ```0.42``` | ```0.36``` | 
| Median | ```0.39``` | ```0.33``` | 
| Min | ```0.351``` | ```0.28``` | 
| Max | ```1.811``` | ```2.218``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__1.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__1.png)

Deno is ```6.84%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3822``` | ```3211``` | 
| ReqPerSec | ```2616``` | ```3114``` | 
| Mean | ```1.79``` | ```1.15``` | 
| Median | ```1.53``` | ```1.03``` | 
| Min | ```0.314``` | ```0.252``` | 
| Max | ```25.555``` | ```21.216``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__10.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__10.png)

Deno is ```15.99%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```9190``` | ```7512``` | 
| ReqPerSec | ```2720``` | ```3328``` | 
| Mean | ```4.72``` | ```2.83``` | 
| Median | ```4.44``` | ```2.63``` | 
| Min | ```0.336``` | ```0.386``` | 
| Max | ```77.604``` | ```105.727``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__25.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__25.png)

Deno is ```18.26%``` faster than Node.js

### Echo name over HTTPS
A simple echo name program that runs over HTTPS
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_https_hello_name.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_https_hello_name.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1086``` | ```1113``` | 
| ReqPerSec | ```920``` | ```898``` | 
| Mean | ```0.4``` | ```0.45``` | 
| Median | ```0.37``` | ```0.42``` | 
| Min | ```0.314``` | ```0.344``` | 
| Max | ```2.646``` | ```1.908``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__1.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__1.png)

Deno is ```2.43%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3503``` | ```3419``` | 
| ReqPerSec | ```2854``` | ```2924``` | 
| Mean | ```1.35``` | ```1.43``` | 
| Median | ```1.14``` | ```1.32``` | 
| Min | ```0.288``` | ```0.327``` | 
| Max | ```11.432``` | ```24.103``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__10.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__10.png)

Deno is ```2.40%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```8627``` | ```9158``` | 
| ReqPerSec | ```2897``` | ```2729``` | 
| Mean | ```4.08``` | ```4.21``` | 
| Median | ```3.91``` | ```3.75``` | 
| Min | ```0.321``` | ```0.532``` | 
| Max | ```144.908``` | ```60.893``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__25.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__25.png)

Deno is ```5.80%``` slower than Node.js

### Five hundred random integers
Generate five hundred random integers and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1349``` | ```1363``` | 
| ReqPerSec | ```741``` | ```733``` | 
| Mean | ```0.43``` | ```0.45``` | 
| Median | ```0.4``` | ```0.41``` | 
| Min | ```0.302``` | ```0.33``` | 
| Max | ```2``` | ```2.063``` | 


![Chart of Deno random_int](charts/deno__random_int__1.png)
![Chart of Node.js random_int](charts/node__random_int__1.png)

Deno is ```1.03%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3939``` | ```4181``` | 
| ReqPerSec | ```2538``` | ```2391``` | 
| Mean | ```1.52``` | ```1.62``` | 
| Median | ```1.32``` | ```1.46``` | 
| Min | ```0.293``` | ```0.304``` | 
| Max | ```11.935``` | ```20.745``` | 


![Chart of Deno random_int](charts/deno__random_int__10.png)
![Chart of Node.js random_int](charts/node__random_int__10.png)

Deno is ```5.79%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```10026``` | ```9975``` | 
| ReqPerSec | ```2493``` | ```2506``` | 
| Mean | ```5.1``` | ```4.18``` | 
| Median | ```4.77``` | ```3.86``` | 
| Min | ```0.369``` | ```0.442``` | 
| Max | ```76.723``` | ```48.755``` | 


![Chart of Deno random_int](charts/deno__random_int__25.png)
![Chart of Node.js random_int](charts/node__random_int__25.png)

Deno is ```0.51%``` faster than Node.js

### Five hundred random 16 character hex string
Generate five hundred random 16 character hex strings and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_hex.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_hex.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2804``` | ```2889``` | 
| ReqPerSec | ```356``` | ```346``` | 
| Mean | ```1.09``` | ```1.08``` | 
| Median | ```1.02``` | ```1.02``` | 
| Min | ```0.868``` | ```0.833``` | 
| Max | ```2.307``` | ```2.596``` | 


![Chart of Deno random_hex](charts/deno__random_hex__1.png)
![Chart of Node.js random_hex](charts/node__random_hex__1.png)

Deno is ```2.94%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7940``` | ```9950``` | 
| ReqPerSec | ```1259``` | ```1005``` | 
| Mean | ```4.46``` | ```4.96``` | 
| Median | ```3.52``` | ```5.16``` | 
| Min | ```0.83``` | ```0.865``` | 
| Max | ```13.669``` | ```13.486``` | 


![Chart of Deno random_hex](charts/deno__random_hex__10.png)
![Chart of Node.js random_hex](charts/node__random_hex__10.png)

Deno is ```20.20%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```20819``` | ```26565``` | 
| ReqPerSec | ```1200``` | ```941``` | 
| Mean | ```14.12``` | ```15.37``` | 
| Median | ```12.89``` | ```16.1``` | 
| Min | ```0.808``` | ```1.576``` | 
| Max | ```42.01``` | ```33.276``` | 


![Chart of Deno random_hex](charts/deno__random_hex__25.png)
![Chart of Node.js random_hex](charts/node__random_hex__25.png)

Deno is ```21.63%``` slower than Node.js

### One hundred V1 UUIDs
Generate one hundred V1 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v1.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v1.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1703``` | ```1844``` | 
| ReqPerSec | ```587``` | ```542``` | 
| Mean | ```0.59``` | ```0.71``` | 
| Median | ```0.55``` | ```0.68``` | 
| Min | ```0.462``` | ```0.49``` | 
| Max | ```2.152``` | ```2.932``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__1.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__1.png)

Deno is ```7.65%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4485``` | ```5105``` | 
| ReqPerSec | ```2229``` | ```1958``` | 
| Mean | ```1.95``` | ```2.57``` | 
| Median | ```1.67``` | ```2.36``` | 
| Min | ```0.379``` | ```0.519``` | 
| Max | ```12.556``` | ```21.504``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__10.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__10.png)

Deno is ```12.14%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```11757``` | ```13913``` | 
| ReqPerSec | ```2126``` | ```1796``` | 
| Mean | ```6.38``` | ```8.37``` | 
| Median | ```6``` | ```8.88``` | 
| Min | ```0.436``` | ```0.923``` | 
| Max | ```129.146``` | ```27.987``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__25.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__25.png)

Deno is ```15.50%``` slower than Node.js

### One hundred V4 UUIDs
Generate one hundred V4 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v4.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v4.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1959``` | ```2977``` | 
| ReqPerSec | ```510``` | ```335``` | 
| Mean | ```0.83``` | ```1.76``` | 
| Median | ```0.77``` | ```1.54``` | 
| Min | ```0.649``` | ```1.244``` | 
| Max | ```2.743``` | ```5.537``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__1.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__1.png)

Deno is ```34.20%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5778``` | ```14374``` | 
| ReqPerSec | ```1730``` | ```695``` | 
| Mean | ```3.21``` | ```11.34``` | 
| Median | ```2.83``` | ```9.51``` | 
| Min | ```0.549``` | ```2.276``` | 
| Max | ```14.157``` | ```33.858``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__10.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__10.png)

Deno is ```59.80%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```15372``` | ```39503``` | 
| ReqPerSec | ```1626``` | ```632``` | 
| Mean | ```9.8``` | ```32.84``` | 
| Median | ```8.87``` | ```29.51``` | 
| Min | ```0.612``` | ```1.656``` | 
| Max | ```51.997``` | ```60.057``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__25.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__25.png)

Deno is ```61.09%``` slower than Node.js

### One hundred V5 UUIDs
Generate one hundred V5 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v5.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v5.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2194``` | ```2801``` | 
| ReqPerSec | ```455``` | ```357``` | 
| Mean | ```1.07``` | ```1.59``` | 
| Median | ```0.93``` | ```1.56``` | 
| Min | ```0.808``` | ```1.236``` | 
| Max | ```3.696``` | ```3.825``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__1.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__1.png)

Deno is ```21.67%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```8437``` | ```12095``` | 
| ReqPerSec | ```1185``` | ```826``` | 
| Mean | ```5.46``` | ```9.13``` | 
| Median | ```5.36``` | ```8.87``` | 
| Min | ```0.759``` | ```3.088``` | 
| Max | ```24.015``` | ```13.408``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__10.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__10.png)

Deno is ```30.24%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```20323``` | ```32147``` | 
| ReqPerSec | ```1230``` | ```777``` | 
| Mean | ```14.37``` | ```26.02``` | 
| Median | ```14.31``` | ```26.7``` | 
| Min | ```0.743``` | ```1.469``` | 
| Max | ```71.73``` | ```46.035``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__25.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__25.png)

Deno is ```36.78%``` slower than Node.js

### Parse five hundred strings
Parse five hundred strings containing integers and return parsed integers in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_parse_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_parse_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1282``` | ```1563``` | 
| ReqPerSec | ```780``` | ```639``` | 
| Mean | ```0.43``` | ```0.54``` | 
| Median | ```0.39``` | ```0.53``` | 
| Min | ```0.339``` | ```0.351``` | 
| Max | ```1.841``` | ```2.085``` | 


![Chart of Deno parse_int](charts/deno__parse_int__1.png)
![Chart of Node.js parse_int](charts/node__parse_int__1.png)

Deno is ```17.98%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3894``` | ```4337``` | 
| ReqPerSec | ```2568``` | ```2305``` | 
| Mean | ```1.6``` | ```1.84``` | 
| Median | ```1.43``` | ```1.72``` | 
| Min | ```0.323``` | ```0.407``` | 
| Max | ```11.695``` | ```21.427``` | 


![Chart of Deno parse_int](charts/deno__parse_int__10.png)
![Chart of Node.js parse_int](charts/node__parse_int__10.png)

Deno is ```10.21%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```10074``` | ```10905``` | 
| ReqPerSec | ```2481``` | ```2292``` | 
| Mean | ```5.21``` | ```5.17``` | 
| Median | ```4.89``` | ```4.84``` | 
| Min | ```0.365``` | ```0.523``` | 
| Max | ```93.654``` | ```160.643``` | 


![Chart of Deno parse_int](charts/deno__parse_int__25.png)
![Chart of Node.js parse_int](charts/node__parse_int__25.png)

Deno is ```7.62%``` slower than Node.js

### Calculate mean of 500 numbers
Calculate mean of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_mean.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_mean.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1071``` | ```1068``` | 
| ReqPerSec | ```933``` | ```936``` | 
| Mean | ```0.39``` | ```0.41``` | 
| Median | ```0.37``` | ```0.38``` | 
| Min | ```0.305``` | ```0.317``` | 
| Max | ```1.994``` | ```1.934``` | 


![Chart of Deno mean](charts/deno__mean__1.png)
![Chart of Node.js mean](charts/node__mean__1.png)

Deno is ```0.28%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3298``` | ```3295``` | 
| ReqPerSec | ```3032``` | ```3034``` | 
| Mean | ```1.28``` | ```1.33``` | 
| Median | ```1.2``` | ```1.23``` | 
| Min | ```0.272``` | ```0.299``` | 
| Max | ```10.861``` | ```18.11``` | 


![Chart of Deno mean](charts/deno__mean__10.png)
![Chart of Node.js mean](charts/node__mean__10.png)

Deno is ```0.09%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```8375``` | ```7930``` | 
| ReqPerSec | ```2985``` | ```3152``` | 
| Mean | ```3.88``` | ```3.31``` | 
| Median | ```3.57``` | ```3.15``` | 
| Min | ```0.291``` | ```0.425``` | 
| Max | ```38.153``` | ```22.208``` | 


![Chart of Deno mean](charts/deno__mean__25.png)
![Chart of Node.js mean](charts/node__mean__25.png)

Deno is ```5.31%``` faster than Node.js

### Calculate median of 500 numbers
Calculate median of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_median.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_median.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1169``` | ```1147``` | 
| ReqPerSec | ```855``` | ```871``` | 
| Mean | ```0.48``` | ```0.48``` | 
| Median | ```0.45``` | ```0.45``` | 
| Min | ```0.39``` | ```0.398``` | 
| Max | ```2.145``` | ```1.984``` | 


![Chart of Deno median](charts/deno__median__1.png)
![Chart of Node.js median](charts/node__median__1.png)

Deno is ```1.88%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3662``` | ```3801``` | 
| ReqPerSec | ```2730``` | ```2630``` | 
| Mean | ```1.63``` | ```1.8``` | 
| Median | ```1.37``` | ```1.69``` | 
| Min | ```0.371``` | ```0.399``` | 
| Max | ```11.213``` | ```23.837``` | 


![Chart of Deno median](charts/deno__median__10.png)
![Chart of Node.js median](charts/node__median__10.png)

Deno is ```3.66%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```9261``` | ```10125``` | 
| ReqPerSec | ```2699``` | ```2469``` | 
| Mean | ```4.84``` | ```5.71``` | 
| Median | ```4.66``` | ```5.88``` | 
| Min | ```0.367``` | ```0.623``` | 
| Max | ```53.106``` | ```159.235``` | 


![Chart of Deno median](charts/deno__median__25.png)
![Chart of Node.js median](charts/node__median__25.png)

Deno is ```8.53%``` slower than Node.js

### Write 500 console logs
Write 500 lines on the console, and return number of lines in response.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_console_log.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_console_log.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2757``` | ```2249``` | 
| ReqPerSec | ```362``` | ```444``` | 
| Mean | ```1.92``` | ```1.51``` | 
| Median | ```1.87``` | ```1.48``` | 
| Min | ```1.69``` | ```1.328``` | 
| Max | ```2.854``` | ```3.133``` | 


![Chart of Deno console_log](charts/deno__console_log__1.png)
![Chart of Node.js console_log](charts/node__console_log__1.png)

Deno is ```18.43%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```18547``` | ```12661``` | 
| ReqPerSec | ```539``` | ```789``` | 
| Mean | ```14.5``` | ```10.09``` | 
| Median | ```14.28``` | ```10.09``` | 
| Min | ```2.066``` | ```1.499``` | 
| Max | ```32.346``` | ```41.488``` | 


![Chart of Deno console_log](charts/deno__console_log__10.png)
![Chart of Node.js console_log](charts/node__console_log__10.png)

Deno is ```31.74%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```23902``` | ```32769``` | 
| ReqPerSec | ```1045``` | ```762``` | 
| Mean | ```17.82``` | ```27.06``` | 
| Median | ```12.65``` | ```27.8``` | 
| Min | ```0.701``` | ```2.052``` | 
| Max | ```2787.09``` | ```34.666``` | 


![Chart of Deno console_log](charts/deno__console_log__25.png)
![Chart of Node.js console_log](charts/node__console_log__25.png)

Deno is ```27.06%``` slower than Node.js

### Multipart/form-data with fields
Receive multipart/form-data and return parsed fields in JSON.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_multipart_fd.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_multipart_fd.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1259``` | ```8020``` | 
| ReqPerSec | ```794``` | ```124``` | 
| Mean | ```0.55``` | ```6.94``` | 
| Median | ```0.49``` | ```6.07``` | 
| Min | ```0.41``` | ```5.315``` | 
| Max | ```2.989``` | ```11.544``` | 


![Chart of Deno form_data_fields](charts/deno__form_data_fields__1.png)
![Chart of Node.js form_data_fields](charts/node__form_data_fields__1.png)

Deno is ```84.30%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3933``` | ```82966``` | 
| ReqPerSec | ```2542``` | ```120``` | 
| Mean | ```1.76``` | ```77.05``` | 
| Median | ```1.52``` | ```77.36``` | 
| Min | ```0.312``` | ```14.571``` | 
| Max | ```12.137``` | ```88.179``` | 


![Chart of Deno form_data_fields](charts/deno__form_data_fields__10.png)
![Chart of Node.js form_data_fields](charts/node__form_data_fields__10.png)

Deno is ```95.26%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```9567``` | ```226426``` | 
| ReqPerSec | ```2613``` | ```110``` | 
| Mean | ```4.81``` | ```211.05``` | 
| Median | ```4.36``` | ```211.19``` | 
| Min | ```0.329``` | ```20.3``` | 
| Max | ```196.347``` | ```250.421``` | 


![Chart of Deno form_data_fields](charts/deno__form_data_fields__25.png)
![Chart of Node.js form_data_fields](charts/node__form_data_fields__25.png)

Deno is ```95.77%``` slower than Node.js

### A simple message exchange over UDP
Receive a message over UDP, and echo it back.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_udp_server.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_udp_server.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```645``` | ```718``` | 
| ReqPerSec | ```1550``` | ```1392``` | 
| Mean | ```0.21``` | ```0.28``` | 
| Median | ```0.2``` | ```0.26``` | 
| Min | ```0.186``` | ```0.237``` | 
| Max | ```0.93``` | ```1.616``` | 


![Chart of Deno udp_server](charts/deno__udp_server__1.png)
![Chart of Node.js udp_server](charts/node__udp_server__1.png)

Deno is ```10.17%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2469``` | ```2835``` | 
| ReqPerSec | ```4050``` | ```3527``` | 
| Mean | ```0.84``` | ```1.21``` | 
| Median | ```0.6``` | ```1.17``` | 
| Min | ```0.206``` | ```0.241``` | 
| Max | ```105.174``` | ```73.074``` | 


![Chart of Deno udp_server](charts/deno__udp_server__10.png)
![Chart of Node.js udp_server](charts/node__udp_server__10.png)

Deno is ```12.91%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6491``` | ```7923``` | 
| ReqPerSec | ```3851``` | ```3155``` | 
| Mean | ```2.74``` | ```4.21``` | 
| Median | ```2.53``` | ```3.91``` | 
| Min | ```0.21``` | ```0.273``` | 
| Max | ```135.535``` | ```397.219``` | 


![Chart of Deno udp_server](charts/deno__udp_server__25.png)
![Chart of Node.js udp_server](charts/node__udp_server__25.png)

Deno is ```18.07%``` slower than Node.js

### A simple message exchange over WebSocket
Receive a message over WebSocket, and echo it back.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_ws_server.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_ws_server.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1806``` | ```8609``` | 
| ReqPerSec | ```553``` | ```116``` | 
| Mean | ```1.3``` | ```8.1``` | 
| Median | ```1.22``` | ```1.13``` | 
| Min | ```1.02``` | ```0.913``` | 
| Max | ```4.05``` | ```1918.295``` | 


![Chart of Deno ws_server](charts/deno__ws_server__1.png)
![Chart of Node.js ws_server](charts/node__ws_server__1.png)

Deno is ```79.02%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6350``` | ```97763``` | 
| ReqPerSec | ```1574``` | ```102``` | 
| Mean | ```4.54``` | ```91.15``` | 
| Median | ```4.35``` | ```4.4``` | 
| Min | ```1.079``` | ```0.927``` | 
| Max | ```42.63``` | ```1973.337``` | 


![Chart of Deno ws_server](charts/deno__ws_server__10.png)
![Chart of Node.js ws_server](charts/node__ws_server__10.png)

Deno is ```93.50%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```15973``` | ```242488``` | 
| ReqPerSec | ```1565``` | ```103``` | 
| Mean | ```11.6``` | ```224.69``` | 
| Median | ```11.31``` | ```10.97``` | 
| Min | ```0.968``` | ```1.012``` | 
| Max | ```165.892``` | ```2002.718``` | 


![Chart of Deno ws_server](charts/deno__ws_server__25.png)
![Chart of Node.js ws_server](charts/node__ws_server__25.png)

Deno is ```93.41%``` slower than Node.js
## Next steps

There is a lot more work to be done! If you like to suggest more benchmarks, please add an issue with your suggestions.

Also, please add a star to this repository if it has been valuable. More stars means more readers and this would encourage us to keep the benchmark running.
