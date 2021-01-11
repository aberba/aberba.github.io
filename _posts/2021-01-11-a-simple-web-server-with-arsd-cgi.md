---
title: "Building a simple Web server with arsd CGI framework"
date: 2021-01-11 10:20:23
categories: [programming]
tags: [D, arsd, webdev]
---

![No one](/images/2021-arsd-cgi-web-demo.png)

Frameworks for building web servers in the D programming language come with
different conventions and design choices. I previously wrote about using the
vibe.d web framework both in it's
[route-base style](https://aberba.com/page2/2016/hello-world-app-with-the-vibe.d-web-framework/)
and declarative
[web interface](https://aberba.com/2018/using-vibe-d-web-interface/) style.
However there's another alternative, the
[CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface) style, which the
[arsd CGI](http://dpldocs.info/experimental-docs/arsd.cgi.html) web framework
was designed with (kind of).

> Ards CGI is just one module among a
> [collection](https://code.dlang.org/packages/arsd-official) of modules under
> the arsd namespace.

The interesting thing about using arsd for me is it's simplicity and how
lightweight it is. It's quite straightforward to get a web server up and running
with very few lines of code. Moreover, arsd by default comes with zero system
dependencies. It does not require you to install any system package to use
unlike vibe.d. This advantage makes arsd easy to run in any environment
especially when you do not have system access to install system dependencies
(cloud functions, PaaS, etc).

> Zero system dependencies!!

Now, I'm will be using the D package manager, dub, to run the server app. Create
a dub projects by running `dub init arsd-cgi-demo` command from your command
line where `arsd-cgi-demo` is your project's name. Make sure to add
`arsd-official:cgi` when prompted to add a dependency as follows:

> The D package manager called [dub](https://dub.pm/getting_started) to create
> and run the project. Dub comes bundled with the D compiler when installed.

```sh
dub init arsd-cgi-demo
Package recipe format (sdl/json) [json]:
Name [arsd-cgi-demo]:
Description [A minimal D application.]:
Author name [aberba]:
License [proprietary]:
Copyright string [Copyright © 2021, aberba]:
Add dependency (leave empty to skip) []: arsd-official:cgi
Adding dependency arsd-official:cgi ~>9.0.4
Add dependency (leave empty to skip) []:
Successfully created an empty project in '/home/aberba/workspace/d/arsd-cgi-demo'.
Package successfully created in arsd-cgi-demo
```

So lets see a sample ards server:

```d
import arsd.cgi;

void handler(Cgi cgi)
{
	cgi.setResponseContentType("text/html");

	switch (cgi.pathInfo)
	{
	case "/":
		cgi.write("Hello, World!");
		break;

		// other routes go here

	default:
		cgi.setResponseStatus("404 Not found");
		cgi.write("Requested page not found.");
		break;
	}
}

void main()
{
	RequestServer server;
	server.listeningPort = 9000;
	server.serve!handler;
}
```

That's all it takes. You first create a handler which takes a `Cgi` parameter
with all the facilities to handle both receiving an http request and sending a
response.

`cgi.pathInfo` is used to match the request route and response according. You
may also use `cgi.requestMethod` to also match the request method which may be
one of `cgi.RequestMethod.GET`, `cgi.RequestMethod.POST`,
`cgi.RequestMethod.PATCH` and friends. The following code show how you may do
that in the `handler` function:

```d
void handler(Cgi cgi)
{
	cgi.setResponseContentType("text/html");

	switch (cgi.pathInfo)
	{
	case "/":
		if (cgi.requestMethod == cgi.RequestMethod.GET)
		{
			cgi.write("Hello from GET");
		}
		else
		{
			// you may also send 404, whatever you want, 🤷‍♀️

			cgi.write("Hello work something else");

		}
		break;

		// other routes go here

	default:
		cgi.setResponseStatus("404 Not found");
		break;
	}
}
```

You may also notice the `cgi.setResponseStatus()` method for sending both a
response status code and string. The prefix, `404`, becomes the response code
whilst the text that follows, in this case `Not found`, then becomes the
response text. This is a convention used in certain aspects of arsd. I will dive
into those aspects in another post later.

Now since arsd is written in D with a very powerful metaprogramming support, it
is capable fro abstracting things to minimize the lines of code needed to
implement certain functionalities. Let's see how arsd support the idiomatic D
way setting up the web server:

```d
void handler(Cgi cgi)
{
    // the rest of the content goes here
}

GenericMain!handler;
```

That's it!. No need to manually initialize a request server or register a port
manually. Arsd takes care of generating the code needed to handle all of that
for you. Pretty need.

This is just a tease of what arsd CGI web framework can do. Its also supports a
declarative of handling requests with a URL
[dispatcher](http://dpldocs.info/experimental-docs/arsd.cgi.dispatcher.html). I
will write about later.

Now it's not all rainbow and sunshine with arsd CGI. It does not support all the
features you might get **out of the box** with Vibe.d such a SSL cert
integration (you may use NGINX as a proxy to handle SSL). This might be good
thing or bad depending on what you are used to or your use case. As mentioned,
arsd CGI is just one module in a whole
[arsd collection](http://dpldocs.info/experimental-docs/arsd.html). It's meant
for you to pick and choose additional modules based on your needs including
packages available
inhttp://dpldocs.info/experimental-docs/arsd.cgi.dispatcher.html the
[D package repository](https://code.dlang.org).
