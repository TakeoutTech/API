.. _rest_encoding:

JSON Encoding Details
=============================

This page describes how values are encoded to JSON for use with the Paytornix API. All API calls are documented using JSON however XML can also be used by changing the endpoint URL from ``.json`` to ``.xml`` and providing appropriately formatted XML.

Encoding of Types
-----------------

*Boolean*
    **JSON:** Encoded as a JSON boolean.

    Examples:

    .. code:: javascript

       { "field": true }

    .. code:: javascript

       { "field": false }

*String*
    **JSON:** A string which may have particular formatting requirements detailed in the description of the field, such as an enumeration of accepted values.

    Example:

    .. code:: javascript

       { "field": "foo bar" }

*Date*
    **JSON:** A string that represents a date, formatted as ``yyyy-mm-dd``.

    Example:

    .. code:: javascript

       { "field": "2014-06-13" }

*DateTime*
    **JSON:** A string that represents a date and time, preferably formatted using ISO8601 format. Also can be formatted ``yyyy-mm-dd hh:mm:ss [+-zzzz]``

    .. probably need more description

    Example:

    .. code:: javascript

       { "field": "2014-06-13T23:01:50.481-0400" }

*Decimal*
    **JSON:** A string that represents a decimal number, formatted as ``[+-]mmmm[.nn]``: an optional sign indicator followed by sequence of digits and then optional decimal point and fractional part. Represented as a string instead of JSON native number due to some libraries using an imprecise floating-point type to represent this value, which would be inappropriate for currency values.

    Examples:

    .. code:: javascript

       { "field": "145.92" }

    .. code:: javascript

       { "field": "-45" }

*Integer* or *Long*
    **JSON:** A 32-bit (Integer) or 64-bit (Long) integral value, in normal JSON format, e.g. ``1234`` or ``-810``

    Example:

    .. code:: javascript

       { "field": 145 }
       { "field": -45 }

*Object*
    **JSON:** As a JSON object. The particular fields expected are detailed in the description.

    Example:

    .. code:: javascript

       "obj": {
           "field1": "foo",
           "field2": 1234,
           â€¦
       }

*List[]*
    **JSON:** As a JSON list with each element encoded according to the contained type.

    *List[Int]* example:

    .. code:: javascript

       "lstInt": [
           "foo",
           "bar"
       ]

    *List[Object]* example:

    .. code:: javascript

       "lstObj": [
           { "a": 1, "b": true },
           { "a": 2, "b": false },
           â€¦
       ]

    Empty list example:

    .. code:: javascript

       "lstObj": []

    **JSON:** As a JSON object with each field value encoded according to the contained type.

    *Map[Int]* example:

    .. code:: javascript

       "mapInt": {
           "foo": 1,
           "bar": 2
       }

    *Map[Object]* example:

    .. code:: javascript

       "mapObj": {
           "foo": { "a": 1, "b": true },
           "bar": { "a": 2, "b": false }
       }

    Empty map example:

    .. code:: javascript

       "mapObj": {}


Optional and Required Fields
----------------------------

Fields marked *(required)* in the documentation of a request endpoint must be given when submitting requests, and fields marked *(required)* in the documentation of a reply will always be returned.

Similarly, fields marked *(optional)* may be omitted entirely from the request and may or may not be provided in replies. For replies, the description of a field will often explain when the field will be given. Note that in JSON an optional field may be given with the value ``null`` rather than omitted entirely, but this should be avoided if possible.
