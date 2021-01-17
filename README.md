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

## Tests and Results



### Hello world!
This one is a very simple hello world program. It responds to a GET request with a JSON containing a string Hello World!
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```556``` | ```588``` | 
| ReqPerSec | ```1798``` | ```1700``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.237``` | ```0.256``` | 
| Max | ```1.271``` | ```4.361``` | 


![Chart of Deno hello_world](charts/deno__hello_world__1.png)
![Chart of Node.js hello_world](charts/node__hello_world__1.png)

Deno is ```5.44%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1777``` | ```1741``` | 
| ReqPerSec | ```5627``` | ```5743``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```0``` | 
| Min | ```0.275``` | ```0.248``` | 
| Max | ```10.461``` | ```6.552``` | 


![Chart of Deno hello_world](charts/deno__hello_world__10.png)
![Chart of Node.js hello_world](charts/node__hello_world__10.png)

Deno is ```2.03%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4308``` | ```3969``` | 
| ReqPerSec | ```5803``` | ```6298``` | 
| Mean | ```3``` | ```2``` | 
| Median | ```2``` | ```2``` | 
| Min | ```0.22``` | ```0.511``` | 
| Max | ```15.678``` | ```20.028``` | 


![Chart of Deno hello_world](charts/deno__hello_world__25.png)
![Chart of Node.js hello_world](charts/node__hello_world__25.png)

Deno is ```7.87%``` faster than Node.js

### Hello world with frameworks - oak and express
Hello world program using the popular frameworks: Oak/Deno, Express/Node.js
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world_oak_exp.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world_oak_exp.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```710``` | ```633``` | 
| ReqPerSec | ```1408``` | ```1579``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.354``` | ```0.282``` | 
| Max | ```1.892``` | ```2.013``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__1.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__1.png)

Deno is ```10.85%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2416``` | ```1836``` | 
| ReqPerSec | ```4139``` | ```5446``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.319``` | ```0.268``` | 
| Max | ```12.962``` | ```14.936``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__10.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__10.png)

Deno is ```24.01%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5862``` | ```4194``` | 
| ReqPerSec | ```4264``` | ```5960``` | 
| Mean | ```4``` | ```2``` | 
| Median | ```4``` | ```2``` | 
| Min | ```0.287``` | ```0.487``` | 
| Max | ```26.171``` | ```17.604``` | 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__25.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__25.png)

Deno is ```28.45%``` faster than Node.js

### Echo name over HTTPS
A simple echo name program that runs over HTTPS
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_https_hello_name.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_https_hello_name.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```699``` | ```724``` | 
| ReqPerSec | ```1430``` | ```1381``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.313``` | ```0.353``` | 
| Max | ```2.624``` | ```1.941``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__1.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__1.png)

Deno is ```3.45%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2150``` | ```2136``` | 
| ReqPerSec | ```4651``` | ```4681``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.308``` | ```0.461``` | 
| Max | ```11.234``` | ```6.221``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__10.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__10.png)

Deno is ```0.65%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5112``` | ```4852``` | 
| ReqPerSec | ```4890``` | ```5152``` | 
| Mean | ```3``` | ```3``` | 
| Median | ```3``` | ```3``` | 
| Min | ```0.302``` | ```0.5``` | 
| Max | ```22.776``` | ```19.8``` | 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__25.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__25.png)

Deno is ```5.09%``` faster than Node.js

### Five hundred random integers
Generate five hundred random integers and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```967``` | ```929``` | 
| ReqPerSec | ```1034``` | ```1076``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.305``` | ```0.318``` | 
| Max | ```1.794``` | ```1.967``` | 


![Chart of Deno random_int](charts/deno__random_int__1.png)
![Chart of Node.js random_int](charts/node__random_int__1.png)

Deno is ```3.93%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2578``` | ```2636``` | 
| ReqPerSec | ```3878``` | ```3793``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.335``` | ```0.38``` | 
| Max | ```11.753``` | ```22.972``` | 


![Chart of Deno random_int](charts/deno__random_int__10.png)
![Chart of Node.js random_int](charts/node__random_int__10.png)

Deno is ```2.20%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6452``` | ```6346``` | 
| ReqPerSec | ```3874``` | ```3939``` | 
| Mean | ```4``` | ```3``` | 
| Median | ```4``` | ```3``` | 
| Min | ```0.379``` | ```0.552``` | 
| Max | ```18.925``` | ```20.158``` | 


![Chart of Deno random_int](charts/deno__random_int__25.png)
![Chart of Node.js random_int](charts/node__random_int__25.png)

Deno is ```1.64%``` faster than Node.js

### Five hundred random 16 character hex string
Generate five hundred random 16 character hex strings and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_hex.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_hex.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2420``` | ```2513``` | 
| ReqPerSec | ```413``` | ```397``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.864``` | ```0.836``` | 
| Max | ```2.341``` | ```3.039``` | 


![Chart of Deno random_hex](charts/deno__random_hex__1.png)
![Chart of Node.js random_hex](charts/node__random_hex__1.png)

