M-Lab Observatory Manifest Specification Guidelines
====================
Version: 0.0 (2014-09-29)

Requirements
---------------------

*Things that should be conveyed*

* What Measurement Lab sites have been available, and when they became available.
* What ISPs are available and when they became available or unavailable.
* What metrics Measurement Lab has data for, and when did we start collecting the data.
* What transit provider the Measurement Lab site sits behind.
* What events could cause inconsistent or missing data.
** Where is there gaps in data due to downtime? 

Draft Spec
---------------------
```
 {
   "file_format_version": 1,
   "generated_on": UnixTimestamp/UTCTimestamp,
   "latest_data_available": UnixTimestamp/UTCTimestamp,
   "sites": [
      {
         "name": String(city, state),
         "country": String(ISO 3166 two-letter),
         "shortcode": String(airport code),
         "transit_provider": String,
         "start_date": UnixTimestamp/UTCTimestamp/null,
         "end_date": UnixTimestamp/UTCTimestamp/null,
         "maintenance": [
            {
               "type": String("downtime", "rename", ...),
               "start_time": UnixTimestamp/UTCTimestamp,
               "end_time": UnixTimestamp/UTCTimestamp/null,
               "affected_tests": String("all", [metric:name])
            },
            ...
         ]
      },
      ...
   ],
   "client_providers":[
      {
         "name": String,
         "shortcode": String,
         "start_date": UnixTimestamp/UTCTimestamp/null (null implies since start of Measurement Lab data),
         "end_date": UnixTimestamp/UTCTimestamp/null
      },
      ...
   ],
   "transit_providers":[
      {
         "name": String,
         "shortcode": String,
      },
      ...
   ],
   "metrics":[
      {
         "name": String,
         "shortcode": String,
      },
      ...
   ],
 }
```
