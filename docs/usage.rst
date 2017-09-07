.. _rest_encoding:

Usage Examples
==============

Useful POSMan scripts... 

.. attention::
  [work in progress]
  
**cURL script**

.. code:: javascript

  var settings = {
    "async": true,
    "crossDomain": true,
    "url": "https://dev.takeouttech.com/auth/token",
    "method": "POST",
    "data": {
      "grant_type": "password",
      "client_id": "YXBwbGljYXRpb25hcGlrZXkxODM=",
      "client_secret": "YXBwbGljYXRpb25zZWNyZXRrZXkzMDg="
    }
  }

  $.ajax(settings).done(function (response) {
    console.log(response);
  });

**C# RestSharp**

.. code:: C#

  var client = new RestClient("https://dev.takeouttech.com/auth/token");
  var request = new RestRequest(Method.POST);
  request.AddHeader("content-type", "application/x-www-form-urlencoded");
  request.AddParameter("application/x-www-form-urlencoded", "grant_type=password&client_id=YXBwbGljYXRpb25hcGlrZXkxODM%3D&client_secret=YXBwbGljYXRpb25zZWNyZXRrZXkzMDg%3D", ParameterType.RequestBody);
  IRestResponse response = client.Execute(request);
