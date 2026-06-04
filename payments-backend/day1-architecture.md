
### QUIZ
### Payment FLOW QUIZ - Day 1

### Why Daraja calls your server and not the other way around
The STK push flow is initiated by your server, but the actual 
payment happens on the customer's phone Safaricom controls 
that process. Your server has no way of knowing when the customer 
enters their PIN or whether the transaction succeeded. Instead of 
your server repeatedly polling Safaricom (which would be slow and 
inefficient), Safaricom calls your callback URL the moment the 
transaction is complete. 

### Why you need ngrok for the callback
Safaricom's servers are on the public internet and can only send 
HTTP requests to publicly accessible URLs. Your local development 
server  is only visible on your own machine  
Safaricom cannot reach it. ngrok solves this by creating a secure 
public tunnel to your localhost, giving it a real HTTPS URL that 
Safaricom can call.

### What would happen if you lost the callback
If the callback is lost or your server is unreachable when 
Safaricom sends it, your server never receives confirmation that 
the payment succeeded. The customer's M-Pesa account would be 
debited, but your database would have no record of it. This means 
the customer paid but your system shows no payment leading to 
disputes, broken order flows, and a poor user experience. This is 
why callback reliability is critical in payment systems.


## TASK 5-Payment Flow 

### Business Owner Creates a Payment Link
The business owner fills in the customer's details on the React 
frontend and clicks "Create Link". The request is sent to the 
Express backend, which passes through CORS and JSON middleware 
before reaching the payments route. The server creates the payment 
link, stores the details in the database with a status of 
"pending", and returns a 201 response confirming the link was 
created.
