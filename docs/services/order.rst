Order Service
-------------

Use this service to submit, update, void orders.

For POS integrated orders: Update and Void action can only be performed before the order is submitted into the restaurant's POS system;
and only sites that are configured will accept these actions.

We recommend a daily sync of sites and menus to keep their pricing current.

``/order/submit``

Sample order:
All amount values are in $.$$x100 integers
``
{
  "uuid": "[orderGUID] - leave empty", //supplied on return
  "status": "[status] - leave empty",  //supplied on return
  "statusHistory": [ //supplied on return
    {
      "status": "UNCONFIRMED",
      "timestamp": "2016-11-30T20:01:45.107Z",
      "update_source": "GRUBHUB",
      "reason": "GHCORE STATUS CALLING"
    }
  ],
  "merchant_id": "[storeGUID]", //required
  "fulfillment_info": {         //require either delivery_info or pickup_info
    "delivery_info": {          //required if delivery, null otherwise
      "address": {
        "address_line1": "line1",
        "address_line2": "line2",
        "city": "city",
        "state": "st",
        "country": "US",
        "zip_code": "12345"
      },
      "is_managed_delivery": false,                          //supplied on return
      "estimated_delivery_time": "2016-11-30T20:25:00.000Z", //supplied on return
      "instruction": "",        //optional: delivery instruction
      "contact_info": {         //required
        "phone": "(111) 222-1234",
        "name": "First Last"
      }
    },
    "pickup_info": {            //required if pickup, null otherwise
      "contact_info": {         //required
        "phone": "(111) 222-1234",
        "name": "First Last"
      }      
    }
  },
  "time_placed": "2016-11-30T19:58:15.511Z",  //required
  "when_for": "2016-11-30T20:28:15.146Z",     //required
  "payments": {                         //=== payments ===
    "payments": [                       //required
      {                                 //at least 1 payment must be present 
        "payment_type": "CASH",         //required, type: CASH, CREDIT
        "amount": 2173                  //required, amount of this payment type
      }
    ],
    "total": 2173,                      //required, total paid (to be paid)
    "adjusted_total": 2173              //required
  },
  "charges": {                          //=== chargess ===
    "fees": {                           //required if delivery
      "total": 100
    },
    "taxes": {                          //required
      "total": 90
    },
    "tip": {                            //required if has tip, other fill 0
      "amount": 283
    },
    "diner_grand_total": 2173,          //required, the extended total
    "grand_total": 2173,                //required, the order's grand total
    "line_groups": [                    //=== line groups ===
      {                                 //one per each person for group order, otherwise, 1 linegroup per order
        "label": "",                    //optional, for group order, enter name of person
        "lines": [                          //=== lines ===
          {                                 //one line object per item
            "id": "[itemPOSID]",            //required, the POSID
            "name": "Name of item",         //required
            "description": "",              //optional 
            "special_instructions": "",     //optional
            "price": 850,                   //required
            "quantity": 2,                  //required
            "diner_total": 1700,            //required, however - may not be honored by POS
            "total": 1700,                  //required
            "item_type": "",                //optional, future use
            "variation_id": "",             //optional, future use
            "line_options": [                 //=== line options (modifiers) ===
              {                               //optional, if none, return empty array []
                "id": "[modPOSID]",           //required
                "name": "Name of Mod",        //required
                "price": 0,                   //required
                "line_sub_options": []        //optional, future use, send empty array []
              },
              {
                "id": "4053",
                "name": "Pepper Jack",
                "price": 0,
                "line_sub_options": []
              }
            ]
          }
        ]
      }
    ],
    "coupons": [] //optional: future use
  }
}
``
