CRUD
----

Create, Retrive, Update and Delete using 
HTTP methods POST, GET, PUT and DELETE respectively. 
For simplicity and making it work out of the box it is using
a session based fake database, thus depending on a client that
supports PHP Session Cookies. You may use [REST Console](https://chrome.google.com/webstore/detail/faceofpmfclkengnkgkgjkcibdbhemoc#)
an extension for Chrome or [RESTClient](https://addons.mozilla.org/en-US/firefox/addon/restclient/) 
a firefox extension
> This API Server is made using the following php files/folders

> * index.php      (gateway)
> * author.php      (api)
> * sessiondb.php      (helper)
> * restler.php      (framework)

This API Server exposes the following URIs

	GET    author     ⇠ Author::get()
	GET    author/:id ⇠ Author::get()
	POST   author     ⇠ Author::post()
	PUT    author     ⇠ Author::put()
	PUT    author/:id ⇠ Author::put()
	DELETE author     ⇠ Author::delete()
	DELETE author/:id ⇠ Author::delete()


Try the following links in your browser

GET [author](index.php/author)
:	
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[
 {
   "id": 1,
   "name": "Jac Wright",
   "email": "jacwright@gmail.com"
 },
 {
   "id": 2,
   "name": "Arul Kumaran",
   "email": "arul@luracast.com"
 }
]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

GET [author/2](index.php/author/2)
:	
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
{
 "id": 2,
 "name": "Arul Kumaran",
 "email": "arul@luracast.com"
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


###Creating new Author

Typical post request to create a new author will be any of the following


**Using query parameters**

	POST /examples/_006_crud/index.php/author?name=Another&email=another@email.com HTTP/1.1
	Host: restler2.dev
	Content-Length: 0
	Accept-Language: en
	X-Requested-With: XMLHttpRequest
	User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_0) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.112 Safari/535.1
	Content-Type: application/x-www-form-urlencoded; charset=UTF-8
	Accept: */*
	Accept-Encoding: gzip,deflate,sdch
	Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3
	Cookie: PHPSESSID=dcdfec433e86c1a6730f75303187071f

**Using post vars**

	POST /examples/_006_crud/index.php/author HTTP/1.1
	Host: restler2.dev
	Content-Length: 36
	Accept-Language: en
	X-Requested-With: XMLHttpRequest
	User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_0) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.112 Safari/535.1
	Content-Type: application/x-www-form-urlencoded; charset=UTF-8
	Accept: */*
	Accept-Encoding: gzip,deflate,sdch
	Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3
	Cookie: PHPSESSID=dcdfec433e86c1a6730f75303187071f

	name=Another&email=another@email.com

**Using JSON data**

	POST /examples/_006_crud/index.php/author HTTP/1.1
	Host: restler2.dev
	Content-Length: 46
	Origin: chrome-extension://faceofpmfclkengnkgkgjkcibdbhemoc
	Accept-Language: en
	X-Requested-With: XMLHttpRequest
	User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_0) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.112 Safari/535.1
	Content-Type: application/json; charset=UTF-8
	Accept: */*
	Accept-Encoding: gzip,deflate,sdch
	Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3
	Cookie: PHPSESSID=dcdfec433e86c1a6730f75303187071f
	
	{"name":"Another","email":"another@email.com"}
	

and the response could be

	HTTP/1.1 200 OK
	Date: Fri, 19 Aug 2011 16:34:41 GMT
	Server: Apache/2.2.19 (Unix) mod_ssl/2.2.19 OpenSSL/0.9.8r DAV/2 PHP/5.3.6 with Suhosin-Patch
	X-Powered-By: Luracast Restler v2.0.0
	Expires: 0
	Cache-Control: no-cache, must-revalidate
	Pragma: no-cache
	Content-Length: 66
	Content-Type: application/json
	
	{
	  "name": "Another",
	  "email": "another@email.com",
	  "id": 7
	}

*[index.php]: _006_crud/index.php
*[author.php]: _006_crud/author.php
*[sessiondb.php]: _006_crud/sessiondb.php
*[restler.php]: ../restler/restler.php
