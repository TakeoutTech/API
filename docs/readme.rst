Welcome
========
Welcome to the TakeoutTech integration API.

This site will help you augment your great product with our Menu, Location, Order and POS integration services. We are very excited to see what you come up with.

The TakeoutTech API consists a set of REST style endpoints. All methods must be inovked using HTTPS, with arguments passed as GET/POST/PUT/DELETE parameters, or as JSON object within the body of the request.

This site will be a great resource throughout your project for finding information on our REST API.  Good luck!

Getting Started
---------------

Contact TakeoutTech to obtain your API credentials.

Once your request is granted, you may obtain the following information from the TakeoutTech portal or through your contact representative:

* client_id
* client_secret

What's next and Quick-Start Steps
---------------------------------

Development/Production base urls:

* Developement: https://dev.takeouttech.com
* Production: (TBA)

Quick-Start
~~~~~~~~~~~
**Step 1: Athentication - obtaining the OAuth 2.0 Token**

OAuth 2.0 is a protocol that allows your application to request authorization for access to granted services.

POST ``/api/auth/token``
  * client_id = [the_client_id]
  * client_secret = [the_client_secret]
  * grant_type = password

A bearer token will be returned, this token must be passed along with every request to the TakeoutTech API endpoints.

**Step 2: Accessing a Service**

Depending on the desirable action, note the GET, POST, PUT, DELETE action used along with the request.

Example:

GET ``/api/client/locations``
  * [header] Authorization: Bearer [the bearer token obtained in Step 1]

This request will return a list of locations configured for the given client_id, client_secret pair.

Quick links
~~~~~~~~~~~
* :doc:`/api/client`
* :doc:`/api/menu`
* :doc:`/api/order`
* :doc:`/api/pos`

Tools
~~~~~
POSTMAN scripts [work in progress]
- scripts
