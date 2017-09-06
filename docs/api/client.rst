.. _rest_encoding:

Client Service
--------------

Use this service to obtain location information 


GET ``/api/client/locations``
~~~~~~~~~~~~~~~~~~~~~~~~

Example Response:

.. code:: javascript

  [
      {
          "ID": "d48c30e0-3c52-450f-b068-fcd8bcb47d7f",
          "Name": "Takeout Cafe",
          "Active": true
      },
      {
          "ID": "d3ad210d-c8b1-449e-8389-bd82e20e327f",
          "Name": "Takeout Cafe - WebLinkx",
          "Active": true
      },
      {
          "ID": "466ba466-f9e8-4a9d-8248-da483944936f",
          "Name": "Takeout Cafe - Kiosk",
          "Active": true
      }
  ]


GET ``/api/client/location``
~~~~~~~~~~~~~~~~~~~~~~~~
  * id: string, the GUID for this location

Example Response:

.. code:: javascript

  {
      "Phone": "(212) 983-7374",
      "Fax": "(212) 953-7378",
      "MenuID": "7ca9aafd-9ec2-4bff-8224-a4a7cc9710f9",  //**this is the MenuID for this location**
      "Address": {
          "ID": 2774628,
          "Street": " Lexington Avenue",
          "Apartment": "",
          "City": "New York",
          "State": "NY",
          "Zip": "10028",
          "Line1Summary": "Lexington Avenue Lexington Avenue",
          "Line2Summary": "New York, NY 10028"
      },
      "PickupHours": [
          {
              "DayOfWeek": 1,
              "Day": "Monday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "6:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "9:00 PM"
          },
          {
              "DayOfWeek": 2,
              "Day": "Tuesday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "6:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "9:00 PM"
          },
          {
              "DayOfWeek": 3,
              "Day": "Wednesday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "6:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "9:00 PM"
          },
          {
              "DayOfWeek": 4,
              "Day": "Thursday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "6:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "9:00 PM"
          },
          {
              "DayOfWeek": 5,
              "Day": "Friday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "6:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "9:00 PM"
          },
          {
              "DayOfWeek": 6,
              "Day": "Saturday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "7:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "8:00 PM"
          },
          {
              "DayOfWeek": 7,
              "Day": "Sunday",
              "LunchPrepTime": 30,
              "LunchOpenTime": "7:00 AM",
              "LunchCloseTime": "12:00 PM",
              "DinnerPrepTime": 30,
              "DinnerOpenTime": "12:01 PM",
              "DinnerCloseTime": "8:00 PM"
          }
      ],
      "DeliveryHours": [
          {
              "DayOfWeek": 1,
              "Day": "Monday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          },
          {
              "DayOfWeek": 2,
              "Day": "Tuesday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          },
          {
              "DayOfWeek": 3,
              "Day": "Wednesday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          },
          {
              "DayOfWeek": 4,
              "Day": "Thursday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          },
          {
              "DayOfWeek": 5,
              "Day": "Friday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          },
          {
              "DayOfWeek": 6,
              "Day": "Saturday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          },
          {
              "DayOfWeek": 7,
              "Day": "Sunday",
              "LunchPrepTime": 15,
              "LunchOpenTime": "12:00 AM",
              "LunchCloseTime": "12:00 AM",
              "DinnerPrepTime": 15,
              "DinnerOpenTime": "12:00 AM",
              "DinnerCloseTime": "12:00 AM"
          }
      ],
      "Holidays": [],
      "ID": "483915c0-38d3-4f66-8fdf-0907ef68fa06",
      "Name": "Fresh & Co. (85th/Lex)",
      "Active": false
  }
