<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>REDIRECT</title>
    <style>
        html {
            font-size: 20px;
        }

        body {
            max-width: 700px;
            padding: 30px;
            border: 16px groove orangered;
            margin: 0 auto;
        }

        h1, p, pre {
            padding: 0;
            border: 0;
            margin: 0;
        }

        h1 {
            margin: 30px 0 0 0;
        }

        p {
            margin: 16px 0 0 0;
        }

        pre {
            background-color: rgba(211, 211, 211, 0.45);
            border: 1px solid black;
        }

        .discord {
            color: red;
        }
    </style>

```
</head>
<body>

<h1>301 Moved Permanently</h1>
<p>Client request:</p>
<pre>
GET /index.php HTTP/1.1
Host: www.example.org
</pre>
<p>Server response:</p>
<pre>
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/index.asp
</pre>
<p>301 tells the browser that the resource at the uri has been <strong>changed permanently</strong> to the new location specified by the value of the 'Location' response header. The browser makes a new request and <strong>subsequently the browser will NOT make another request to the original link</strong>. Even if manually typed in the address bar by the user, in this case http://www.example.org/index.php, the browser will always make the call to http://www.example.org/index.asp</p>
<p>The HTTP response status code 301 Moved Permanently is used for permanent URL redirection, meaning current links or records using the URL that the response is received for should be updated. The new URL should be provided in the Location field included with the response. The 301 redirect is considered a best practice for upgrading users from HTTP to HTTPS. RFC 2616 states that: If the 301 status code is received in response to a request of any type other than GET or HEAD, the client must ask the user before redirecting.</p>


<h1>302 Found</h1>
<p>Client request:</p>
<pre>
GET /index.html HTTP/1.1
Host: www.example.com
</pre>
<p>Server response:</p>
<pre>
HTTP/1.1 302 Found
Location: http://www.iana.org/domains/example/
</pre>
<p>302 tells the browser that the <strong>resource</strong> at the uri has been <strong>changed temporarily</strong>. The browser will <strong>redirect</strong> to the new location <strong>this time ONLY</strong>. The next time a request comes to the original uri, the browser will in fact hit the original uri.</p>
<p>The HTTP response status code 302 Found is a common way of performing URL redirection. An HTTP response with this status code will additionally provide a URL in the 'Location' header field. The user agent (e.g. a web browser) is invited by a response with this code to make a second, <strong class="discord">otherwise identical, request</strong> to the new URL specified in the location field. The HTTP/1.0 specification (RFC 1945) initially defined this code, and gives it the description phrase "Moved Temporarily".</p>
<p class="discord">Many web browsers implemented this code in a manner that violated this standard, changing the request type of the new request to GET, regardless of the type employed in the original request (e.g. POST). For this reason, HTTP/1.1 (RFC 2616) added the new status codes 303 and 307 to disambiguate between the two behaviours, with 303 mandating the change of request type to GET, and 307 preserving the request type as originally sent. Despite the greater clarity provided by this disambiguation, the 302 code is still employed in web frameworks to preserve compatibility with browsers that do not implement the HTTP/1.1 specification.</p>
<p class="discord">The update of RFC 2616 changes the definition to allow user agents to rewrite POST to GET.</p>

<h1>303 See Other</h1>
<p>Client request:</p>
<pre>
POST / HTTP/1.1
Host: www.example.com
</pre>
<p>Server response:</p>
<pre>
HTTP/1.1 303 See Other
Location: http://example.org/other
</pre>
<p>303 is almost as the <strong>same as 302</strong>, the only difference being that it tells the browser to make the second request and <strong>use the GET verb</strong> so even a POST will be converted to a GET</p>
<p>The HTTP response status code 303 "See Other" is a way to redirect web applications to a new URI, particularly after a HTTP POST has been performed, since RFC 2616 (HTTP 1.1).</p>

<p> According to RFC 7231, which obsoletes RFC 2616, "A 303 response to a GET request indicates that the origin server does not have a representation of the target resource that can be transferred by the server over HTTP. However, the Location field value refers to a resource that is descriptive of the target resource, such that making a retrieval request on that other resource might result in a representation that is useful to recipients without implying that it represents the original target resource."</p>

<p>This status code should be used with the location header, as described below. If a server responds to a POST or other non-idempotent request with a 303 See Other response and a value for the location header, the client is expected to obtain the resource mentioned in the location header <strong>using the GET method</strong>; to trigger a request to the target resource using the same method, the server is expected to provide a 307 Temporary Redirect response.</p>
<p>Daniel (paraphrased): "Good for using once you have processed a form submitted by POST method, and now that the form has been processed, redirect to a new URL using the GET method."</p>

<h1>307 Temporary Redirect</h1>
<p>Client request:</p>
<pre>
POST / HTTP/1.1
Host: www.example.com
</pre>
<p>Server response:</p>
<pre>
HTTP/1.1 307 Temporary Redirect
Location: http://example.org/other
</pre>
<p>This is the <strong>same as 302</strong> except it tells the browser that the next request should be made with the <strong>same verb as the original</strong>, in this case POST. In other words, even a POST to the original link, should redirected by a POST to the new link.</p>
<p>Daniel (paraphrased): "If you use this to redirect and the method was POST, then you redirect to the 'Location' URL and the method of the redirect will also be POST so all of the data goes with the redirect to the new 'Location.'"</p>

<h1>418 Teapot</h1>
<p>This code was defined in 1998 as one of the traditional IETF April Fools' jokes, in RFC 2324, Hyper Text Coffee Pot Control Protocol, and is not expected to be implemented by actual HTTP servers. The RFC specifies this code should be returned by tea pots requested to brew coffee. This HTTP status is used as an easter egg in some websites, including <a href="http://www.google.com/teapot">http://www.google.com/teapot</a></p>
```
````
<p><a href="https://en.wikipedia.org/wiki/HTTP_301">source: wikipedia</a></p>

<p><a href="http://blogs.msdn.com/b/tijujohn/archive/2012/06/01/different-redirect-http-response-status-codes-and-how-the-browser-should-react-301-vs-302-vs-303-vs-307.aspx">source: tijujohn</a></p>
</body>
</html>
© 2021 GitHub, Inc.
```