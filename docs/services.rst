Services
===============
.. note::
    Visit https://www.takeouttech.com, login to the Portal to obtain your api credentials.
    
The response data will be returned in a standard reponse wrapper as below:

Sample Success Response:

.. code:: javascript

    {
    "StatusCode": 200,
    "Message": "",
    "Data": {the data object(s)},
    "Success": true,
    "ClassType": "name of data"
    }
    
Sample Failure resopnse:

.. code:: javascript

    {
    "StatusCode": [the error code],
    "Message": "The failure message.",
    "Data": null,
    "Success": false,
    "ClassType": "name of data"
    }

:doc:`/api/client`
--------------
Base URL + ``/api/client``

* All locations
* Location Detail
* Location Configuration

:doc:`/api/menu`
--------------
Base URL + ``/api/menu``

* Menu
* Items
* Modifiers

:doc:`/api/order`
--------------
Base URL + ``/api/order``

* Submit Order
* Update Order
* Cancel Order
* Order Status


:doc:`/api/pos`
--------------
Base URL + ``/api/pos``

* Configuration
* Remote Operations
* Status
