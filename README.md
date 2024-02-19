**Use Case Summary**
The contact center use case I created is a sample credit card payment service that can be used by any credit card company. 
The contact center uses a lookup to a DynamoDB table (using AWS lambda) to find the caller's acount by thier ANI.
If the record is not found or if the customer is calling about another acoount they can also give another phone number for the right account.
The input by users is captured using 3 differents lex bots; one to capture PIN code; one to capture phone number; and another general purpose bot used as 'main menu' bot.
The menu for this contact center offers callers the option to hear their remaining balance or to make a payment.
The lambda function mentioned earlier, also executes the pay bill option a customer selects to modify the account they're calling about in the DynamoDB table.

**FILES**
This repository is composed of some of the main files I used to run my contact center in Amazon Connect for this assessment.
This includes the 3 lex bots I used: 
* GeneralBot
    * used as a yes/no bot and main menu bot for the following 2 intents: check balance and make a payment
* PinCaptureBot
* PhoneNumberCaptureBot

dynamoDB table that holds the customers' information using their phone number as the primary key
* Sample DynamoDB records.csv
    * the records for the sample users I used to test the sample contact center.

The multi-purpose lambda function I used
* GetCustomerInfo
    * returns the customer information based on the callers ANI
    * returns the customer information based on the caller's input phone number
    * executes the make a payment option to calculate and update customers' "account" in the DynamoDB table.
