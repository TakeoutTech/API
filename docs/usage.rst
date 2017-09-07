POSTMan
========

Useful POSMan scripts... 

.. attention::
  [work in progress]
  
**cURL script**
.. code::
  curl -X POST
  https://dev.takeouttech.com/auth/token
  -d 'grant_type=password&client_id=YXBwbGljYXRpb25hcGlrZXkxODM%3D&client_secret=YXBwbGljYXRpb25zZWNyZXRrZXkzMDg%3D'
  ``
**C# RestSharp**
.. code::
  var client = new RestClient("https://dev.takeouttech.com/auth/token");
  var request = new RestRequest(Method.POST);
  request.AddHeader("content-type", "application/x-www-form-urlencoded");
  request.AddParameter("application/x-www-form-urlencoded", "grant_type=password&client_id=YXBwbGljYXRpb25hcGlrZXkxODM%3D&client_secret=YXBwbGljYXRpb25zZWNyZXRrZXkzMDg%3D", ParameterType.RequestBody);
  IRestResponse response = client.Execute(request);
