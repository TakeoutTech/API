.. _rest_encoding:

Usage Examples
==============

.. attention::
  [work in progress]
  
/api/auth/token
~~~~~~~~~~~~~~~

**cURL/javascript**

.. code:: cURL

  curl -X POST \
    https://dev.takeouttech.com/auth/token \
    -H 'content-type: application/x-www-form-urlencoded' \
    -d 'grant_type=password&client_id=YXBwbGljYXRpb25hcGlrZXkxODM%3D&client_secret=YXBwbGljYXRpb25zZWNyZXRrZXkzMDg%3D'

.. code:: javascript

  $.ajax({
    "async": true,
    "crossDomain": true,
    "url": "https://dev.takeouttech.com/auth/token",
    "method": "POST",
    "data": {
      "grant_type": "password",
      "client_id": "YXBwbGljYXRpb25hcGlrZXkxODM=",
      "client_secret": "YXBwbGljYXRpb25zZWNyZXRrZXkzMDg="
    }
  }).done(function (response) {
    console.log(response);
  });

**C# RestSharp**

.. code:: C#

  var client = new RestClient("https://dev.takeouttech.com/auth/token");
  var request = new RestRequest(Method.POST);
  request.AddHeader("content-type", "application/x-www-form-urlencoded");
  request.AddParameter(
    "application/x-www-form-urlencoded",
    "grant_type=password&client_id=YXBwbGljYXRpb25hcGlrZXkxODM%3D&client_secret=YXBwbGljYXRpb25zZWNyZXRrZXkzMDg%3D", 
    ParameterType.RequestBody);
  IRestResponse response = client.Execute(request);
  
  
**Sample OAuth response:**
 
.. code:: javascript
 
   {
      "access_token": "S6QFolq4p4mmTwomm3AH8mlnA8APy9AR79p0B5U-wlqFAgMujszcWEDf8Vodm9Rz4jwpfmCArjH8kRsVMiTZ2oo00KhMihSDWwuLMSEp5hyohR4rDVYUn17_DwRSYQ8w8-g2OpKbDcCR_oDofabsapdIh_Cffg7D70UT4d6jYXJewKGbLhzgHWwXwtRfRmGsag0icufxqk7RcdVifwY-_YSnBCIY1OpgcM4KYHULR-Gi7DxRNvl_zIELoF3q6Fgb9XUOgH5CVyIZWhDD3cuYBd4QzkTOaumkYjrqTLG0mEieBxJYYwqlRtkW8cWEFc9Q",
      "token_type": "bearer",
      "expires_in": 3599
  }
 
