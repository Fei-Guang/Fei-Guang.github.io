# GET vs. POST
HTTP POST requests supply additional data from the client (browser) to the server in the message body. 
In contrast, GET requests include all required data in the URL. Forms in HTML can use either method by
specifying method="POST" or method="GET" (default) in the <form> element. The method specified determines 
how form data is submitted to the server. When the method is GET, all form data is encoded into the URL, 
appended to the action URL as query string parameters. With POST, form data appears within the message body 
of the HTTP request

Authors of services which use the HTTP protocol SHOULD NOT use GET based forms for the submission of sensitive data, because this will cause this data to be encoded in the Request-URI. Many existing servers, proxies, and user agents will log the request URI in some place where it might be visible to third parties. Servers can use POST-based form submission instead

Finally, an important consideration when using GET for AJAX requests is that some browsers - IE in particular - will cache the results of a GET request. So if you, for example, poll using the same GET request you will always get back the same results, even if the data you are querying is being updated server-side. One way to alleviate this problem is to make the URL unique for each request by appending a timestamp.

http://www.diffen.com/difference/GET-vs-POST-HTTP-Requests
