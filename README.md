# BUDT-703 Database Management Systems

## Brand name:

Dream Living

## Business processes/transactions:

Dream Living will show ratings for apartment complexes around College Park, MD. Users will be able to see reviews for specific apartments along with their related management companies. They will be able to see reviews from multiple different sources such as Google, apartmentratings.com, etc. Apartments are managed by one company. There are reviewers who will write reviews either on a specific apartment on each review source. Also, the review platform collects information about apartments.


## Mission statement

To analyze reviews for apartment complexes around University of Maryland, College Park. To build insights on the ratings of apartment complexes and which ones may be the best for students to choose from for their living needs.

## Mission Objectives for the client

•	To display AVERAGE ratings of the Apartments across multiple review platforms

•	To display Review Platform wise data for certain apartments

•	To display which Review platform has the most/least review count

•	To find which cities have the highest/lowest rated Apartments

•	To find which Management Company replies the fastest/slowest on the reviews


## Design of The Database:


### 1.	Entities:

•	Entity 1: ManagementCompany

•	Entity 2: Apartment

•	Entity 3: Reviewer

•	Entity 4: ReviewPlatform


### 2.	ER schema:
#### Entities, Attributes and Primary Keys:

ManagementCompany (**mgtId**, mgtName, mgtAddress, -mgtStreet, -mgtCity, -mgtState,
-mgtZipCode, mgtPhoneNumber)

Apartment (**aptId**, aptName, aptAddress, -aptStreet, -aptCity, -aptState, -aptZipCode, aptPhoneNumber)

Reviewer (**rvwId**, rvwAccountName) 

ReviewPlatform(pltId, pltName)

#### Relationships, Attributes, Degrees, Participating Entities and Constraints


Manage: Binary

    o	1 ManagementCompany to 1 or more Apartments

    o	1 Apartment to 1 ManagementCompany 

Review: Ternary

    o	1 Reviewer and 1 ReviewPlatform to 0 or more Apartment

    o	1 Apartment and 1 Reviewer to 0 or more ReviewPlatform

    o	1 Apartment and 1 ReviewPlatform to 0 or more Reviewer
    
### 3. ER diagram

<p align = "center">

<img width="468" alt="image" src="https://user-images.githubusercontent.com/99423162/191620419-7dcb8e7f-fc17-4679-8d17-da8df280147b.png">

</p>


### 4.	Relations:
  ManagementCompany (mgtId, mgtName, mgtStreet, mgtCity, mgtState, mgtZipCode, mgtPhoneNumber)
  
  Apartment (aptId, aptName, aptStreet, aptCity, aptState, aptZipCode, aptPhoneNumber,
  mgtId)
  
  Reviewer (rvwId, rvwAccountName) ReviewPlatform (pltId, pltName)
  
  Review (revId, aptId, pltId, rvwId, revStarRating, revDate, revDescription, revReply, revReplyDate)

### 5.	Functional dependency:
  mgtId → mgtName, mgtStreet, mgtCity, mgtState, mgtZipCode, mgtPhoneNumber aptId → aptName, aptStreet, aptCity, aptState, aptZipCode, aptPhoneNumber, mgtId rvwId → rvwAccountName
  
  pltId → pltName
  
  revId → aptId, pltId, rvwId, revStarRating, revDate, revDescription, revReply, revReplyDate

### 6.	Business rules:

  [R1] When Apartment information is deleted from the database, there is no change in Management Company information.

  [R2] If the Apartment information is updated, the Management Company information is updated accordingly.

  [R3] If the Review is deleted from the database, there is no change in the Apartment information.

  [R4] If the Review is updated, the Apartment information should be updated accordingly. 

  [R5] If the Review is deleted from the database, there is no change in the Review Platform
  information.

  [R6] If the Review is updated, the Review Platform information should be updated accordingly.

  [R7] If the Review is deleted from the database, there is no change in the Reviewer information.

  [R8] If the Review is updated, the Reviewer information should be updated accordingly.


### 7.	Referential integrity:

<p align = "center">

<img width="468" alt="image" src="https://user-images.githubusercontent.com/99423162/191621085-0aa83f04-3cd0-4038-bdd6-d7c0d0ac1490.png">

</p>


### 8.	Sample Data for every relation:
ManagementCompany (SM1, Southern Management, 1950 Old Gallows Road,Vienna,Virginia, 22182, 7039022000)
Apartment (GH, Graduate Hills, TulaneDrive, Hyattsville, Maryland,20783, 2406811064,
SM1)

Reviewer (RVW1, ANONYMOUS)

ReviewPlatform (AR, ApartmentRatings, GH)

Review (REV1, GH, AR, RVW1, 1, 7/20/2012, ‘Go to a dumpster in Grad Hills. Pull out a large cardboard box and setup your apartment in the medium of I-495. THIS would be a better option than living in Grad Hills. This place is dangerous, disgusting, and all around bad. The UMD Police had to setup a substation within Grad Hills because the crime is so bad. They should also setup a exterminator substation because this place is crawling with cockroaches. Oh, and utilities are included within the rent. This sounds great at first, when the utilities work or management decides to turn them on.	which is a rarity.’, NULL,
NULL)

