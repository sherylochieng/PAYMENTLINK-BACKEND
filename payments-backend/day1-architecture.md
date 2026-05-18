Task 5: Write the payments architecture in your own words

BIZ  OWNER TO SERVER TO CREATE LINK

We start with initiall process wher biz owner creates payment link for customer
FRONTEND -> CLICKScreate link -> enters customer detais -> server ->(cors + express.json) -> link.route.js(link created) -> database ( stores all data) -> 201 message sent to owner link created 

LINK FROM BIZ OWNER TO CUSTOMER TO SERVER TO SAFARICOM
LINK GENERATED SENT to Customer -> server -> safaricom(authentication and authorization) ->server callback sent to server(request accepted) -> safaricom sends promt to customer -> customer enters pin -> payment sealed -> server (status change to paid) -> frontend immediately sends succeess message to customer as receipt is being generated and sent to the customer and stored to database.




Why Daraja calls your server and not the other way around?

to notify it process began to prevent rate limiting that may make saf server thing my server is malicious
Prevent double payment
Allow server continue other operations as it waits for the customer to finalize payment after putting their pin


Why you need ngrok (or a real server) for the callback??

saf server or third purty servers need to talk to public servers so ngrok convers my local server url into public allowing it talk to safaricom server


What would happen if you lost the callback (hint: the customer would be charged but you would not know)?

may cause fighting btwn customer and owner coz theres no proof of truth ,,but that can be solved by obtaining saf statement.



