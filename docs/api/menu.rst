.. _rest_encoding:

Menu Service
------------

Use this service to obtain menu detail.
Menu data are returned in two modes:
#. Full [TBI]
#. Simplfied [current]

.. note::

  The modifiers for an item are embeded in the hierarchical data section of the item, some of these are repeated.
  Detail information on menu items may be obtain through <item> queries.

GET ``/api/menu``
~~~~~~~~~~~~~~~~~~~~~~~~
  * id: string, the GUID for this Menu

Example Request:

.. code:: javascript

  curl -X GET \
    'http://dev.takeouttech.com/api/menu?id=[theMenuGUID]' \
    -H 'authorization: Bearer [theToken]

Example Response:

.. code:: javascript

  {
      "MenuID": 12528,
      "Name": "",
      "Categories": [
          {
              "ID": 209426,
              "MenuID": 12528,
              "Name": "Catering - Sides",
              "Notes": "",
              "Sequence": 0,
              "Items": [
                  {
                      "ID": 1669072,
                      "MenuID": 12528,
                      "MenuGroupID": 209426,
                      "MenuPeriodID": 36768,
                      "MenuTypeID": 16233,
                      "Reference": "755",
                      "Sequence": -1,
                      "Description": "Sour Cream (Serves 5)",
                      "Notes": "",
                      "Retail": 10,
                      "Taxable": true,
                      "Online": true,
                      "PrepTime": 0,
                      "OutOfStock": "",
                      "Discontinued": false,
                      "PosID": "",
                      "TypeName": "Catering",
                      "ImageUrl": "",
                      "Availability": {
                          "Name": "Lunch & Dinner",
                          "StartDate": "10/4/2012",
                          "EndDate": "10/4/2099",
                          "StartTime": "12:00 AM",
                          "EndTime": "11:59 PM",
                          "Weekday": {
                              "Monday": true,
                              "Tuesday": true,
                              "Wednesday": true,
                              "Thursday": true,
                              "Friday": true,
                              "Saturday": true,
                              "Sunday": true
                          }
                      },
                      "Options": []
                  },
                  {
                      "ID": 1669067,
                      "MenuID": 12528,
                      "MenuGroupID": 209426,
                      "MenuPeriodID": 36768,
                      "MenuTypeID": 16233,
                      "Reference": "750",
                      "Sequence": 35,
                      "Description": "Rice",
                      "Notes": "",
                      "Retail": 0,
                      "Taxable": true,
                      "Online": true,
                      "PrepTime": 0,
                      "OutOfStock": "",
                      "Discontinued": false,
                      "PosID": "",
                      "TypeName": "Catering",
                      "ImageUrl": "",
                      "Availability": {
                          "Name": "Lunch & Dinner",
                          "StartDate": "10/4/2012",
                          "EndDate": "10/4/2099",
                          "StartTime": "12:00 AM",
                          "EndTime": "11:59 PM",
                          "Weekday": {
                              "Monday": true,
                              "Tuesday": true,
                              "Wednesday": true,
                              "Thursday": true,
                              "Friday": true,
                              "Saturday": true,
                              "Sunday": true
                          }
                      },
                      "Options": []
                  }
        ]
      }
    ]
  }
