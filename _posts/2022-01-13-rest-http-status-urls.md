---
layout: post
title: Coding Challenge 14
subtitle: .NET Bootcamp Research Notes
tags: [C#,.NET, API,REST,gRPC, DESIGN API URLS, HTTP Status Codes,]
comments: false
---

<p style='text-align: justify;'>
In this tutorial, we are going to talk about some important topics such as  API, REST, RPC, HTTP Methods...
</p>


#### API(application programming interface) 

<p style='text-align: justify;'>
An API is an interface that enables applications to exchange data among each other. Many companies use an apı to speed up their jobs. They can constrain and extend access depending on the authorization.  By using an API, we constrain clients to access directly to our applications. So, how do applications communicate among each other?
Depending on needs, some companies prefer JSON, XML, SOAP, RPC...
If an API conforms rest standards, it is called restful.
</p>

#### JSON
<p style='text-align: justify;'>
JSON stands for Javascript object notation, is a lightweight data-interchange format. It stores data key/value form.
For instance, i added a sample of json data.</p> 

```JSON
{
    students:[
        {
            'id':1,
            'FirstName':'Bob',
            'LastName': 'Marley',
            'Job': 'Musician'

        },
        {
            'id':2,
            'FirstName':'Bob',
            'LastName': 'Dylan',
            'Job': 'Musician'
        }

    ]
}

```

#### XML
<p style='text-align: justify;'>
XML is the abbreviation of extensible markup language. It ıs also store and transport data. If you know about HTML, it would be easy to read and understand an XML file. It would be better to apply standards and extensions of XML to benefit from the power of XML.</p> 

```XML
<students>
  <student>
    <firstName>Bob</firstName> <lastName>Marley</lastName><Job>Musician</Job>
  </student>
  <student>
    <firstName>Bob</firstName> <lastName>Dylan</lastName><Job>Musician</Job>
  </student>
 
</students>
```

[Standarts and extensions](https://www.ibm.com/docs/en/i/7.1?topic=introduction-xml-standards-extensions#rzamjintrostandards__Namespaces)

#### gRPC
<p style='text-align: justify;'>
It is an open-source, high-performance framework that makes it easier for us to create distributed applications and services. It is used to serialize structured data. Being a protocol based on a binary makes it faster than text-based protocol. It's even  faster than JSON.</p>

[Details](https://grpc.io/)
[Details on Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/grpc)
[Protocol-buffers](https://developers.google.com/protocol-buffers/docs/overview)



#### Soap
<p style='text-align: justify;'>
Soap stands for simple object access protocol. Briefly, it's based on XML that enables to exchange data among the computers. There are several advantages of soap like platform and language independent.  Soap provides data transports, enables connections between different endpoints.</p>



#### Rest(Representational State Transfer)
<p style='text-align: justify;'>
It ıs an architecture style that has following constrains:
<ul>
<li>Uniform interface</li>
<li>Client–server (Client and server side must be open to develop independently.)</li>
<li>Stateless  (A request should contain all necessary information to service the request.)</li>
<li>Cacheable</li>
<li>Layered system</li>
</ul> 
</p>
[Best-practices/api-design](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design)
[rest-api-standards-do-they-even-exist](https://blog.stoplight.io/rest-api-standards-do-they-even-exist)
[Best-practices-for-rest-api-design](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)

https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/

#### Uniform Resource Identifier (URI)
<p style='text-align: justify;'>
In an API design, clients must access resources using a hierarcical order. For instance:</p>```https://my-api.com/api/v1/users/123456/books ```.
<ul>
<li>Do not use underscore(_) </li>
<li>Collections are specified in the URL with plural names.</li>
<li>A Document is specified in the URL with a singular name. </li>
<li>Do not use camel case </li>
<li>Allow filtering, sorting, and pagination</li>
<li>Nest resources for hierarchical objects </li>
</ul> 
...

[Details](https://datatracker.ietf.org/doc/html/rfc3986#section-1.1.1)

#### HTTP Methods
<p style='text-align: justify;'>
Let's start learning some key words like idempotent, Safe, Cacheable...</p> 


#### Idempotent
<p style='text-align: justify;'>
If the result does not change when you make one or more requests, we call this HTTP method idempotent.
 Here are some examples of idempotent methods: GET, HEAD, PUT, DELETE, OPTIONS, TRACE.
>An HTTP method is idempotent if an identical request can be made once or several times in a row with the same effect while leaving the server in the same state. </p>

##### GET
<p style='text-align: justify;'>
The HTTP GET method is used to retrieve data from a specified resource. For security reasons, do not use GET method to send pieces of information like email and password because your email and password will be shown on the search area as below.
For instance, here i get data of a specified product having id = 2.</p>

<code>
{
  "id": 2,
  "categoryId": 3,
  "productName": "Phone",
  "publishingDate": "2022-01-13T10:49:38.6979609+03:00"
}
</code>

##### HEAD
<p style='text-align: justify;'>
It's similar to GET method, but the response does not have a message-body. It's often used to retrieve meta-data. Meta-data might contain information about keywords, content-type, page description, author, viewport,content-encoding...
</p>

##### PUT
The PUT method enables us to send data for update operations. If an error occurs while creating an object, you can return HTTP 500 status code.

<code>
 [HttpPut("{id}")]
</code>

##### DELETE
It ıs used to delete a specified resouces. 

<code>
[HttpDelete("{id}")]
</code>


##### OPTIONS
>The OPTIONS method describes the communication options for the target resource.


#### Non Idempotent

##### POST
The HTTP POST is used to submit data to the server. If you create a new object, you can return HTTP 201 status code.

<code>
[HttpPost]
</code>

##### PATCH
It's used to update partial informations from a specific resource.

<code>
[HttpPatch("{id}")]
</code>

#### Safe
>An HTTP method is safe if it doesn't alter the state of the server. In other words, a method is safe if it leads to a read-only operation.


#### Cacheable
>A cacheable response is an HTTP response that can be cached, that is stored to be retrieved and used later, saving a new request to the server. 


##### Common HTTP Status Codes
200: This code indicates that the request is successful.
<code>return Ok()</code>

400:  If a client enters an invalid request, we see this code.
<code>return BadRequest()</code></br>
401: If a unauthoried user try to access a resource, the server usually returns this code. I added an example of the way that we return the status 401 code.

```c#
[HttpGet("/panel/{authorization}")]
    public IActionResult HowToReturn401(string authorization)
    {
        if (authorization=="user")
        {
            return Unauthorized();//401
        }
        return Ok();
    }
```

403: If a use is auhenticated, but it's not allowed to  access a resource. Suppose that a user is not allowed to access vip panel, the server can return the status 403 code as below.

```c#
[HttpGet("/panel/vip/{authorization}")]
public IActionResult HowToReturn403(string authorization)
{
    if (authorization == "user")
    {
        return StatusCode(403);// Forbidden
    }
    return Ok();
}

```
404: Not Found
```c#
return NotFound();

```
500: Internal server error 
```c#
 return StatusCode(500);

```

502 Bad Gateway – This indicates an invalid response from an upstream server.
```c#
 return StatusCode(502);

```
503: Service Unavailable

```c#
[HttpGet("/admin")]
public IActionResult HowToReturn503()
{
  
    return StatusCode(503);
}

```

[Web/HTTP/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
