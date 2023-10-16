# NoSQL-challenge
Challenge assignment for Mongo

Data for this project was from the provided project files.

Layout for assignment came from starter file.

Specific sections using sources listed below:

--------------------------------------------------
Setup (Part 1)
--------------------------------------------------

Some dependency imports provided in starter file.

The following sections were also provided:

    # Create an instance of MongoClient
    mongo = MongoClient(port=27017)

    # assign the uk_food database to a variable name
    db = mongo['uk_food']

    # assign the collection to a variable
    establishments = db['establishments']

Bigyan from AskBCS helped with the importing of the database via the command line as my mongoimport was not set up properly:

    mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishmens.json

--------------------------------------------------
Update the Database (Part 2)
--------------------------------------------------    

The following section was provided in the instructions:
    {
        "BusinessName":"Penang Flavours",
        "BusinessType":"Restaurant/Cafe/Canteen",
        "BusinessTypeID":"",
        "AddressLine1":"Penang Flavours",
        "AddressLine2":"146A Plumstead Rd",
        "AddressLine3":"London",
        "AddressLine4":"",
        "PostCode":"SE18 7DY",
        "Phone":"",
        "LocalAuthorityCode":"511",
        "LocalAuthorityName":"Greenwich",
        "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
        "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
        "scores":{
            "Hygiene":"",
            "Structural":"",
            "ConfidenceInManagement":""
        },
        "SchemeType":"FHRS",
        "geocode":{
            "longitude":"0.08384000",
            "latitude":"51.49014200"
        },
        "RightToReply":"",
        "Distance":4623.9723280747176,
        "NewRatingPending":True
    }

The following section was provided in the starter code:

    # Set non 1-5 Rating Values to Null
    non_ratings = ["AwaitingInspection", "Awaiting Inspection", "AwaitingPublication", "Pass", "Exempt"]
    establishments.update_many({"RatingValue": {"$in": non_ratings}}, [ {'$set':{ "RatingValue" : None}} ])

--------------------------------------------------
Setup (Analysis File)
--------------------------------------------------

Some dependency imports provided in starter file.

The following sections were also provided:

    # Create an instance of MongoClient
    mongo = MongoClient(port=27017)

    # assign the uk_food database to a variable name
    db = mongo['uk_food']

    # assign the collection to a variable
    establishments = db['establishments']

References
UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).
