# Highlevel Overview
Take in a customer Id, channel, max number of offers. Return a list of available offers for the customer in descending order of their score.

### :page_facing_up: Supporting Files 
- *Customers.csv* - List of customers and their attributes
- *Tranactions.csv* - Transactions to run with the given customer Id, channel and offers.
- *Offers.json* - List of available offers, their properties, and a description of the rules that should be created with them.

### :1234: Detailed Process Steps
1. Line from Transactions.csv is fed into service with Customer Id, Channel and the Max Number of Offers
2. Full customer profile is pulled in based on ID
3. Offers are evaluated for eligibility by rules. Offer metadata: cost, eligibleStates, assigned channel(s), start, and end dates should also be considered in addition to their rules.
4. The the eligible offers are each scored by a SQL `SELECT RAND();` then put in descending order
5. The full list of offers is written to a log table including: Customer Id, Channel, Max Offers Requested, Date
6. Output is the maxinum number of requested offers in order
