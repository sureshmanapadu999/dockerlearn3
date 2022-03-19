We can decide whether our application is 
"not fully RESTful" or "almost RESTful" or "not RESTful at all" by using a model developed by Leonard Richardson.

 Every REST API belongs to one of these 4 levels
*  Level 0(SOAP based web services)(not rest)
*  Level 1(we use concept of resource URIs)(not fully rest)
*  Level 2(we use different HTTP methods for these different operations example: create-POST, read-GET, update-PUT, delete-DELETE)(almost rest)
*  Level 3( we implement HATEOAS)(fully rest)

HATEOAS
HATEOAS(Hypermedia as the Engine of Application State) is a way to provide links to resources in the API response, so that the client doesn't have to deal with URI construction and business flow. They make a request, and the next steps, along with the URIs are handed to them in the response. When you write APIs, you can choose to add URIs in the response using the href attribute. You can also provide more information about the relationship of the linked resource using the rel attribute.

source:
Please go through the article: http://martinfowler.com/articles/richardsonMaturityModel.html
