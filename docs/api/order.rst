.. _rest_encoding:

Order Service
-------------

Use this service to submit, update, void orders.

.. note::

   For POS integrated orders: Update and Void action can only be performed before the order is submitted into the restaurant's POS system; and only sites that are configured will accept these actions.

   We recommend a daily sync of sites and menus to keep their pricing current.

GET ``/api/order``
~~~~~~~~~~~~~~~~~~

   * id: string, id of the order
   * posType: string, type of POS system, leave blank for HTML render of the order
   
POST ``/api/order/calculate``
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::

   * charges fees, tax, tip, will be added on reutrn; however, tip should be updated by submit method
   * diner_grand_total, grand_total will be updated
   
Order Body Example:

.. code:: javascript 
   
   {
     "uuid": "",
     "status": "",
     "merchant_id": "d48c30e0-3c52-450f-b068-fcd8bcb47d7f",
     "fulfillment_info": {
       "delivery_info": {
         "address": {
           "address_line1": "line1",
           "address_line2": "line2",
           "city": "city",
           "state": "st",
           "country": "US",
           "zip_code": "12345"
         },
         "is_managed_delivery": false,
         "estimated_delivery_time": "2016-11-30T20:25:00.000Z",
         "instruction": "",
         "contact_info": {
           "phone": "(111) 222-1234",
           "name": "First Last"
         }
       },
       "pickup_info": {
         "contact_info": {
           "phone": "(111) 222-1234",
           "name": "First Last"
         }
       }
     },
     "time_placed": "2016-11-30T19:58:15.511Z",
     "when_for": "2016-11-30T20:28:15.146Z",
     "charges": {
       "line_groups": [
         {
           "label": "",
           "lines": [
             {
               "id": "112233",
               "name": "Name of item",
               "description": "",
               "special_instructions": "",
               "price": 850,
               "quantity": 2,
               "diner_total": 1700,
               "total": 1700,
               "item_type": "",
               "variation_id": "",
               "line_options": [
                 {
                   "id": "111",
                   "name": "Name of Mod",
                   "price": 0,
                   "line_sub_options": []
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
       "coupons": []
     }
   }


  

POST ``/api/order/submit``
~~~~~~~~~~~~~~~~~~~~~~~~~~

URL Parameter:

   * calc: boolean (true/false)
      true: perform calculation, overwrite supplied prices and line totals
      false: use the supplied price and line totals without price look up, performs no intneral calculation

Order Body Example:

.. code:: javascript

   {
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
           "payment_type": "CASH",         //required, type: CASH, CREDIT, OTHER
           "payment_name": "Visa",         //optional, name: Visa, MasterCard, AMEX, Discover, [PaymentName]
           "payment_ref": "",              //optional, payment reference/notes
           "amount": 2173                  //required, amount of this payment type
         }
       ],
       "total": 2173,                      //required, total paid (to be paid)
       "adjusted_total": 2173              //required
     },
     "charges": {                          //=== chargess ===
       "fees": {                           //optional: fee will be returned if there's delivery fee
         "total": 100
       },
       "taxes": {                          //required if calc == false
         "total": 90
       },
       "tip": {                            //required if has tip, other fill 0
         "amount": 283
       },
       "diner_grand_total": 2173,          //required if calc == false, the extended total
       "grand_total": 2173,                //required if calc == false, the order total
       "line_groups": [                    //=== line groups ===
         {                                 //one linegroup per order; group order: one/each person 
           "label": "",                    //optional, for group order, name of person
           "lines": [                          //=== lines ===
             {                                 //one line object per item
               "id": "[itemPOSID]",            //required, the POSID
               "name": "Name of item",         //required
               "description": "",              //optional 
               "special_instructions": "",     //optional
               "price": 850,                   //required, if set to -99 => forces price look up
               "quantity": 2,                  //required, must be positive number > 0
               "diner_total": 1700,            //required, if price set to -99, this is overwritten (may not be honored by POS)
               "total": 1700,                  //required, if price set to -99, this is overwritten
               "item_type": "",                //optional, future use
               "variation_id": "",             //optional, future use
               "line_options": [                 //=== line options (modifiers) ===
                 {                               //optional, if none, send empty array []
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

The following segment will be appended to top of order on reply:

.. code:: javascript

   {
     "uuid": "[orderGUID]",
     "status": "[status]",
     "statusHistory": [
       {
         "status": "PENDING",
         "timestamp": "2016-11-30T20:01:45.107Z",
         "update_source": "",
         "reason": "Order received"
       }
     ],
     ... [the order body]
    }

