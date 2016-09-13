#Search Criteria

A search request can include the following search criteria:

category_group

The desired 3taps category grouping code. Note that this parameter can include logical operators, as described below.

category

The desired 3taps category code. Note that this parameter can include logical operators, as described below.

location.country

The desired 3taps country code, or "*" to search for all postings which have a country value. Note that this parameter can include logical operators, as described below.

location.state

The desired 3taps state, or "*" to search for all postings which have a state value. Note that this parameter can include logical operators, as described below.

location.metro

The desired 3taps metro area code, or "*" to search for all postings which have a metro value. Note that this parameter can include logical operators, as described below.

location.region

The desired 3taps region code, or "*" to search for all postings which have a metro value. Note that this parameter can include logical operators, as described below.

location.county

The desired 3taps county code, or "*" to search for all postings which have a metro value. Note that this parameter can include logical operators, as described below.

location.city

The desired 3taps city code, or "*" to search for all postings which have a metro value. Note that this parameter can include logical operators, as described below.

location.locality

The desired 3taps locality code, or "*" to search for all postings which have a metro value. Note that this parameter can include logical operators, as described below.

location.zipcode

The desired 3taps ZIP code, or "*" to search for all postings which have a metro value. Note that this parameter can include logical operators, as described below.

radius

The desired radius for a radius-based search. This should be a string consisting of a number and a suffix, like this:

radius=10.2mi

The number can be any whole or floating point value, and the following suffixes are currently supported:

ft = feet. 
m = meters. 
mi = miles. 
km = kilometers.

There is no default value for the units. If a suffix is not supplied, the search request will be rejected and an error returned back to the caller; this is to prevent confusion where, for example, the user assumes the radius is in miles but it is actually in metres, and surprising results are returned.

Note that if the radius parameter is supplied, the lat and long parameters must also be supplied.

lat

The desired latitude for a radius-based search, in decimal degrees. Note that this parameter can also be used for distance-based sorting, as described below.

long

The desired longitude for a radius-based search, in decimal degrees. Note that this parameter can also be used for distance-based sorting, as described below.

source

The desired 3taps source code. Note that this parameter can include logical operators, as described below.

external_id

The desired external ID for a posting. Note that external ID values are guaranteed to be unique for a single data source, but the same value may be used across sources. For this reason, you would normally search for both the source and the external ID at the same time. Note that this parameter can include logical operators, as described below.

heading

A freeform text string. Only postings with the given string in their heading will be included in the search results. Note that this parameter can make use of text operators, as described below.

body

A freeform text string. Only postings with the given string in their body will be included in the search results. Note that this parameter can make use of text operators, as described below.

text

A freeform text string. Only postings with the given string in their heading or body will be included in the search results. Note that this parameter can make use of text operators, as described below.

timestamp

This parameter is used to only include postings with a given range of timestamp values. The timestamp parameter can either be set to the special value all to match all postings, or alternatively you can use one of the following three formats to specify a desired date/time range:

MIN_TIMESTAMP..MAX_TIMESTAMP   
MIN_TIMESTAMP..   
..MAX_TIMESTAMP
MIN_TIMESTAMP and MAX_TIMESTAMP represent the minimum and maximum timestamp values, respectively. If both are supplied, then only postings within the given range of timestamp values will be included in the search results. If only a minimum timestamp is supplied, only postings later than that timestamp will be included. Similarly, if only a maximum timestamp is supplied, only postings earlier than that timestamp will be included.

Timestamp value can be represented in one of the following ways:

1364387696

An integer value represents a "unix time" value -- that is, the number of seconds since the 1st of January, 1970, in UTC.

2013-03-27 12:34:56

A string containing hyphens or colons are interpreted as a date/time value, in UTC. The following formats are accepted:

YYYY-MM-DD
YYYY-MM-DD HH:MM
YYYY-MM-DD HH:MM:SS

7d
30m

A string consisting of a number following by a single letter represents a relative time value. The timestamp is calculated relative to the current date and time. For example, if the current date and time is 2013-03-28 12:06:30, and the relative time value is 30m, then the timestamp will be calculated as 30 minutes ago -- ie, 2013-03-28 11:36:30.

The following relative timestamp codes are currently supported:

s = seconds. 
m = minutes. 
h = hours. 
d = days. 
w = weeks.

id

This parameter can be used to search for a single posting with a single record ID, or a number of postings within a given range of record IDs. To search against a single record ID, the value should simply be the integer record ID, like this:

?id=1234567
Alternatively, to search against a range of record IDs, the parameter should look like this:

?id=1234567..1234890
price

This parameter is used to only include postings with a given range of price values. The parameter's value should be a string formatted in one of the following ways:

MIN_PRICE..MAX_PRICE
MIN_PRICE..
..MAX_PRICE
*
MIN_PRICE and MAX_PRICE represent the minimum and maximum price values. If both are supplied, then only postings with the given range of price values will be included in the search results. If only a minimum price is supplied, only postings greater than or equal to that minimum price will be included. Similarly, if only a maximum price is supplied, only postings less than or equal to that maximum price will be included.

If the price criteria is set to *, the search will match all postings which have a price.

Note that price values can be given as either integer or floating-point values.

currency

Only include postings in the given currency. The parameter's value should be a 3-character ISO-4217 currency code.

annotations

A specially-formatted string identifying one or more annotation values. Only postings which match the given annotation value(s) will be included in the search results.

The value of this parameter should consist of one or more key:value pairs separated by either AND or OR, and the whole string surrounded by { and } characters. For example:

annotations={make:ford AND model:mustang}
Note that the value can be set to "*", which means that all postings will be found that have the given annotation regardless of its value. For example, the following search criteria:

annotations={size:large AND color:*}
will find all postings which have their size annotation set to large, and which have a color. Note that if you combine multiple annotation comparisons, you can use parentheses to control the order in which they are evaluated. For example:

annotations={(bedrooms:2br OR bedrooms:3br) AND dogs:yes}
status

Only include postings with the given status value. The following status values are currently supported:

registered   
for_sale   
for_hire      
for_rent  
wanted   
lost   
stolen   
found
Note that this parameter can include logical operators, as described below.

state

The state the posting is in. This will be one of the following values:

available   
unavailable   
expired
Note that this parameter can include logical operators, as described below.

has_image

If this parameter is supplied and has the value "1", only postings which have an image will be included in the search results. If this parameter has the value "0", only postings which do not have images will be included in the search results.

has_price

If this parameter is supplied and has the value "1", only postings which have a price value will be included in the search results. If this parameter has the value "0", only postings which do not have a price value will be included in the search results.

include_deleted

By default, deleted postings will not be included in the search results. If this parameter is supplied and has the value "1", however, deleted postings will be included in the search results.

only_deleted

If this parameter is supplied and has the value "1", only deleted postings will be included in the search results.