Deno is ```3.70%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6849``` | ```8992``` | 
| ReqPerSec | ```1460``` | ```1112``` | 
| Mean | ```4``` | ```5``` | 
| Median | ```3``` | ```5``` | 
| Min | ```0.902``` | ```0.851``` | 
| Max | ```25.02``` | ```12.17``` | 


![Chart of Deno random_hex](charts/deno__random_hex__10.png)
![Chart of Node.js random_hex](charts/node__random_hex__10.png)

Deno is ```23.83%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```16926``` | ```23330``` | 
| ReqPerSec | ```1477``` | ```1071``` | 
| Mean | ```13``` | ```15``` | 
| Median | ```12``` | ```15``` | 
| Min | ```0.838``` | ```1.675``` | 
| Max | ```40.497``` | ```33.471``` | 


![Chart of Deno random_hex](charts/deno__random_hex__25.png)
![Chart of Node.js random_hex](charts/node__random_hex__25.png)

Deno is ```27.45%``` slower than Node.js

### One hundred V1 UUIDs
Generate one hundred V1 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v1.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v1.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1286``` | ```1296``` | 
| ReqPerSec | ```777``` | ```771``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.428``` | ```0.472``` | 
| Max | ```2.375``` | ```2.557``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__1.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__1.png)

Deno is ```0.77%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```3111``` | ```3828``` | 
| ReqPerSec | ```3214``` | ```2612``` | 
| Mean | ```1``` | ```2``` | 
| Median | ```1``` | ```2``` | 
| Min | ```0.391``` | ```0.584``` | 
| Max | ```12.002``` | ```15.128``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__10.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__10.png)

Deno is ```18.73%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7942``` | ```10587``` | 
| ReqPerSec | ```3147``` | ```2361``` | 
| Mean | ```5``` | ```8``` | 
| Median | ```5``` | ```8``` | 
| Min | ```0.398``` | ```0.578``` | 
| Max | ```20.062``` | ```26.545``` | 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__25.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__25.png)

Deno is ```24.98%``` slower than Node.js

### One hundred V4 UUIDs
Generate one hundred V4 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v4.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v4.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1585``` | ```2507``` | 
| ReqPerSec | ```630``` | ```398``` | 
| Mean | ```0``` | ```1``` | 
| Median | ```0``` | ```1``` | 
| Min | ```0.666``` | ```1.202``` | 
| Max | ```2.178``` | ```5.464``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__1.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__1.png)

Deno is ```36.78%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4516``` | ```13014``` | 
| ReqPerSec | ```2214``` | ```768``` | 
| Mean | ```3``` | ```11``` | 
| Median | ```2``` | ```9``` | 
| Min | ```0.652``` | ```1.573``` | 
| Max | ```11.543``` | ```21.815``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__10.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__10.png)

Deno is ```65.30%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```11484``` | ```36922``` | 
| ReqPerSec | ```2176``` | ```677``` | 
| Mean | ```9``` | ```33``` | 
| Median | ```8``` | ```30``` | 
| Min | ```0.618``` | ```2.118``` | 
| Max | ```28.051``` | ```55.516``` | 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__25.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__25.png)

Deno is ```68.90%``` slower than Node.js

### One hundred V5 UUIDs
Generate one hundred V5 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v5.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v5.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1846``` | ```2435``` | 
| ReqPerSec | ```541``` | ```410``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```0``` | ```1``` | 
| Min | ```0.819``` | ```1.218``` | 
| Max | ```4.096``` | ```4.148``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__1.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__1.png)

Deno is ```24.19%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```7267``` | ```10885``` | 
| ReqPerSec | ```1376``` | ```918``` | 
| Mean | ```5``` | ```9``` | 
| Median | ```4``` | ```8``` | 
| Min | ```0.746``` | ```2.069``` | 
| Max | ```13.714``` | ```13.524``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__10.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__10.png)

Deno is ```33.24%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```17304``` | ```31259``` | 
| ReqPerSec | ```1444``` | ```799``` | 
| Mean | ```14``` | ```28``` | 
| Median | ```14``` | ```28``` | 
| Min | ```0.758``` | ```1.849``` | 
| Max | ```38.648``` | ```45.367``` | 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__25.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__25.png)

Deno is ```44.64%``` slower than Node.js

### Parse five hundred strings
Parse five hundred strings containing integers and return parsed integers in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_parse_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_parse_int.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```906``` | ```1131``` | 
| ReqPerSec | ```1103``` | ```884``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.341``` | ```0.359``` | 
| Max | ```1.766``` | ```2.236``` | 


![Chart of Deno parse_int](charts/deno__parse_int__1.png)
![Chart of Node.js parse_int](charts/node__parse_int__1.png)

Deno is ```19.89%``` slower than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2501``` | ```2979``` | 
| ReqPerSec | ```3998``` | ```3356``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.369``` | ```0.397``` | 
| Max | ```11.034``` | ```22.004``` | 


![Chart of Deno parse_int](charts/deno__parse_int__10.png)
![Chart of Node.js parse_int](charts/node__parse_int__10.png)

