.. _rest_encoding:

JSON and XML Encoding Details
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

    **XML:** Encoded as the text ``true`` or ``false``

    Examples:

    .. code:: xml

       <field>true</field>

    .. code:: xml

       <field>false</field>
*String*
    **JSON:** A string which may have particular formatting requirements detailed in the description of the field, such as an enumeration of accepted values.

    Example:

    .. code:: javascript

       { "field": "foo bar" }

    **XML:** A text fragment which may have particular formatting requirements detailed in the description of the field, such as an enumeration of accepted values.

    Example:

    .. code:: xml

       <field>foo bar</field>
*Date*
    **JSON:** A string that represents a date, formatted as ``yyyy-mm-dd``.

    Example:

    .. code:: javascript

       { "field": "2014-06-13" }

    **XML:** A text fragment that represents a date, formatted as ``yyyy-mm-dd``.

    .. code:: xml

       <field>2014-06-13</field>
*DateTime*
    **JSON:** A string that represents a date and time, preferably formatted using ISO8601 format. Also can be formatted ``yyyy-mm-dd hh:mm:ss [+-zzzz]``

    .. probably need more description

    Example:

    .. code:: javascript

       { "field": "2014-06-13T23:01:50.481-0400" }

    **XML:** A text fragment that represents a date and time, preferably formatted using ISO8601 format. Also can be formatted ``yyyy-mm-dd hh:mm:ss [+-zzzz]``

    Example:

    .. code:: xml

       <field>2014-06-13T23:01:50.481-0400</field>
*Decimal*
    **JSON:** A string that represents a decimal number, formatted as ``[+-]mmmm[.nn]``: an optional sign indicator followed by sequence of digits and then optional decimal point and fractional part. Represented as a string instead of JSON native number due to some libraries using an imprecise floating-point type to represent this value, which would be inappropriate for currency values.

    Examples:

    .. code:: javascript

       { "field": "145.92" }

    .. code:: javascript

       { "field": "-45" }

    **XML:** A text fragment that represents a decimal number, formatted as ``[+-]mmmm[.nn]``: an optional sign indicator followed by sequence of digits and then optional decimal point and fractional part.

    Examples:

    .. code:: xml

       <field>145.92</field>

    .. code:: xml

       <field>-45</field>
*Integer* or *Long*
    **JSON:** A 32-bit (Integer) or 64-bit (Long) integral value, in normal JSON format, e.g. ``1234`` or ``-810``

    Example:

    .. code:: javascript

       { "field": 145 }
       { "field": -45 }

    **XML:** A text fragment representing a 32-bit (Integer) or 64-bit (Long) integral quantity formatted in the usual way, e.g. ``1234`` or ``-810``

    Example:

    .. code:: xml

       <field>145</field>
       <field>-45</field>
*Object*
    **JSON:** As a JSON object. The particular fields expected are detailed in the description.

    Example:

    .. code:: javascript

       "obj": {
           "field1": "foo",
           "field2": 1234,
           â€¦
       }

    **XML:** As an element with a subelement for each expected field, detailed in the description.

    Example:

    .. code:: xml

       <obj>
           <field1>foo</field1>
           <field2>1234</field2>
           â€¦
       </obj>
*List[â€¦]*
    **JSON:** As a JSON list with each element encoded according to the contained type.

    *List[Int]* example:

    .. code:: javascript

       "lstInt": [
           "foo",
           "bar",
           â€¦
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

    **XML:** As a ``<array>`` element with ``<item>`` subelements, each ``<item>`` element containing one value encoded according to the contained type.

    *List[Int]* example:

    .. code:: xml

       <lstInt><array>
           <item>foo</item>
           <item>bar</item>
           â€¦
       </array></lstInt>

    *List[Object]* example:

    .. code:: xml

       <lstObj><array>
           <item><a>1</a><b>true</b></item>
           <item><a>2</a><b>false</b></item>
           â€¦
       </array></lstObj>

    Empty list example:

    .. code:: xml

       <lstObj><array /></lstObj>
*Map[â€¦]*
    **JSON:** As a JSON object with each field value encoded according to the contained type.

    *Map[Int]* example:

    .. code:: javascript

       "mapInt": {
           "foo": 1,
           "bar": 2,
           â€¦
       }

    *Map[Object]* example:

    .. code:: javascript

       "mapObj": {
           "foo": { "a": 1, "b": true },
           "bar": { "a": 2, "b": false },
           â€¦
       }

    Empty map example:

    .. code:: javascript

       "mapObj": {}

    **XML:** As an element for each key with the contents of the element encoded according to the contained type.

    .. note::

       Empty maps are represented specially in XML using the
       special element ``<empty />``. See example below.

    *Map[Int]* example:

    .. code:: xml

       <mapInt>
           <foo>1</foo>
           <bar>2</bar>
           â€¦
       </mapInt>

    *Map[Object]* example:

    .. code:: xml

       <mapObj>
           <foo><a>1</a><b>true</b></foo>
           <bar><a>2</a><b>false</b></bar>
           â€¦
       </mapObj>

    Empty map example:

    .. code:: xml

       <mapObj><empty /></mapObj>

Optional and Required Fields
----------------------------

Fields marked *(required)* in the documentation of a request endpoint must be given when submitting requests, and fields marked *(required)* in the documentation of a reply will always be given by the Paytronix system.

Similarly, fields marked *(optional)* may be omitted entirely from the request and may or may not be provided by the Paytronix system in replies. For replies, the description of a field will often explain when the field will be given. Note that in JSON an optional field may be given with the value ``null`` rather than omitted entirely, but this should be avoided if possible.
