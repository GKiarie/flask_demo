RESTful API

Central to the concept of RESTful web services is the notion of resources. Resources are represented by URIs. The clients send requests to these URIs using the methods defined by the HTTP protocol, and possibly as a result of that the state of the affected resource changes.



REST:
REpresentational
State
Transfer

***********************************
Constaraints:
**********************************
1. Uniform Interface - The method of communication between a client and a server must be uniform.

2. Statelessness - Each request from a client must contain all the information required by the server to carry out the request. In other words, the server cannot store information provided by the client in one request and use it in another request.

3. Cacheable -  The server must indicate to the client if requests can be cached or not.

4. Client_server -  There should be a separation between the server that offers a service, and the client that consumes it.

5. Layered System - Communication between a client and a server should be standardized in such a way that allows intermediaries to respond to requests instead of the end server, without the client having to do anything different.

6. Code on Demand (optional) - Servers can provide executable code or scripts for clients to execute in their context. This constraint is the only one that is optional.

**************************************
Idempotency
**************************************

From a RESTful service standpoint, for an operation (or service call) to be idempotent, clients can make that same call repeatedly while producing the same result.
Making multiple identical requests has the same effect as making a single request.
PUT
DELETE - Both considered idempotent

GET, HEAD, OPTIONS, TRACE - only for retriecing data. Idempotent simce multiple, identical requests will have the same outcomes

*************************
HTTP Status Codes
*************************
https://www.restapitutorial.com/httpstatuscodes.html

************************
REST API Cheat Sheet
*************************
https://github.com/RestCheatSheet/api-cheat-sheet#api-design-cheat-sheet

*********************************
Designing a Simple Web Service
*********************************
Identify the resources that will be exposed and how they will be affected by the different request methods.
Let's say we want to write a To Do List application and we want to design a web service for it. The first thing to do is to decide what is the root URL to access this service.

e.g.

http://[hostname]/todo/api/v1.0/

Here I have decided to include the name of the application and the version of the API in the URL. Including the application name in the URL is useful to provide a namespace that separates this service from others that can be running on the same system. Including the version in the URL can help with making updates in the future, since new and potentially incompatible functions can be added under a new version, without affecting applications that rely on the older functions.

select the resources that will be exposed by this service
Our tasks resource will use HTTP methods as follows:

GET     http://[hostname]/todo/api/v1.0/tasks       Retrieve list of tasks
GET     http://[hostname]/todo/api/v1.0/tasks/[task_id]     Retriev a task
POST    http://[hostname]/todo/api/v1.0/tasks               Create anew task
PUT     http://[hostname]/todo/api/v1.0/tasks/[task_id]     Update existimg task
DELETE  http://[hostname]/todo/api/v1.0/tasks/[task_id]     Delete a task

We can define a task as having the following fields:

id: unique identifier for tasks. Numeric type.
title: short task description. String type.
description: long task description. Text type.
done: task completion state. Boolean type.

And with this we are basically done with the design part of our web service. All that is left is to implement it!