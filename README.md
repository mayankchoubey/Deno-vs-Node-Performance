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
Deno: ```1.7.4```

Node.js: ```15.8.0```

### Last Run
Mon Feb 15 23:24:17 PST 2021

### Environment
MacBook Pro 1.4Ghz Quad core i5 with 8G memory

### List of Tests

| Test | Description |
| ------- | ------- |
| [Hello world](#hello-world)| This one is a very simple hello world program. It responds to a GET request with a JSON containing a string Hello World!|  
| [Hello world with frameworks: oak and express](#hello-world-with-frameworks-oak-and-express)| Hello world program using the popular frameworks: Oak/Deno, Express/Node.js|  
| [Echo name over HTTPS](#echo-name-over-https)| A simple echo name program that runs over HTTPS|  
| [Five hundred random integers](#five-hundred-random-integers)| Generate five hundred random integers and return them in a JSON array|  
| [Five hundred random 16 character hex string](#five-hundred-random-16-character-hex-string)| Generate five hundred random 16 character hex strings and return them in a JSON array|  
| [One hundred V1 UUIDs](#one-hundred-v1-uuids)| Generate one hundred V1 UUIDs and return them in a JSON array|  
| [One hundred V4 UUIDs](#one-hundred-v4-uuids)| Generate one hundred V4 UUIDs and return them in a JSON array|  
| [One hundred V5 UUIDs](#one-hundred-v5-uuids)| Generate one hundred V5 UUIDs and return them in a JSON array|  
| [Parse five hundred strings](#parse-five-hundred-strings)| Parse five hundred strings containing integers and return parsed integers in a JSON array|  
| [Calculate mean of 500 numbers](#calculate-mean-of-500-numbers)| Calculate mean of 500 numbers and return it in response|  
| [Calculate median of 500 numbers](#calculate-median-of-500-numbers)| Calculate median of 500 numbers and return it in response|  
| [Write 500 console logs](#write-500-console-logs)| Write 500 lines on the console, and return number of lines in response.|  
| [A simple API proxy](#a-simple-api-proxy)| Receive request, increment, and send it to a faux server. Receive response, increment, and send it back.|  
| [Multipart form-data with fields](#multipart-form-data-with-fields)| Receive multipart/form-data and return parsed fields in JSON.|  
| [A simple message exchange over UDP](#a-simple-message-exchange-over-udp)| Receive a message over UDP, and echo it back.|  
| [A simple message exchange over WebSocket](#a-simple-message-exchange-over-websocket)| Receive a message over WebSocket, and echo it back.|  

## Tests and Results



### Hello world
This one is a very simple hello world program. It responds to a GET request with a JSON containing a string Hello World!
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1154```| ```1000```|![](charts/green.png)| 
|ReqPerSec|```866```| ```1000```|![](charts/green.png)| 
|Min.|```0.24```| ```0.23```|![](charts/green.png)| 
|1st Qu.|```0.33```| ```0.25```|![](charts/green.png)| 
|Median|```0.38```| ```0.27```|![](charts/green.png)| 
|Mean|```0.42```| ```0.3```|![](charts/green.png)| 
|3rd Qu.|```0.45```| ```0.3```|![](charts/green.png)| 
|Max.|```2.67```| ```2.01```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.24```| ```0.23```|![](charts/green.png)| 
|10%|```0.27```| ```0.24```|![](charts/green.png)| 
|20%|```0.31```| ```0.25```|![](charts/green.png)| 
|30%|```0.34```| ```0.25```|![](charts/green.png)| 
|40%|```0.36```| ```0.26```|![](charts/green.png)| 
|50%|```0.38```| ```0.27```|![](charts/green.png)| 
|60%|```0.4```| ```0.27```|![](charts/green.png)| 
|70%|```0.43```| ```0.28```|![](charts/green.png)| 
|80%|```0.48```| ```0.32```|![](charts/green.png)| 
|90%|```0.58```| ```0.36```|![](charts/green.png)| 
|100%|```2.67```| ```2.01```|![](charts/green.png)| 


![Chart of Deno hello_world](charts/deno__hello_world__1.png)
![Chart of Node.js hello_world](charts/node__hello_world__1.png)

Deno is ```13.34%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3738```| ```3987```|![](charts/red.png)| 
|ReqPerSec|```2675```| ```2508```|![](charts/red.png)| 
|Min.|```0.21```| ```0.27```|![](charts/red.png)| 
|1st Qu.|```0.71```| ```0.96```|![](charts/red.png)| 
|Median|```1.08```| ```1.27```|![](charts/red.png)| 
|Mean|```1.31```| ```1.56```|![](charts/red.png)| 
|3rd Qu.|```1.68```| ```1.75```|![](charts/red.png)| 
|Max.|```52.1```| ```100.06```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.21```| ```0.27```|![](charts/red.png)| 
|10%|```0.44```| ```0.61```|![](charts/red.png)| 
|20%|```0.62```| ```0.88```|![](charts/red.png)| 
|30%|```0.8```| ```1.02```|![](charts/red.png)| 
|40%|```0.94```| ```1.13```|![](charts/red.png)| 
|50%|```1.08```| ```1.27```|![](charts/red.png)| 
|60%|```1.28```| ```1.42```|![](charts/red.png)| 
|70%|```1.54```| ```1.61```|![](charts/red.png)| 
|80%|```1.84```| ```1.93```|![](charts/red.png)| 
|90%|```2.28```| ```2.48```|![](charts/red.png)| 
|100%|```52.1```| ```100.06```|![](charts/red.png)| 


![Chart of Deno hello_world](charts/deno__hello_world__10.png)
![Chart of Node.js hello_world](charts/node__hello_world__10.png)

Deno is ```6.25%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```8257```| ```7576```|![](charts/green.png)| 
|ReqPerSec|```3027```| ```3299```|![](charts/green.png)| 
|Min.|```0.27```| ```0.31```|![](charts/red.png)| 
|1st Qu.|```2.78```| ```2.75```|![](charts/green.png)| 
|Median|```3.28```| ```3.14```|![](charts/green.png)| 
|Mean|```3.66```| ```3.39```|![](charts/green.png)| 
|3rd Qu.|```4.01```| ```3.62```|![](charts/green.png)| 
|Max.|```145.84```| ```119.6```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.27```| ```0.31```|![](charts/red.png)| 
|10%|```2.09```| ```2.24```|![](charts/red.png)| 
|20%|```2.63```| ```2.64```|![](charts/red.png)| 
|30%|```2.9```| ```2.85```|![](charts/green.png)| 
|40%|```3.09```| ```3.01```|![](charts/green.png)| 
|50%|```3.28```| ```3.14```|![](charts/green.png)| 
|60%|```3.49```| ```3.29```|![](charts/green.png)| 
|70%|```3.78```| ```3.49```|![](charts/green.png)| 
|80%|```4.33```| ```3.81```|![](charts/green.png)| 
|90%|```5.76```| ```4.47```|![](charts/green.png)| 
|100%|```145.84```| ```119.6```|![](charts/green.png)| 


![Chart of Deno hello_world](charts/deno__hello_world__25.png)
![Chart of Node.js hello_world](charts/node__hello_world__25.png)

Deno is ```8.25%``` faster than Node.js. ![](charts/green.png)

### Hello world with frameworks: oak and express
Hello world program using the popular frameworks: Oak/Deno, Express/Node.js
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_hello_world_oak_exp.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_hello_world_oak_exp.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1188```| ```1008```|![](charts/green.png)| 
|ReqPerSec|```841```| ```992```|![](charts/green.png)| 
|Min.|```0.36```| ```0.26```|![](charts/green.png)| 
|1st Qu.|```0.45```| ```0.29```|![](charts/green.png)| 
|Median|```0.49```| ```0.31```|![](charts/green.png)| 
|Mean|```0.5```| ```0.35```|![](charts/green.png)| 
|3rd Qu.|```0.52```| ```0.36```|![](charts/green.png)| 
|Max.|```2.48```| ```2.37```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.36```| ```0.26```|![](charts/green.png)| 
|10%|```0.41```| ```0.28```|![](charts/green.png)| 
|20%|```0.44```| ```0.28```|![](charts/green.png)| 
|30%|```0.45```| ```0.29```|![](charts/green.png)| 
|40%|```0.47```| ```0.3```|![](charts/green.png)| 
|50%|```0.49```| ```0.31```|![](charts/green.png)| 
|60%|```0.5```| ```0.32```|![](charts/green.png)| 
|70%|```0.51```| ```0.35```|![](charts/green.png)| 
|80%|```0.52```| ```0.37```|![](charts/green.png)| 
|90%|```0.58```| ```0.43```|![](charts/green.png)| 
|100%|```2.48```| ```2.37```|![](charts/green.png)| 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__1.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__1.png)

Deno is ```15.15%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3957```| ```3237```|![](charts/green.png)| 
|ReqPerSec|```2527```| ```3089```|![](charts/green.png)| 
|Min.|```0.29```| ```0.28```|![](charts/green.png)| 
|1st Qu.|```1.19```| ```0.96```|![](charts/green.png)| 
|Median|```1.61```| ```1.21```|![](charts/green.png)| 
|Mean|```1.91```| ```1.33```|![](charts/green.png)| 
|3rd Qu.|```2.43```| ```1.48```|![](charts/green.png)| 
|Max.|```54.55```| ```40```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.29```| ```0.28```|![](charts/green.png)| 
|10%|```0.9```| ```0.62```|![](charts/green.png)| 
|20%|```1.14```| ```0.88```|![](charts/green.png)| 
|30%|```1.27```| ```1.02```|![](charts/green.png)| 
|40%|```1.41```| ```1.13```|![](charts/green.png)| 
|50%|```1.61```| ```1.21```|![](charts/green.png)| 
|60%|```1.82```| ```1.29```|![](charts/green.png)| 
|70%|```2.18```| ```1.41```|![](charts/green.png)| 
|80%|```2.6```| ```1.58```|![](charts/green.png)| 
|90%|```3.2```| ```1.9```|![](charts/green.png)| 
|100%|```54.55```| ```40```|![](charts/green.png)| 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__10.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__10.png)

Deno is ```18.20%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```9500```| ```7878```|![](charts/green.png)| 
|ReqPerSec|```2631```| ```3173```|![](charts/green.png)| 
|Min.|```0.31```| ```0.33```|![](charts/red.png)| 
|1st Qu.|```4.25```| ```3.06```|![](charts/green.png)| 
|Median|```4.77```| ```3.45```|![](charts/green.png)| 
|Mean|```5.18```| ```3.62```|![](charts/green.png)| 
|3rd Qu.|```5.43```| ```3.94```|![](charts/green.png)| 
|Max.|```155.35```| ```164.86```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.31```| ```0.33```|![](charts/red.png)| 
|10%|```2.98```| ```2.47```|![](charts/green.png)| 
|20%|```4.05```| ```2.93```|![](charts/green.png)| 
|30%|```4.38```| ```3.16```|![](charts/green.png)| 
|40%|```4.58```| ```3.31```|![](charts/green.png)| 
|50%|```4.77```| ```3.45```|![](charts/green.png)| 
|60%|```4.98```| ```3.63```|![](charts/green.png)| 
|70%|```5.23```| ```3.83```|![](charts/green.png)| 
|80%|```5.75```| ```4.09```|![](charts/green.png)| 
|90%|```7.7```| ```4.61```|![](charts/green.png)| 
|100%|```155.35```| ```164.86```|![](charts/red.png)| 


![Chart of Deno hello_world_oak_exp](charts/deno__hello_world_oak_exp__25.png)
![Chart of Node.js hello_world_oak_exp](charts/node__hello_world_oak_exp__25.png)

Deno is ```17.07%``` faster than Node.js. ![](charts/green.png)

### Echo name over HTTPS
A simple echo name program that runs over HTTPS
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_https_hello_name.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_https_hello_name.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1069```| ```1037```|![](charts/green.png)| 
|ReqPerSec|```935```| ```964```|![](charts/green.png)| 
|Min.|```0.29```| ```0.3```|![](charts/red.png)| 
|1st Qu.|```0.32```| ```0.32```|![](charts/green.png)| 
|Median|```0.34```| ```0.33```|![](charts/green.png)| 
|Mean|```0.38```| ```0.38```|![](charts/green.png)| 
|3rd Qu.|```0.39```| ```0.39```|![](charts/green.png)| 
|Max.|```2.6```| ```2.25```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.29```| ```0.3```|![](charts/red.png)| 
|10%|```0.3```| ```0.31```|![](charts/red.png)| 
|20%|```0.31```| ```0.31```|![](charts/green.png)| 
|30%|```0.33```| ```0.32```|![](charts/green.png)| 
|40%|```0.34```| ```0.32```|![](charts/green.png)| 
|50%|```0.34```| ```0.33```|![](charts/green.png)| 
|60%|```0.35```| ```0.35```|![](charts/green.png)| 
|70%|```0.38```| ```0.38```|![](charts/green.png)| 
|80%|```0.41```| ```0.41```|![](charts/green.png)| 
|90%|```0.47```| ```0.48```|![](charts/red.png)| 
|100%|```2.6```| ```2.25```|![](charts/green.png)| 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__1.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__1.png)

Deno is ```2.99%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3496```| ```3418```|![](charts/green.png)| 
|ReqPerSec|```2860```| ```2925```|![](charts/green.png)| 
|Min.|```0.27```| ```0.27```|![](charts/green.png)| 
|1st Qu.|```0.84```| ```1.1```|![](charts/red.png)| 
|Median|```1.21```| ```1.37```|![](charts/red.png)| 
|Mean|```1.42```| ```1.48```|![](charts/red.png)| 
|3rd Qu.|```1.78```| ```1.7```|![](charts/green.png)| 
|Max.|```59.41```| ```24.74```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.27```| ```0.27```|![](charts/green.png)| 
|10%|```0.58```| ```0.79```|![](charts/red.png)| 
|20%|```0.76```| ```1.03```|![](charts/red.png)| 
|30%|```0.93```| ```1.16```|![](charts/red.png)| 
|40%|```1.08```| ```1.27```|![](charts/red.png)| 
|50%|```1.21```| ```1.37```|![](charts/red.png)| 
|60%|```1.38```| ```1.48```|![](charts/red.png)| 
|70%|```1.62```| ```1.61```|![](charts/green.png)| 
|80%|```1.97```| ```1.81```|![](charts/green.png)| 
|90%|```2.4```| ```2.14```|![](charts/green.png)| 
|100%|```59.41```| ```24.74```|![](charts/green.png)| 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__10.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__10.png)

Deno is ```2.23%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```8683```| ```8156```|![](charts/green.png)| 
|ReqPerSec|```2879```| ```3065```|![](charts/green.png)| 
|Min.|```0.41```| ```0.37```|![](charts/green.png)| 
|1st Qu.|```3.37```| ```3.41```|![](charts/red.png)| 
|Median|```3.89```| ```3.88```|![](charts/green.png)| 
|Mean|```4.18```| ```4.04```|![](charts/green.png)| 
|3rd Qu.|```4.5```| ```4.45```|![](charts/green.png)| 
|Max.|```197.27```| ```136.37```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.41```| ```0.37```|![](charts/green.png)| 
|10%|```2.23```| ```2.89```|![](charts/red.png)| 
|20%|```3.12```| ```3.28```|![](charts/red.png)| 
|30%|```3.51```| ```3.5```|![](charts/green.png)| 
|40%|```3.71```| ```3.69```|![](charts/green.png)| 
|50%|```3.89```| ```3.88```|![](charts/green.png)| 
|60%|```4.07```| ```4.07```|![](charts/green.png)| 
|70%|```4.32```| ```4.3```|![](charts/green.png)| 
|80%|```4.75```| ```4.63```|![](charts/green.png)| 
|90%|```6.06```| ```5.21```|![](charts/green.png)| 
|100%|```197.27```| ```136.37```|![](charts/green.png)| 


![Chart of Deno hello_name_https](charts/deno__hello_name_https__25.png)
![Chart of Node.js hello_name_https](charts/node__hello_name_https__25.png)

Deno is ```6.07%``` faster than Node.js. ![](charts/green.png)

### Five hundred random integers
Generate five hundred random integers and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_int.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1072```| ```1027```|![](charts/green.png)| 
|ReqPerSec|```932```| ```973```|![](charts/green.png)| 
|Min.|```0.29```| ```0.29```|![](charts/green.png)| 
|1st Qu.|```0.32```| ```0.31```|![](charts/green.png)| 
|Median|```0.35```| ```0.33```|![](charts/green.png)| 
|Mean|```0.39```| ```0.38```|![](charts/green.png)| 
|3rd Qu.|```0.43```| ```0.39```|![](charts/green.png)| 
|Max.|```1.74```| ```1.99```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.29```| ```0.29```|![](charts/green.png)| 
|10%|```0.3```| ```0.31```|![](charts/red.png)| 
|20%|```0.31```| ```0.31```|![](charts/green.png)| 
|30%|```0.32```| ```0.32```|![](charts/green.png)| 
|40%|```0.34```| ```0.32```|![](charts/green.png)| 
|50%|```0.35```| ```0.33```|![](charts/green.png)| 
|60%|```0.37```| ```0.35```|![](charts/green.png)| 
|70%|```0.41```| ```0.37```|![](charts/green.png)| 
|80%|```0.45```| ```0.42```|![](charts/green.png)| 
|90%|```0.5```| ```0.49```|![](charts/green.png)| 
|100%|```1.74```| ```1.99```|![](charts/red.png)| 


![Chart of Deno random_int](charts/deno__random_int__1.png)
![Chart of Node.js random_int](charts/node__random_int__1.png)

Deno is ```4.20%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3519```| ```3647```|![](charts/red.png)| 
|ReqPerSec|```2841```| ```2741```|![](charts/red.png)| 
|Min.|```0.26```| ```0.28```|![](charts/red.png)| 
|1st Qu.|```0.85```| ```1.25```|![](charts/red.png)| 
|Median|```1.2```| ```1.46```|![](charts/red.png)| 
|Mean|```1.42```| ```1.58```|![](charts/red.png)| 
|3rd Qu.|```1.89```| ```1.78```|![](charts/green.png)| 
|Max.|```16.51```| ```59.24```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.26```| ```0.28```|![](charts/red.png)| 
|10%|```0.57```| ```0.93```|![](charts/red.png)| 
|20%|```0.76```| ```1.17```|![](charts/red.png)| 
|30%|```0.93```| ```1.3```|![](charts/red.png)| 
|40%|```1.06```| ```1.38```|![](charts/red.png)| 
|50%|```1.2```| ```1.46```|![](charts/red.png)| 
|60%|```1.41```| ```1.57```|![](charts/red.png)| 
|70%|```1.72```| ```1.71```|![](charts/green.png)| 
|80%|```2.05```| ```1.88```|![](charts/green.png)| 
|90%|```2.4```| ```2.18```|![](charts/green.png)| 
|100%|```16.51```| ```59.24```|![](charts/red.png)| 


![Chart of Deno random_int](charts/deno__random_int__10.png)
![Chart of Node.js random_int](charts/node__random_int__10.png)

Deno is ```3.51%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```8486```| ```8264```|![](charts/green.png)| 
|ReqPerSec|```2946```| ```3025```|![](charts/green.png)| 
|Min.|```0.32```| ```0.43```|![](charts/red.png)| 
|1st Qu.|```3.24```| ```3.72```|![](charts/red.png)| 
|Median|```3.75```| ```4.14```|![](charts/red.png)| 
|Mean|```4.08```| ```4.24```|![](charts/red.png)| 
|3rd Qu.|```4.39```| ```4.62```|![](charts/red.png)| 
|Max.|```137.62```| ```72.88```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.32```| ```0.43```|![](charts/red.png)| 
|10%|```2.21```| ```3.33```|![](charts/red.png)| 
|20%|```3.02```| ```3.61```|![](charts/red.png)| 
|30%|```3.37```| ```3.81```|![](charts/red.png)| 
|40%|```3.57```| ```3.98```|![](charts/red.png)| 
|50%|```3.75```| ```4.14```|![](charts/red.png)| 
|60%|```3.94```| ```4.31```|![](charts/red.png)| 
|70%|```4.2```| ```4.5```|![](charts/red.png)| 
|80%|```4.66```| ```4.77```|![](charts/red.png)| 
|90%|```6.52```| ```5.25```|![](charts/green.png)| 
|100%|```137.62```| ```72.88```|![](charts/green.png)| 


![Chart of Deno random_int](charts/deno__random_int__25.png)
![Chart of Node.js random_int](charts/node__random_int__25.png)

Deno is ```2.62%``` faster than Node.js. ![](charts/green.png)

### Five hundred random 16 character hex string
Generate five hundred random 16 character hex strings and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_random_hex.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_random_hex.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1710```| ```1668```|![](charts/green.png)| 
|ReqPerSec|```584```| ```599```|![](charts/green.png)| 
|Min.|```0.81```| ```0.79```|![](charts/green.png)| 
|1st Qu.|```0.86```| ```0.88```|![](charts/red.png)| 
|Median|```0.89```| ```0.9```|![](charts/red.png)| 
|Mean|```0.94```| ```0.95```|![](charts/red.png)| 
|3rd Qu.|```0.99```| ```1.01```|![](charts/red.png)| 
|Max.|```2.4```| ```2.58```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.81```| ```0.79```|![](charts/green.png)| 
|10%|```0.84```| ```0.85```|![](charts/red.png)| 
|20%|```0.85```| ```0.88```|![](charts/red.png)| 
|30%|```0.86```| ```0.89```|![](charts/red.png)| 
|40%|```0.88```| ```0.89```|![](charts/red.png)| 
|50%|```0.89```| ```0.9```|![](charts/red.png)| 
|60%|```0.9```| ```0.92```|![](charts/red.png)| 
|70%|```0.95```| ```0.97```|![](charts/red.png)| 
|80%|```1.04```| ```1.05```|![](charts/red.png)| 
|90%|```1.1```| ```1.08```|![](charts/green.png)| 
|100%|```2.4```| ```2.58```|![](charts/red.png)| 


![Chart of Deno random_hex](charts/deno__random_hex__1.png)
![Chart of Node.js random_hex](charts/node__random_hex__1.png)

Deno is ```2.46%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```7195```| ```7979```|![](charts/red.png)| 
|ReqPerSec|```1389```| ```1253```|![](charts/red.png)| 
|Min.|```0.73```| ```0.84```|![](charts/red.png)| 
|1st Qu.|```3.73```| ```3.69```|![](charts/green.png)| 
|Median|```4.12```| ```4.37```|![](charts/red.png)| 
|Mean|```4.5```| ```4.33```|![](charts/green.png)| 
|3rd Qu.|```4.9```| ```5.04```|![](charts/red.png)| 
|Max.|```48.33```| ```26.47```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.73```| ```0.84```|![](charts/red.png)| 
|10%|```1.84```| ```3.14```|![](charts/red.png)| 
|20%|```3.66```| ```3.53```|![](charts/green.png)| 
|30%|```3.8```| ```3.85```|![](charts/red.png)| 
|40%|```3.98```| ```4.08```|![](charts/red.png)| 
|50%|```4.12```| ```4.37```|![](charts/red.png)| 
|60%|```4.37```| ```4.62```|![](charts/red.png)| 
|70%|```4.64```| ```4.9```|![](charts/red.png)| 
|80%|```5.27```| ```5.19```|![](charts/green.png)| 
|90%|```8.02```| ```5.51```|![](charts/green.png)| 
|100%|```48.33```| ```26.47```|![](charts/green.png)| 


![Chart of Deno random_hex](charts/deno__random_hex__10.png)
![Chart of Node.js random_hex](charts/node__random_hex__10.png)

Deno is ```9.83%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```17346```| ```21035```|![](charts/red.png)| 
|ReqPerSec|```1441```| ```1188```|![](charts/red.png)| 
|Min.|```0.76```| ```1.38```|![](charts/red.png)| 
|1st Qu.|```11.48```| ```10.94```|![](charts/green.png)| 
|Median|```11.81```| ```11.71```|![](charts/green.png)| 
|Mean|```12.08```| ```11.69```|![](charts/green.png)| 
|3rd Qu.|```12.23```| ```12.76```|![](charts/red.png)| 
|Max.|```197.57```| ```17.42```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.76```| ```1.38```|![](charts/red.png)| 
|10%|```11.07```| ```9.77```|![](charts/green.png)| 
|20%|```11.4```| ```10.67```|![](charts/green.png)| 
|30%|```11.55```| ```11.14```|![](charts/green.png)| 
|40%|```11.67```| ```11.45```|![](charts/green.png)| 
|50%|```11.81```| ```11.71```|![](charts/green.png)| 
|60%|```11.98```| ```12.07```|![](charts/red.png)| 
|70%|```12.14```| ```12.54```|![](charts/red.png)| 
|80%|```12.38```| ```12.94```|![](charts/red.png)| 
|90%|```13.1```| ```13.39```|![](charts/red.png)| 
|100%|```197.57```| ```17.42```|![](charts/green.png)| 


![Chart of Deno random_hex](charts/deno__random_hex__25.png)
![Chart of Node.js random_hex](charts/node__random_hex__25.png)

Deno is ```17.54%``` slower than Node.js. ![](charts/red.png)

### One hundred V1 UUIDs
Generate one hundred V1 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v1.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v1.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1199```| ```1294```|![](charts/red.png)| 
|ReqPerSec|```834```| ```772```|![](charts/red.png)| 
|Min.|```0.34```| ```0.46```|![](charts/red.png)| 
|1st Qu.|```0.43```| ```0.55```|![](charts/red.png)| 
|Median|```0.49```| ```0.58```|![](charts/red.png)| 
|Mean|```0.5```| ```0.6```|![](charts/red.png)| 
|3rd Qu.|```0.52```| ```0.63```|![](charts/red.png)| 
|Max.|```1.88```| ```2.16```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.34```| ```0.46```|![](charts/red.png)| 
|10%|```0.36```| ```0.48```|![](charts/red.png)| 
|20%|```0.39```| ```0.54```|![](charts/red.png)| 
|30%|```0.46```| ```0.55```|![](charts/red.png)| 
|40%|```0.48```| ```0.57```|![](charts/red.png)| 
|50%|```0.49```| ```0.58```|![](charts/red.png)| 
|60%|```0.5```| ```0.59```|![](charts/red.png)| 
|70%|```0.51```| ```0.61```|![](charts/red.png)| 
|80%|```0.53```| ```0.64```|![](charts/red.png)| 
|90%|```0.6```| ```0.72```|![](charts/red.png)| 
|100%|```1.88```| ```2.16```|![](charts/red.png)| 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__1.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__1.png)

Deno is ```7.34%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3826```| ```4401```|![](charts/red.png)| 
|ReqPerSec|```2613```| ```2272```|![](charts/red.png)| 
|Min.|```0.32```| ```0.5```|![](charts/red.png)| 
|1st Qu.|```1.09```| ```2.06```|![](charts/red.png)| 
|Median|```1.43```| ```2.35```|![](charts/red.png)| 
|Mean|```1.71```| ```2.49```|![](charts/red.png)| 
|3rd Qu.|```2.31```| ```2.89```|![](charts/red.png)| 
|Max.|```26.81```| ```36.54```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.32```| ```0.5```|![](charts/red.png)| 
|10%|```0.77```| ```1.81```|![](charts/red.png)| 
|20%|```1.01```| ```2.02```|![](charts/red.png)| 
|30%|```1.16```| ```2.11```|![](charts/red.png)| 
|40%|```1.28```| ```2.23```|![](charts/red.png)| 
|50%|```1.43```| ```2.35```|![](charts/red.png)| 
|60%|```1.64```| ```2.53```|![](charts/red.png)| 
|70%|```2.11```| ```2.74```|![](charts/red.png)| 
|80%|```2.48```| ```3.05```|![](charts/red.png)| 
|90%|```2.86```| ```3.3```|![](charts/red.png)| 
|100%|```26.81```| ```36.54```|![](charts/red.png)| 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__10.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__10.png)

Deno is ```13.07%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```9467```| ```11965```|![](charts/red.png)| 
|ReqPerSec|```2640```| ```2089```|![](charts/red.png)| 
|Min.|```0.42```| ```0.68```|![](charts/red.png)| 
|1st Qu.|```3.94```| ```7.03```|![](charts/red.png)| 
|Median|```4.55```| ```7.97```|![](charts/red.png)| 
|Mean|```4.82```| ```7.7```|![](charts/red.png)| 
|3rd Qu.|```5.21```| ```8.47```|![](charts/red.png)| 
|Max.|```114.44```| ```15.89```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.42```| ```0.68```|![](charts/red.png)| 
|10%|```2.32```| ```5.55```|![](charts/red.png)| 
|20%|```3.56```| ```6.38```|![](charts/red.png)| 
|30%|```4.12```| ```7.51```|![](charts/red.png)| 
|40%|```4.36```| ```7.81```|![](charts/red.png)| 
|50%|```4.55```| ```7.97```|![](charts/red.png)| 
|60%|```4.75```| ```8.15```|![](charts/red.png)| 
|70%|```5.01```| ```8.35```|![](charts/red.png)| 
|80%|```5.48```| ```8.63```|![](charts/red.png)| 
|90%|```7.61```| ```9.05```|![](charts/red.png)| 
|100%|```114.44```| ```15.89```|![](charts/green.png)| 


![Chart of Deno uuid_v1](charts/deno__uuid_v1__25.png)
![Chart of Node.js uuid_v1](charts/node__uuid_v1__25.png)

Deno is ```20.88%``` slower than Node.js. ![](charts/red.png)

### One hundred V4 UUIDs
Generate one hundred V4 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v4.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v4.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1455```| ```2224```|![](charts/red.png)| 
|ReqPerSec|```687```| ```449```|![](charts/red.png)| 
|Min.|```0.59```| ```1.19```|![](charts/red.png)| 
|1st Qu.|```0.66```| ```1.26```|![](charts/red.png)| 
|Median|```0.69```| ```1.29```|![](charts/red.png)| 
|Mean|```0.74```| ```1.49```|![](charts/red.png)| 
|3rd Qu.|```0.72```| ```1.45```|![](charts/red.png)| 
|Max.|```2.42```| ```3.4```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.59```| ```1.19```|![](charts/red.png)| 
|10%|```0.65```| ```1.25```|![](charts/red.png)| 
|20%|```0.66```| ```1.26```|![](charts/red.png)| 
|30%|```0.67```| ```1.27```|![](charts/red.png)| 
|40%|```0.68```| ```1.28```|![](charts/red.png)| 
|50%|```0.69```| ```1.29```|![](charts/red.png)| 
|60%|```0.7```| ```1.31```|![](charts/red.png)| 
|70%|```0.71```| ```1.35```|![](charts/red.png)| 
|80%|```0.74```| ```1.6```|![](charts/red.png)| 
|90%|```0.84```| ```2.22```|![](charts/red.png)| 
|100%|```2.42```| ```3.4```|![](charts/red.png)| 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__1.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__1.png)

Deno is ```34.58%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```5599```| ```14249```|![](charts/red.png)| 
|ReqPerSec|```1786```| ```701```|![](charts/red.png)| 
|Min.|```0.55```| ```1.31```|![](charts/red.png)| 
|1st Qu.|```2.24```| ```9.29```|![](charts/red.png)| 
|Median|```2.67```| ```9.84```|![](charts/red.png)| 
|Mean|```3.15```| ```11.84```|![](charts/red.png)| 
|3rd Qu.|```4.03```| ```14.18```|![](charts/red.png)| 
|Max.|```17.2```| ```22.72```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.55```| ```1.31```|![](charts/red.png)| 
|10%|```1.5```| ```9.11```|![](charts/red.png)| 
|20%|```2.2```| ```9.24```|![](charts/red.png)| 
|30%|```2.27```| ```9.36```|![](charts/red.png)| 
|40%|```2.34```| ```9.51```|![](charts/red.png)| 
|50%|```2.67```| ```9.84```|![](charts/red.png)| 
|60%|```3.15```| ```11.46```|![](charts/red.png)| 
|70%|```3.58```| ```13.24```|![](charts/red.png)| 
|80%|```4.35```| ```14.9```|![](charts/red.png)| 
|90%|```5.63```| ```17.47```|![](charts/red.png)| 
|100%|```17.2```| ```22.72```|![](charts/red.png)| 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__10.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__10.png)

Deno is ```60.71%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```13521```| ```37820```|![](charts/red.png)| 
|ReqPerSec|```1848```| ```661```|![](charts/red.png)| 
|Min.|```0.54```| ```2.47```|![](charts/red.png)| 
|1st Qu.|```6.96```| ```26.02```|![](charts/red.png)| 
|Median|```7.9```| ```28.69```|![](charts/red.png)| 
|Mean|```8.37```| ```32.31```|![](charts/red.png)| 
|3rd Qu.|```9.15```| ```37.87```|![](charts/red.png)| 
|Max.|```156.61```| ```189.99```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.54```| ```2.47```|![](charts/red.png)| 
|10%|```6.56```| ```24.6```|![](charts/red.png)| 
|20%|```6.87```| ```25.45```|![](charts/red.png)| 
|30%|```7.04```| ```26.62```|![](charts/red.png)| 
|40%|```7.33```| ```27.3```|![](charts/red.png)| 
|50%|```7.9```| ```28.69```|![](charts/red.png)| 
|60%|```8.48```| ```33.16```|![](charts/red.png)| 
|70%|```8.84```| ```36.16```|![](charts/red.png)| 
|80%|```9.76```| ```41.25```|![](charts/red.png)| 
|90%|```11.29```| ```44.76```|![](charts/red.png)| 
|100%|```156.61```| ```189.99```|![](charts/red.png)| 


![Chart of Deno uuid_v4](charts/deno__uuid_v4__25.png)
![Chart of Node.js uuid_v4](charts/node__uuid_v4__25.png)

Deno is ```64.25%``` slower than Node.js. ![](charts/red.png)

### One hundred V5 UUIDs
Generate one hundred V5 UUIDs and return them in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_uuid_v5.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_uuid_v5.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1748```| ```2109```|![](charts/red.png)| 
|ReqPerSec|```572```| ```474```|![](charts/red.png)| 
|Min.|```0.79```| ```1.2```|![](charts/red.png)| 
|1st Qu.|```0.83```| ```1.26```|![](charts/red.png)| 
|Median|```0.85```| ```1.29```|![](charts/red.png)| 
|Mean|```1```| ```1.36```|![](charts/red.png)| 
|3rd Qu.|```0.9```| ```1.46```|![](charts/red.png)| 
|Max.|```2.78```| ```3.21```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.79```| ```1.2```|![](charts/red.png)| 
|10%|```0.81```| ```1.25```|![](charts/red.png)| 
|20%|```0.82```| ```1.26```|![](charts/red.png)| 
|30%|```0.83```| ```1.26```|![](charts/red.png)| 
|40%|```0.84```| ```1.27```|![](charts/red.png)| 
|50%|```0.85```| ```1.29```|![](charts/red.png)| 
|60%|```0.86```| ```1.31```|![](charts/red.png)| 
|70%|```0.89```| ```1.44```|![](charts/red.png)| 
|80%|```0.94```| ```1.48```|![](charts/red.png)| 
|90%|```1.62```| ```1.52```|![](charts/green.png)| 
|100%|```2.78```| ```3.21```|![](charts/red.png)| 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__1.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__1.png)

Deno is ```17.12%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```8278```| ```11476```|![](charts/red.png)| 
|ReqPerSec|```1208```| ```871```|![](charts/red.png)| 
|Min.|```0.72```| ```1.31```|![](charts/red.png)| 
|1st Qu.|```3.65```| ```8.85```|![](charts/red.png)| 
|Median|```4.93```| ```9.19```|![](charts/red.png)| 
|Mean|```5.45```| ```9.19```|![](charts/red.png)| 
|3rd Qu.|```6.92```| ```9.53```|![](charts/red.png)| 
|Max.|```41.26```| ```12.98```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.72```| ```1.31```|![](charts/red.png)| 
|10%|```1.95```| ```8.71```|![](charts/red.png)| 
|20%|```3.57```| ```8.81```|![](charts/red.png)| 
|30%|```3.74```| ```8.9```|![](charts/red.png)| 
|40%|```4.11```| ```9.01```|![](charts/red.png)| 
|50%|```4.93```| ```9.19```|![](charts/red.png)| 
|60%|```6.08```| ```9.32```|![](charts/red.png)| 
|70%|```6.62```| ```9.45```|![](charts/red.png)| 
|80%|```7.24```| ```9.62```|![](charts/red.png)| 
|90%|```9.91```| ```9.9```|![](charts/green.png)| 
|100%|```41.26```| ```12.98```|![](charts/green.png)| 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__10.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__10.png)

Deno is ```27.87%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```19957```| ```29409```|![](charts/red.png)| 
|ReqPerSec|```1252```| ```850```|![](charts/red.png)| 
|Min.|```0.74```| ```1.71```|![](charts/red.png)| 
|1st Qu.|```11.97```| ```23.18```|![](charts/red.png)| 
|Median|```15.25```| ```24.35```|![](charts/red.png)| 
|Mean|```14.65```| ```24.28```|![](charts/red.png)| 
|3rd Qu.|```16.72```| ```25.46```|![](charts/red.png)| 
|Max.|```254.33```| ```37.01```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.74```| ```1.71```|![](charts/red.png)| 
|10%|```11.07```| ```22.24```|![](charts/red.png)| 
|20%|```11.66```| ```22.95```|![](charts/red.png)| 
|30%|```12.17```| ```23.43```|![](charts/red.png)| 
|40%|```14.37```| ```23.92```|![](charts/red.png)| 
|50%|```15.25```| ```24.35```|![](charts/red.png)| 
|60%|```15.8```| ```24.79```|![](charts/red.png)| 
|70%|```16.39```| ```25.21```|![](charts/red.png)| 
|80%|```17.09```| ```25.69```|![](charts/red.png)| 
|90%|```18.16```| ```26.25```|![](charts/red.png)| 
|100%|```254.33```| ```37.01```|![](charts/green.png)| 


![Chart of Deno uuid_v5](charts/deno__uuid_v5__25.png)
![Chart of Node.js uuid_v5](charts/node__uuid_v5__25.png)

Deno is ```32.14%``` slower than Node.js. ![](charts/red.png)

### Parse five hundred strings
Parse five hundred strings containing integers and return parsed integers in a JSON array
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_parse_int.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_parse_int.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1137```| ```1071```|![](charts/green.png)| 
|ReqPerSec|```879```| ```933```|![](charts/green.png)| 
|Min.|```0.32```| ```0.33```|![](charts/red.png)| 
|1st Qu.|```0.36```| ```0.35```|![](charts/green.png)| 
|Median|```0.45```| ```0.37```|![](charts/green.png)| 
|Mean|```0.45```| ```0.42```|![](charts/green.png)| 
|3rd Qu.|```0.48```| ```0.44```|![](charts/green.png)| 
|Max.|```1.83```| ```2.23```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.32```| ```0.33```|![](charts/red.png)| 
|10%|```0.33```| ```0.34```|![](charts/red.png)| 
|20%|```0.34```| ```0.35```|![](charts/red.png)| 
|30%|```0.38```| ```0.35```|![](charts/green.png)| 
|40%|```0.43```| ```0.36```|![](charts/green.png)| 
|50%|```0.45```| ```0.37```|![](charts/green.png)| 
|60%|```0.47```| ```0.39```|![](charts/green.png)| 
|70%|```0.48```| ```0.42```|![](charts/green.png)| 
|80%|```0.49```| ```0.47```|![](charts/green.png)| 
|90%|```0.52```| ```0.52```|![](charts/green.png)| 
|100%|```1.83```| ```2.23```|![](charts/red.png)| 


![Chart of Deno parse_int](charts/deno__parse_int__1.png)
![Chart of Node.js parse_int](charts/node__parse_int__1.png)

Deno is ```5.80%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3639```| ```3710```|![](charts/red.png)| 
|ReqPerSec|```2748```| ```2695```|![](charts/red.png)| 
|Min.|```0.3```| ```0.3```|![](charts/green.png)| 
|1st Qu.|```0.89```| ```1.49```|![](charts/red.png)| 
|Median|```1.22```| ```1.74```|![](charts/red.png)| 
|Mean|```1.49```| ```1.8```|![](charts/red.png)| 
|3rd Qu.|```1.98```| ```2.06```|![](charts/red.png)| 
|Max.|```16.72```| ```29.22```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.3```| ```0.3```|![](charts/green.png)| 
|10%|```0.6```| ```1.07```|![](charts/red.png)| 
|20%|```0.8```| ```1.4```|![](charts/red.png)| 
|30%|```0.96```| ```1.54```|![](charts/red.png)| 
|40%|```1.09```| ```1.63```|![](charts/red.png)| 
|50%|```1.22```| ```1.74```|![](charts/red.png)| 
|60%|```1.39```| ```1.88```|![](charts/red.png)| 
|70%|```1.72```| ```1.98```|![](charts/red.png)| 
|80%|```2.18```| ```2.15```|![](charts/green.png)| 
|90%|```2.61```| ```2.42```|![](charts/green.png)| 
|100%|```16.72```| ```29.22```|![](charts/red.png)| 


![Chart of Deno parse_int](charts/deno__parse_int__10.png)
![Chart of Node.js parse_int](charts/node__parse_int__10.png)

Deno is ```1.91%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```9035```| ```9067```|![](charts/red.png)| 
|ReqPerSec|```2767```| ```2757```|![](charts/red.png)| 
|Min.|```0.34```| ```0.39```|![](charts/red.png)| 
|1st Qu.|```3.53```| ```4.31```|![](charts/red.png)| 
|Median|```4.1```| ```4.86```|![](charts/red.png)| 
|Mean|```4.48```| ```4.86```|![](charts/red.png)| 
|3rd Qu.|```4.78```| ```5.33```|![](charts/red.png)| 
|Max.|```204.77```| ```141.5```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.34```| ```0.39```|![](charts/red.png)| 
|10%|```2.19```| ```3.52```|![](charts/red.png)| 
|20%|```3.23```| ```4.18```|![](charts/red.png)| 
|30%|```3.69```| ```4.43```|![](charts/red.png)| 
|40%|```3.9```| ```4.65```|![](charts/red.png)| 
|50%|```4.1```| ```4.86```|![](charts/red.png)| 
|60%|```4.32```| ```5.07```|![](charts/red.png)| 
|70%|```4.6```| ```5.23```|![](charts/red.png)| 
|80%|```5.11```| ```5.47```|![](charts/red.png)| 
|90%|```7.46```| ```5.86```|![](charts/green.png)| 
|100%|```204.77```| ```141.5```|![](charts/green.png)| 


![Chart of Deno parse_int](charts/deno__parse_int__25.png)
![Chart of Node.js parse_int](charts/node__parse_int__25.png)

Deno is ```0.35%``` slower than Node.js. ![](charts/red.png)

### Calculate mean of 500 numbers
Calculate mean of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_mean.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_mean.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1129```| ```1038```|![](charts/green.png)| 
|ReqPerSec|```885```| ```963```|![](charts/green.png)| 
|Min.|```0.29```| ```0.3```|![](charts/red.png)| 
|1st Qu.|```0.34```| ```0.32```|![](charts/green.png)| 
|Median|```0.44```| ```0.34```|![](charts/green.png)| 
|Mean|```0.43```| ```0.38```|![](charts/green.png)| 
|3rd Qu.|```0.46```| ```0.39```|![](charts/green.png)| 
|Max.|```2.04```| ```2.31```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.29```| ```0.3```|![](charts/red.png)| 
|10%|```0.31```| ```0.31```|![](charts/green.png)| 
|20%|```0.33```| ```0.32```|![](charts/green.png)| 
|30%|```0.36```| ```0.32```|![](charts/green.png)| 
|40%|```0.4```| ```0.33```|![](charts/green.png)| 
|50%|```0.44```| ```0.34```|![](charts/green.png)| 
|60%|```0.45```| ```0.36```|![](charts/green.png)| 
|70%|```0.46```| ```0.38```|![](charts/green.png)| 
|80%|```0.47```| ```0.41```|![](charts/green.png)| 
|90%|```0.51```| ```0.47```|![](charts/green.png)| 
|100%|```2.04```| ```2.31```|![](charts/red.png)| 


![Chart of Deno mean](charts/deno__mean__1.png)
![Chart of Node.js mean](charts/node__mean__1.png)

Deno is ```8.06%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3460```| ```3431```|![](charts/green.png)| 
|ReqPerSec|```2890```| ```2914```|![](charts/green.png)| 
|Min.|```0.3```| ```0.28```|![](charts/green.png)| 
|1st Qu.|```0.85```| ```1.17```|![](charts/red.png)| 
|Median|```1.18```| ```1.42```|![](charts/red.png)| 
|Mean|```1.4```| ```1.53```|![](charts/red.png)| 
|3rd Qu.|```1.82```| ```1.72```|![](charts/green.png)| 
|Max.|```11.79```| ```58.08```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.3```| ```0.28```|![](charts/green.png)| 
|10%|```0.56```| ```0.82```|![](charts/red.png)| 
|20%|```0.76```| ```1.09```|![](charts/red.png)| 
|30%|```0.92```| ```1.24```|![](charts/red.png)| 
|40%|```1.05```| ```1.33```|![](charts/red.png)| 
|50%|```1.18```| ```1.42```|![](charts/red.png)| 
|60%|```1.37```| ```1.51```|![](charts/red.png)| 
|70%|```1.65```| ```1.64```|![](charts/green.png)| 
|80%|```2.01```| ```1.8```|![](charts/green.png)| 
|90%|```2.42```| ```2.12```|![](charts/green.png)| 
|100%|```11.79```| ```58.08```|![](charts/red.png)| 


![Chart of Deno mean](charts/deno__mean__10.png)
![Chart of Node.js mean](charts/node__mean__10.png)

Deno is ```0.84%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```8489```| ```8038```|![](charts/green.png)| 
|ReqPerSec|```2944```| ```3110```|![](charts/green.png)| 
|Min.|```0.36```| ```0.38```|![](charts/red.png)| 
|1st Qu.|```3.24```| ```3.37```|![](charts/red.png)| 
|Median|```3.74```| ```3.77```|![](charts/red.png)| 
|Mean|```4.09```| ```3.94```|![](charts/green.png)| 
|3rd Qu.|```4.39```| ```4.32```|![](charts/green.png)| 
|Max.|```121.95```| ```122.88```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.36```| ```0.38```|![](charts/red.png)| 
|10%|```2.13```| ```2.95```|![](charts/red.png)| 
|20%|```3.03```| ```3.28```|![](charts/red.png)| 
|30%|```3.37```| ```3.46```|![](charts/red.png)| 
|40%|```3.57```| ```3.62```|![](charts/red.png)| 
|50%|```3.74```| ```3.77```|![](charts/red.png)| 
|60%|```3.94```| ```3.95```|![](charts/red.png)| 
|70%|```4.21```| ```4.17```|![](charts/green.png)| 
|80%|```4.64```| ```4.5```|![](charts/green.png)| 
|90%|```6.63```| ```5.07```|![](charts/green.png)| 
|100%|```121.95```| ```122.88```|![](charts/red.png)| 


![Chart of Deno mean](charts/deno__mean__25.png)
![Chart of Node.js mean](charts/node__mean__25.png)

Deno is ```5.31%``` faster than Node.js. ![](charts/green.png)

### Calculate median of 500 numbers
Calculate median of 500 numbers and return it in response
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_median.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_median.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1209```| ```1148```|![](charts/green.png)| 
|ReqPerSec|```827```| ```871```|![](charts/green.png)| 
|Min.|```0.38```| ```0.38```|![](charts/green.png)| 
|1st Qu.|```0.49```| ```0.42```|![](charts/green.png)| 
|Median|```0.52```| ```0.48```|![](charts/green.png)| 
|Mean|```0.52```| ```0.49```|![](charts/green.png)| 
|3rd Qu.|```0.54```| ```0.52```|![](charts/green.png)| 
|Max.|```2.16```| ```2.45```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.38```| ```0.38```|![](charts/green.png)| 
|10%|```0.4```| ```0.4```|![](charts/green.png)| 
|20%|```0.47```| ```0.41```|![](charts/green.png)| 
|30%|```0.5```| ```0.42```|![](charts/green.png)| 
|40%|```0.51```| ```0.46```|![](charts/green.png)| 
|50%|```0.52```| ```0.48```|![](charts/green.png)| 
|60%|```0.53```| ```0.49```|![](charts/green.png)| 
|70%|```0.54```| ```0.5```|![](charts/green.png)| 
|80%|```0.55```| ```0.54```|![](charts/green.png)| 
|90%|```0.58```| ```0.58```|![](charts/green.png)| 
|100%|```2.16```| ```2.45```|![](charts/red.png)| 


![Chart of Deno median](charts/deno__median__1.png)
![Chart of Node.js median](charts/node__median__1.png)

Deno is ```5.05%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```3825```| ```4050```|![](charts/red.png)| 
|ReqPerSec|```2614```| ```2469```|![](charts/red.png)| 
|Min.|```0.35```| ```0.35```|![](charts/green.png)| 
|1st Qu.|```1.11```| ```1.59```|![](charts/red.png)| 
|Median|```1.44```| ```2.1```|![](charts/red.png)| 
|Mean|```1.71```| ```2.09```|![](charts/red.png)| 
|3rd Qu.|```2.15```| ```2.46```|![](charts/red.png)| 
|Max.|```20.48```| ```50.89```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.35```| ```0.35```|![](charts/green.png)| 
|10%|```0.77```| ```1.08```|![](charts/red.png)| 
|20%|```1.05```| ```1.45```|![](charts/red.png)| 
|30%|```1.17```| ```1.72```|![](charts/red.png)| 
|40%|```1.3```| ```1.94```|![](charts/red.png)| 
|50%|```1.44```| ```2.1```|![](charts/red.png)| 
|60%|```1.61```| ```2.32```|![](charts/red.png)| 
|70%|```1.9```| ```2.41```|![](charts/red.png)| 
|80%|```2.46```| ```2.55```|![](charts/red.png)| 
|90%|```2.93```| ```2.8```|![](charts/green.png)| 
|100%|```20.48```| ```50.89```|![](charts/red.png)| 


![Chart of Deno median](charts/deno__median__10.png)
![Chart of Node.js median](charts/node__median__10.png)

Deno is ```5.56%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```9755```| ```10653```|![](charts/red.png)| 
|ReqPerSec|```2562```| ```2346```|![](charts/red.png)| 
|Min.|```0.37```| ```0.49```|![](charts/red.png)| 
|1st Qu.|```4.28```| ```5.99```|![](charts/red.png)| 
|Median|```4.76```| ```6.39```|![](charts/red.png)| 
|Mean|```5.08```| ```6.36```|![](charts/red.png)| 
|3rd Qu.|```5.34```| ```6.8```|![](charts/red.png)| 
|Max.|```171.32```| ```127.39```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.37```| ```0.49```|![](charts/red.png)| 
|10%|```2.9```| ```5.1```|![](charts/red.png)| 
|20%|```4.1```| ```5.83```|![](charts/red.png)| 
|30%|```4.4```| ```6.1```|![](charts/red.png)| 
|40%|```4.6```| ```6.27```|![](charts/red.png)| 
|50%|```4.76```| ```6.39```|![](charts/red.png)| 
|60%|```4.94```| ```6.52```|![](charts/red.png)| 
|70%|```5.18```| ```6.7```|![](charts/red.png)| 
|80%|```5.58```| ```6.94```|![](charts/red.png)| 
|90%|```8.23```| ```7.42```|![](charts/green.png)| 
|100%|```171.32```| ```127.39```|![](charts/green.png)| 


![Chart of Deno median](charts/deno__median__25.png)
![Chart of Node.js median](charts/node__median__25.png)

Deno is ```8.43%``` slower than Node.js. ![](charts/red.png)

### Write 500 console logs
Write 500 lines on the console, and return number of lines in response.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_console_log.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_console_log.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```2886```| ```2236```|![](charts/green.png)| 
|ReqPerSec|```346```| ```447```|![](charts/green.png)| 
|Min.|```1.79```| ```1.34```|![](charts/green.png)| 
|1st Qu.|```1.9```| ```1.4```|![](charts/green.png)| 
|Median|```1.96```| ```1.42```|![](charts/green.png)| 
|Mean|```2.01```| ```1.45```|![](charts/green.png)| 
|3rd Qu.|```2.06```| ```1.49```|![](charts/green.png)| 
|Max.|```9.25```| ```3.43```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```1.79```| ```1.34```|![](charts/green.png)| 
|10%|```1.86```| ```1.38```|![](charts/green.png)| 
|20%|```1.89```| ```1.39```|![](charts/green.png)| 
|30%|```1.91```| ```1.4```|![](charts/green.png)| 
|40%|```1.94```| ```1.41```|![](charts/green.png)| 
|50%|```1.96```| ```1.42```|![](charts/green.png)| 
|60%|```1.99```| ```1.43```|![](charts/green.png)| 
|70%|```2.04```| ```1.46```|![](charts/green.png)| 
|80%|```2.08```| ```1.51```|![](charts/green.png)| 
|90%|```2.18```| ```1.57```|![](charts/green.png)| 
|100%|```9.25```| ```3.43```|![](charts/green.png)| 


![Chart of Deno console_log](charts/deno__console_log__1.png)
![Chart of Node.js console_log](charts/node__console_log__1.png)

Deno is ```22.52%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```15508```| ```13532```|![](charts/green.png)| 
|ReqPerSec|```644```| ```738```|![](charts/green.png)| 
|Min.|```0.74```| ```1.55```|![](charts/red.png)| 
|1st Qu.|```4.82```| ```10.82```|![](charts/red.png)| 
|Median|```13.58```| ```11.02```|![](charts/green.png)| 
|Mean|```11.87```| ```11.03```|![](charts/green.png)| 
|3rd Qu.|```14.06```| ```11.3```|![](charts/green.png)| 
|Max.|```538.78```| ```15```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.74```| ```1.55```|![](charts/red.png)| 
|10%|```3.56```| ```10.58```|![](charts/red.png)| 
|20%|```4.56```| ```10.78```|![](charts/red.png)| 
|30%|```6.06```| ```10.86```|![](charts/red.png)| 
|40%|```13.07```| ```10.93```|![](charts/green.png)| 
|50%|```13.58```| ```11.02```|![](charts/green.png)| 
|60%|```13.79```| ```11.12```|![](charts/green.png)| 
|70%|```13.96```| ```11.24```|![](charts/green.png)| 
|80%|```14.21```| ```11.38```|![](charts/green.png)| 
|90%|```14.82```| ```11.65```|![](charts/green.png)| 
|100%|```538.78```| ```15```|![](charts/green.png)| 


![Chart of Deno console_log](charts/deno__console_log__10.png)
![Chart of Node.js console_log](charts/node__console_log__10.png)

Deno is ```12.74%``` faster than Node.js. ![](charts/green.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```25150```| ```34962```|![](charts/red.png)| 
|ReqPerSec|```994```| ```715```|![](charts/red.png)| 
|Min.|```0.71```| ```2.27```|![](charts/red.png)| 
|1st Qu.|```12.34```| ```28.49```|![](charts/red.png)| 
|Median|```14.52```| ```29.89```|![](charts/red.png)| 
|Mean|```18.48```| ```29.45```|![](charts/red.png)| 
|3rd Qu.|```15.86```| ```30.41```|![](charts/red.png)| 
|Max.|```1402.41```| ```257.9```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.71```| ```2.27```|![](charts/red.png)| 
|10%|```11.88```| ```27.54```|![](charts/red.png)| 
|20%|```12.25```| ```28.16```|![](charts/red.png)| 
|30%|```12.46```| ```28.93```|![](charts/red.png)| 
|40%|```12.9```| ```29.62```|![](charts/red.png)| 
|50%|```14.52```| ```29.89```|![](charts/red.png)| 
|60%|```15.16```| ```30.09```|![](charts/red.png)| 
|70%|```15.58```| ```30.3```|![](charts/red.png)| 
|80%|```16.24```| ```30.54```|![](charts/red.png)| 
|90%|```27.95```| ```30.93```|![](charts/red.png)| 
|100%|```1402.41```| ```257.9```|![](charts/green.png)| 


![Chart of Deno console_log](charts/deno__console_log__25.png)
![Chart of Node.js console_log](charts/node__console_log__25.png)

Deno is ```28.06%``` slower than Node.js. ![](charts/red.png)

### Multipart form-data with fields
Receive multipart/form-data and return parsed fields in JSON.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_multipart_fd.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_multipart_fd.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1349```| ```8521```|![](charts/red.png)| 
|ReqPerSec|```741```| ```117```|![](charts/red.png)| 
|Min.|```0.41```| ```5.35```|![](charts/red.png)| 
|1st Qu.|```0.56```| ```6.2```|![](charts/red.png)| 
|Median|```0.58```| ```6.56```|![](charts/red.png)| 
|Mean|```0.62```| ```7.43```|![](charts/red.png)| 
|3rd Qu.|```0.61```| ```8.54```|![](charts/red.png)| 
|Max.|```2.92```| ```14.77```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.41```| ```5.35```|![](charts/red.png)| 
|10%|```0.53```| ```5.97```|![](charts/red.png)| 
|20%|```0.55```| ```6.15```|![](charts/red.png)| 
|30%|```0.56```| ```6.25```|![](charts/red.png)| 
|40%|```0.57```| ```6.37```|![](charts/red.png)| 
|50%|```0.58```| ```6.56```|![](charts/red.png)| 
|60%|```0.6```| ```7.06```|![](charts/red.png)| 
|70%|```0.61```| ```7.93```|![](charts/red.png)| 
|80%|```0.63```| ```9.28```|![](charts/red.png)| 
|90%|```0.71```| ```10.3```|![](charts/red.png)| 
|100%|```2.92```| ```14.77```|![](charts/red.png)| 


![Chart of Deno form_data_fields](charts/deno__form_data_fields__1.png)
![Chart of Node.js form_data_fields](charts/node__form_data_fields__1.png)

Deno is ```84.17%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```4086```| ```91293```|![](charts/red.png)| 
|ReqPerSec|```2447```| ```109```|![](charts/red.png)| 
|Min.|```0.32```| ```17.08```|![](charts/red.png)| 
|1st Qu.|```1.11```| ```82.94```|![](charts/red.png)| 
|Median|```1.64```| ```86.04```|![](charts/red.png)| 
|Mean|```1.91```| ```85.11```|![](charts/red.png)| 
|3rd Qu.|```2.36```| ```88.09```|![](charts/red.png)| 
|Max.|```37.04```| ```134.13```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.32```| ```17.08```|![](charts/red.png)| 
|10%|```0.73```| ```80.24```|![](charts/red.png)| 
|20%|```1```| ```82.32```|![](charts/red.png)| 
|30%|```1.21```| ```83.55```|![](charts/red.png)| 
|40%|```1.43```| ```84.87```|![](charts/red.png)| 
|50%|```1.64```| ```86.04```|![](charts/red.png)| 
|60%|```1.86```| ```86.93```|![](charts/red.png)| 
|70%|```2.16```| ```87.71```|![](charts/red.png)| 
|80%|```2.64```| ```88.48```|![](charts/red.png)| 
|90%|```3.44```| ```89.57```|![](charts/red.png)| 
|100%|```37.04```| ```134.13```|![](charts/red.png)| 


![Chart of Deno form_data_fields](charts/deno__form_data_fields__10.png)
![Chart of Node.js form_data_fields](charts/node__form_data_fields__10.png)

Deno is ```95.52%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```10388```| ```202123```|![](charts/red.png)| 
|ReqPerSec|```2406```| ```123```|![](charts/red.png)| 
|Min.|```0.42```| ```13.22```|![](charts/red.png)| 
|1st Qu.|```4.18```| ```184.58```|![](charts/red.png)| 
|Median|```4.89```| ```188.6```|![](charts/red.png)| 
|Mean|```5.4```| ```188.31```|![](charts/red.png)| 
|3rd Qu.|```5.96```| ```192.78```|![](charts/red.png)| 
|Max.|```157.41```| ```225.22```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.42```| ```13.22```|![](charts/red.png)| 
|10%|```3.08```| ```179.9```|![](charts/red.png)| 
|20%|```3.99```| ```183.44```|![](charts/red.png)| 
|30%|```4.33```| ```185.45```|![](charts/red.png)| 
|40%|```4.6```| ```187.03```|![](charts/red.png)| 
|50%|```4.89```| ```188.6```|![](charts/red.png)| 
|60%|```5.24```| ```190.09```|![](charts/red.png)| 
|70%|```5.67```| ```191.79```|![](charts/red.png)| 
|80%|```6.37```| ```193.93```|![](charts/red.png)| 
|90%|```8.66```| ```197.71```|![](charts/red.png)| 
|100%|```157.41```| ```225.22```|![](charts/red.png)| 


![Chart of Deno form_data_fields](charts/deno__form_data_fields__25.png)
![Chart of Node.js form_data_fields](charts/node__form_data_fields__25.png)

Deno is ```94.86%``` slower than Node.js. ![](charts/red.png)

### A simple message exchange over UDP
Receive a message over UDP, and echo it back.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_udp_server.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_udp_server.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```666```| ```709```|![](charts/red.png)| 
|ReqPerSec|```1501```| ```1410```|![](charts/red.png)| 
|Min.|```0.19```| ```0.23```|![](charts/red.png)| 
|1st Qu.|```0.2```| ```0.23```|![](charts/red.png)| 
|Median|```0.2```| ```0.24```|![](charts/red.png)| 
|Mean|```0.21```| ```0.25```|![](charts/red.png)| 
|3rd Qu.|```0.21```| ```0.24```|![](charts/red.png)| 
|Max.|```0.92```| ```1.61```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.19```| ```0.23```|![](charts/red.png)| 
|10%|```0.19```| ```0.23```|![](charts/red.png)| 
|20%|```0.19```| ```0.23```|![](charts/red.png)| 
|30%|```0.2```| ```0.23```|![](charts/red.png)| 
|40%|```0.2```| ```0.24```|![](charts/red.png)| 
|50%|```0.2```| ```0.24```|![](charts/red.png)| 
|60%|```0.2```| ```0.24```|![](charts/red.png)| 
|70%|```0.21```| ```0.24```|![](charts/red.png)| 
|80%|```0.21```| ```0.25```|![](charts/red.png)| 
|90%|```0.23```| ```0.26```|![](charts/red.png)| 
|100%|```0.92```| ```1.61```|![](charts/red.png)| 


![Chart of Deno udp_server](charts/deno__udp_server__1.png)
![Chart of Node.js udp_server](charts/node__udp_server__1.png)

Deno is ```6.06%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```2487```| ```2789```|![](charts/red.png)| 
|ReqPerSec|```4020```| ```3585```|![](charts/red.png)| 
|Min.|```0.17```| ```0.25```|![](charts/red.png)| 
|1st Qu.|```0.3```| ```0.84```|![](charts/red.png)| 
|Median|```0.42```| ```1.08```|![](charts/red.png)| 
|Mean|```0.76```| ```1.09```|![](charts/red.png)| 
|3rd Qu.|```0.58```| ```1.22```|![](charts/red.png)| 
|Max.|```125.7```| ```106.29```|![](charts/green.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.17```| ```0.25```|![](charts/red.png)| 
|10%|```0.25```| ```0.51```|![](charts/red.png)| 
|20%|```0.28```| ```0.75```|![](charts/red.png)| 
|30%|```0.32```| ```0.92```|![](charts/red.png)| 
|40%|```0.37```| ```1.02```|![](charts/red.png)| 
|50%|```0.42```| ```1.08```|![](charts/red.png)| 
|60%|```0.47```| ```1.13```|![](charts/red.png)| 
|70%|```0.54```| ```1.19```|![](charts/red.png)| 
|80%|```0.64```| ```1.25```|![](charts/red.png)| 
|90%|```0.9```| ```1.41```|![](charts/red.png)| 
|100%|```125.7```| ```106.29```|![](charts/green.png)| 


![Chart of Deno udp_server](charts/deno__udp_server__10.png)
![Chart of Node.js udp_server](charts/node__udp_server__10.png)

Deno is ```10.83%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```8542```| ```7937```|![](charts/green.png)| 
|ReqPerSec|```2926```| ```3149```|![](charts/green.png)| 
|Min.|```0.22```| ```0.26```|![](charts/red.png)| 
|1st Qu.|```2.42```| ```2.97```|![](charts/red.png)| 
|Median|```4.07```| ```3.82```|![](charts/green.png)| 
|Mean|```3.96```| ```3.92```|![](charts/green.png)| 
|3rd Qu.|```5.47```| ```4.88```|![](charts/green.png)| 
|Max.|```276.2```| ```286.22```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.22```| ```0.26```|![](charts/red.png)| 
|10%|```0.94```| ```2.42```|![](charts/red.png)| 
|20%|```2.1```| ```2.81```|![](charts/red.png)| 
|30%|```2.71```| ```3.13```|![](charts/red.png)| 
|40%|```3.3```| ```3.5```|![](charts/red.png)| 
|50%|```4.07```| ```3.82```|![](charts/green.png)| 
|60%|```4.7```| ```4.2```|![](charts/green.png)| 
|70%|```5.29```| ```4.62```|![](charts/green.png)| 
|80%|```5.69```| ```5.1```|![](charts/green.png)| 
|90%|```6.27```| ```5.43```|![](charts/green.png)| 
|100%|```276.2```| ```286.22```|![](charts/red.png)| 


![Chart of Deno udp_server](charts/deno__udp_server__25.png)
![Chart of Node.js udp_server](charts/node__udp_server__25.png)

Deno is ```7.08%``` faster than Node.js. ![](charts/green.png)

### A simple message exchange over WebSocket
Receive a message over WebSocket, and echo it back.
* [Deno Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/deno_ws_server.ts)
* [Node Code](https://github.com/mayankchoubey/deno-vs-nodejs/blob/master/node_ws_server.js)
#### Concurrency=1
Here is the overview of the readings:
Total requests: ```1000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```1777```| ```9687```|![](charts/red.png)| 
|ReqPerSec|```562```| ```103```|![](charts/red.png)| 
|Min.|```0.9```| ```0.86```|![](charts/green.png)| 
|1st Qu.|```1.07```| ```0.97```|![](charts/green.png)| 
|Median|```1.15```| ```1.06```|![](charts/green.png)| 
|Mean|```1.22```| ```9.17```|![](charts/red.png)| 
|3rd Qu.|```1.27```| ```1.21```|![](charts/green.png)| 
|Max.|```4.95```| ```1919.72```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.9```| ```0.86```|![](charts/green.png)| 
|10%|```1.03```| ```0.92```|![](charts/green.png)| 
|20%|```1.06```| ```0.95```|![](charts/green.png)| 
|30%|```1.09```| ```0.98```|![](charts/green.png)| 
|40%|```1.12```| ```1.02```|![](charts/green.png)| 
|50%|```1.15```| ```1.06```|![](charts/green.png)| 
|60%|```1.19```| ```1.1```|![](charts/green.png)| 
|70%|```1.24```| ```1.17```|![](charts/green.png)| 
|80%|```1.32```| ```1.27```|![](charts/green.png)| 
|90%|```1.47```| ```1.61```|![](charts/red.png)| 
|100%|```4.95```| ```1919.72```|![](charts/red.png)| 


![Chart of Deno ws_server](charts/deno__ws_server__1.png)
![Chart of Node.js ws_server](charts/node__ws_server__1.png)

Deno is ```81.66%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=10
Here is the overview of the readings:
Total requests: ```10000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```6344```| ```105550```|![](charts/red.png)| 
|ReqPerSec|```1576```| ```94```|![](charts/red.png)| 
|Min.|```0.97```| ```0.84```|![](charts/green.png)| 
|1st Qu.|```3.47```| ```2.19```|![](charts/green.png)| 
|Median|```4.25```| ```2.71```|![](charts/green.png)| 
|Mean|```4.41```| ```83.63```|![](charts/red.png)| 
|3rd Qu.|```5.06```| ```3.56```|![](charts/green.png)| 
|Max.|```107.59```| ```26086.72```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```0.97```| ```0.84```|![](charts/green.png)| 
|10%|```2.68```| ```1.88```|![](charts/green.png)| 
|20%|```3.26```| ```2.09```|![](charts/green.png)| 
|30%|```3.65```| ```2.28```|![](charts/green.png)| 
|40%|```3.95```| ```2.48```|![](charts/green.png)| 
|50%|```4.25```| ```2.71```|![](charts/green.png)| 
|60%|```4.52```| ```2.98```|![](charts/green.png)| 
|70%|```4.85```| ```3.32```|![](charts/green.png)| 
|80%|```5.3```| ```3.9```|![](charts/green.png)| 
|90%|```6.08```| ```5.15```|![](charts/green.png)| 
|100%|```107.59```| ```26086.72```|![](charts/red.png)| 


![Chart of Deno ws_server](charts/deno__ws_server__10.png)
![Chart of Node.js ws_server](charts/node__ws_server__10.png)

Deno is ```93.99%``` slower than Node.js. ![](charts/red.png)
#### Concurrency=25
Here is the overview of the readings:
Total requests: ```25000```



| Reading | Node.js | Deno ||
| ------- | ------- | ---- |---|
|TimeTakenMS|```15981```| ```252679```|![](charts/red.png)| 
|ReqPerSec|```1564```| ```98```|![](charts/red.png)| 
|Min.|```1.05```| ```0.86```|![](charts/green.png)| 
|1st Qu.|```9.74```| ```6.7```|![](charts/green.png)| 
|Median|```11.42```| ```10.71```|![](charts/green.png)| 
|Mean|```11.6```| ```234.66```|![](charts/red.png)| 
|3rd Qu.|```13.07```| ```17.35```|![](charts/red.png)| 
|Max.|```164.55```| ```13319.53```|![](charts/red.png)| 


And, here is the detailed distribution (10% quantiles) of the readings:

| Quantile | Node.js | Deno ||
| ------- | ------- | ---- |---|
|0%|```1.05```| ```0.86```|![](charts/green.png)| 
|10%|```6.53```| ```4.39```|![](charts/green.png)| 
|20%|```9.08```| ```6.01```|![](charts/green.png)| 
|30%|```10.22```| ```7.46```|![](charts/green.png)| 
|40%|```10.87```| ```8.99```|![](charts/green.png)| 
|50%|```11.42```| ```10.71```|![](charts/green.png)| 
|60%|```11.97```| ```12.71```|![](charts/red.png)| 
|70%|```12.65```| ```15.36```|![](charts/red.png)| 
|80%|```13.6```| ```20.06```|![](charts/red.png)| 
|90%|```15.49```| ```1921.39```|![](charts/red.png)| 
|100%|```164.55```| ```13319.53```|![](charts/red.png)| 


![Chart of Deno ws_server](charts/deno__ws_server__25.png)
![Chart of Node.js ws_server](charts/node__ws_server__25.png)

Deno is ```93.68%``` slower than Node.js. ![](charts/red.png)

## Next steps

There is a lot more work to be done! If you like to suggest more benchmarks, please add an issue with your suggestions.

Also, please add a star to this repository if it has been valuable. More stars means more readers and this would encourage us to keep the benchmark running.
