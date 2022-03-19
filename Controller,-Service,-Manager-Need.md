This is just my preference:

Data Access Classes are responsible for each table
Managers are responsible for low level business logics and consistency between a few data tables. They use DAO for performing their duties.
Services provide higher level business services which needs collaboration between managers (manager of managers).
The services should be quite independent and granular which master a set of data and a business domain in the system.
A service should be mature enought so that it can be (and not necessarily will be) exposed over WebApi/WebService etc. as an independent service in the organization.
Services has a well defined interface and they can be injected to other objects for performing and e2e business case.
Services should not have many depenency to other services and they interact to none or just very few of other services for performing a e2e business case.
  	

 -Controllers-
My goal was to have each controller only know about it's respective service, and how to return the information from that service (which is then formatted by one of the two views)

-Services-
Services then bring together the functions of multiple managers to accomplish a full task such as authenticating a user or uploading a parcel.

-Managers-
Managers are directly related to their respective models, and do all of the business logic surrounding those models. They do not bring that logic together, though.