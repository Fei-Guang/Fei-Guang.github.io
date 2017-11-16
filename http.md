# GET vs. POST
HTTP POST requests supply additional data from the client (browser) to the server in the message body. 
In contrast, GET requests include all required data in the URL. Forms in HTML can use either method by
specifying method="POST" or method="GET" (default) in the <form> element. The method specified determines 
how form data is submitted to the server. When the method is GET, all form data is encoded into the URL, 
appended to the action URL as query string parameters. With POST, form data appears within the message body 
of the HTTP request

Authors of services which use the HTTP protocol SHOULD NOT use GET based forms for the submission of sensitive data, because this will cause this data to be encoded in the Request-URI. Many existing servers, proxies, and user agents will log the request URI in some place where it might be visible to third parties. Servers can use POST-based form submission instead

Finally, an important consideration when using GET for AJAX requests is that some browsers - IE in particular - will cache the results of a GET request. So if you, for example, poll using the same GET request you will always get back the same results, even if the data you are querying is being updated server-side. One way to alleviate this problem is to make the URL unique for each request by appending a timestamp.

Restrictions on form data length	Yes, since form data is in the URL and URL length is restricted. A safe URL length limit is often 2048 characters but varies by browser and web server.

From the Dropbox developer blog:
```
    a browser doesn’t know exactly what a particular HTML form does, 
    but if the form is submitted via HTTP GET, the browser knows it’s
    safe to automatically retry the submission if there’s a network error.
    For forms that use HTTP POST, it may not be safe to retry so the browser
    asks the user for confirmation first.
```
A "GET" request is often cacheable, whereas a "POST" request can hardly be. For query systems this may have a considerable efficiency impact, especially if the query strings are simple, since caches might serve the most frequent queries.

http://www.diffen.com/difference/GET-vs-POST-HTTP-Requests

# rotate catalina out without restarting tomcat

The catalina.out file is created by a shell redirection, ex ">> catalina.out 2>&1".  This catches anything written to System.out and System.err and places it into the catalina.out file. 
Given this, a good way to rotate catalina.out is to alter the script to pipe the output to a log rotation script rather than directly to a file.  This will allow you to rotate the logs without restarting Tomcat and without copying the entire contents of the log to another file.
It's a pretty simple change to catalina.sh and it is described at this link.

    http://marc.info/?l=tomcat-user&m=105640876032532&w=2
    https://dzone.com/articles/how-rotate-tomcat-catalinaout
    

    cat /dev/null > logs/catalina.out