Deno is ```16.05%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```6496``` | ```7418``` | 
| ReqPerSec | ```3848``` | ```3370``` | 
| Mean | ```4``` | ```4``` | 
| Median | ```4``` | ```4``` | 
| Min | ```0.333``` | ```1.137``` | 
| Max | ```23.966``` | ```21.747``` | 


![Chart of Deno parse_int](charts/deno__parse_int__25.png)
![Chart of Node.js parse_int](charts/node__parse_int__25.png)

Deno is ```12.43%``` slower than Node.js

### Calculate mean of 500 numbers
Calculate mean of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_mean.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_mean.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```690``` | ```688``` | 
| ReqPerSec | ```1449``` | ```1453``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.305``` | ```0.32``` | 
| Max | ```2.056``` | ```1.907``` | 


![Chart of Deno mean](charts/deno__mean__1.png)
![Chart of Node.js mean](charts/node__mean__1.png)

Deno is ```0.29%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```1967``` | ```2065``` | 
| ReqPerSec | ```5083``` | ```4842``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.292``` | ```0.394``` | 
| Max | ```11.176``` | ```10.908``` | 


![Chart of Deno mean](charts/deno__mean__10.png)
![Chart of Node.js mean](charts/node__mean__10.png)

Deno is ```4.75%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```4868``` | ```4920``` | 
| ReqPerSec | ```5135``` | ```5081``` | 
| Mean | ```3``` | ```3``` | 
| Median | ```3``` | ```3``` | 
| Min | ```0.265``` | ```0.609``` | 
| Max | ```14.573``` | ```21.121``` | 


![Chart of Deno mean](charts/deno__mean__25.png)
![Chart of Node.js mean](charts/node__mean__25.png)

Deno is ```1.06%``` slower than Node.js

### Calculate median of 500 numbers
Calculate median of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_median.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_median.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```762``` | ```755``` | 
| ReqPerSec | ```1312``` | ```1324``` | 
| Mean | ```0``` | ```0``` | 
| Median | ```0``` | ```0``` | 
| Min | ```0.391``` | ```0.401``` | 
| Max | ```2.274``` | ```2.002``` | 


![Chart of Deno median](charts/deno__median__1.png)
![Chart of Node.js median](charts/node__median__1.png)

Deno is ```0.92%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2390``` | ```2571``` | 
| ReqPerSec | ```4184``` | ```3889``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```0.363``` | ```0.419``` | 
| Max | ```10.547``` | ```11.467``` | 


![Chart of Deno median](charts/deno__median__10.png)
![Chart of Node.js median](charts/node__median__10.png)

Deno is ```7.04%``` slower than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```5950``` | ```7341``` | 
| ReqPerSec | ```4201``` | ```3405``` | 
| Mean | ```4``` | ```6``` | 
| Median | ```4``` | ```6``` | 
| Min | ```0.351``` | ```0.562``` | 
| Max | ```17.039``` | ```18.701``` | 


![Chart of Deno median](charts/deno__median__25.png)
![Chart of Node.js median](charts/node__median__25.png)

Deno is ```18.95%``` slower than Node.js

### Write 500 console logs
Write 500 lines on the console, and return number of lines in response.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_console_log.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_console_log.js)
#### Concurrency=1
Total requests: ```1000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```2383``` | ```1842``` | 
| ReqPerSec | ```419``` | ```542``` | 
| Mean | ```1``` | ```1``` | 
| Median | ```1``` | ```1``` | 
| Min | ```1.752``` | ```1.312``` | 
| Max | ```2.796``` | ```3.334``` | 


![Chart of Deno console_log](charts/deno__console_log__1.png)
![Chart of Node.js console_log](charts/node__console_log__1.png)

Deno is ```22.70%``` faster than Node.js
#### Concurrency=10
Total requests: ```10000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```17324``` | ```11389``` | 
| ReqPerSec | ```577``` | ```878``` | 
| Mean | ```14``` | ```10``` | 
| Median | ```14``` | ```10``` | 
| Min | ```1.788``` | ```2.638``` | 
| Max | ```32.235``` | ```16.083``` | 


![Chart of Deno console_log](charts/deno__console_log__10.png)
![Chart of Node.js console_log](charts/node__console_log__10.png)

Deno is ```34.26%``` faster than Node.js
#### Concurrency=25
Total requests: ```25000```



| Reading | Node.js | Deno |
| ------- | ------- | ---- |
| TimeTakenMS | ```31359``` | ```31549``` | 
| ReqPerSec | ```797``` | ```792``` | 
| Mean | ```24``` | ```28``` | 
| Median | ```15``` | ```29``` | 
| Min | ```0.725``` | ```2.864``` | 
| Max | ```3880.012``` | ```46.342``` | 


![Chart of Deno console_log](charts/deno__console_log__25.png)
![Chart of Node.js console_log](charts/node__console_log__25.png)

Deno is ```0.60%``` slower than Node.js
## Next steps

There is a lot more work to be done! If you like to suggest more benchmarks, please add an issue with your suggestions.

Also, please add a star to this repository if it has been valuable. More stars means more readers and this would encourage us to keep the benchmark running.
