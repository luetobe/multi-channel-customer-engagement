# Using the solution

## Example 1 - Interact with the bot and simulate clickstreaming

1. Go to CloudFormation -> outputs, you should see 2 URLs: AgentDomainName	and CustomerDomainName

2. Open the CustomerDomainName's Url and sign up with a valid email. It will open the customer portal

3. Let's emulate a few clicks that an user can do on the page, you can click on the following buttons to capture the clickstreams.

![clickstreaming](./images/image%20(2).png)

4. Next, click on "Cloud Bank Bot" and start interacting with the chatbot powered by Amazon Lex. These are some examples of questions: 
 - What is my savings account balance?
 - I need an cash advance
 - how much do I owe in my credit card
 - credit card due date
 - pay balance of my credit card
 - what are the openning hours for the new york branch

    You can also go to Amazon Lex console and check the different intents configured.

    Every interaction is going to request a PIN (except for the questions about the branches openning hours). You can request to send a pin (Just type *send me a pin*), it will send a PIN to the mobile phone configured in the CloudFormation, or you can also check it at the top right of the website.

5. Now let's interact using Amazon Connect. Go and log in into your Amazon Connect Instance. Open the Connect Agent Control Panel - you can click in the phone icon.

![CCP](./images/Pictureccp.png)

    you should see a portal like this

![clickstreaming](./images/image%20(3).png)

    Make sure you are set as Available

![clickstreaming](./images/image%20(4).png)

6. Without closing the CCP - Go back to your CustomerDomainName portal and in the chat type *I would like to speak with an agent* or *talk to an agent* - This should innitiate a new chat incoming in the CCP.

<img src="./images/image%20(5).png" alt="drawing" width="750"/>

7. Accept the chat - now your agent is chatting with the end user in the banking portal.


## Example 2 - Interact using Contact Center powered by Amazon Connect

1. Call the phone number you configure in Lab 1 - Step 3. 

2. when prompted dial 2. FAQ. Now you can ask the same questions than in the previous example 
 - What is my savings account balance?
 - I need an cash advance
 - how much do I owe in my credit card
 - credit card due date
 - pay balance of my credit card
 - what are the openning hours for the new york branch
 
 It will also require PIN for specific account questions - you need to type it.
 
 3. Then choose option #3 - It will redirect your call to an agent, if your agent is set as available, it then will forward the call and it should be ringing.
 
 4. In order to test Call Analytics - Please hold a call where you simulate agent/call between two people.

 
 ## Example 3 - Interact using Alexa

 If you deployed the step - AlexaSkill. Then please interact with Alexa, you can use the developer test console, saying "Alexa, open my cloud bank" or "Alexa, abre banca nube" for spanish, and then ask some of the same questions.

Remember you can say, Alexa, send me a pin and it will send you a PIN to the mobile phone configured in the cloudformation.

 - What is my savings account balance?
 - I need an cash advance
 - how much do I owe in my credit card
 - credit card due date
 - pay balance of my credit card
 - what are the openning hours for the new york branch
 
 
 ## Analyze all Data

Now that we have gather data from different sources (calls recorded, chats using Lex, voice using Alexa and clickstreaming), let's log in the agent portal to have a end to end visualization of the customer's interactions.

1. Go to CloudFormation -> outputs. You should see 2 URLs: AgentDomainName and CustomerDomainName.

2. Open the AgentDomainName's URL and sign in (if register in example #1) or sign up with a valid email. It will open the agent portal.

3. Now, you can see all the voice, bot, and other interaction we just created.

![agents-portal](./images/agentsportal.png)

If you’re done experimenting and want to delete all the resources created to avoid incurring future charges, go to step 6: [Cleaning Up](../06_CleanUp/README.md)


# Example Customer Walktrought

A customer uses their Alexa to find out about their credit card balance

<img src="./images/alexa.png" alt="drawing" width="500"/>

Customer does not understand why USD 1500, so they decide to go to their customer portal and check the transactions and accounts. Customer still does not understand, they decide to use the chat in the customer portal to speak to an agent. When the call or chat session gets routed to the agent, the agent can see all the different interactions that the customer had and their frustration

First, the agent can see all the clickstreaming done by the customer

![agents-portal](./images/example1.png)

Then, it can see the call to the Alexa bot. 

![agents-portal](./images/example2.png)

It may mean that the customer is being struggling to find out why they owe USD 1,500. Therefore, the agent can react proactively

<img src="./images/Picture1.png" alt="drawing" width="800"/>

