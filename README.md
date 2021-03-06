# IoT Alarm System  built for my old grandmother using AWS IoT Button and AWS services

A Easy to use IoT Alarm system using AWS IoT button and some services like Lambda, Connect, Step Functions,etc..

I created this to help my Grandmother. My grandma is 88-years old with reduced mobility. She lives alone in a small village without a caretaker and does not really use mobile phones. If she falls, then she is in danger as she will not be able to get back up, same if something goes wrong while sleeping. However, with an AWS IoT button she can call for help by simply pressing the button and potentially save her life. 

Since her village provides free Wi-Fi coverage, I built an emergency alert system using AWS. After clicking the AWS IoT button, a series of events will take place to get her the assistance she needs. This is a simple approach to help her in difficult situations and one others can take as well. 

![alt text](https://github.com/DanGOTO100/IoTAlarmsystem/blob/master/grandmaemergency.png) 


Basically:

Once someone clicks the AWS IoT button, an ”alarm” state is set and actions will begin. 
First, we will call the designated phone (my grandma fix phone) and request to press “1” to deactivate the alarm (in case it was  clicked the button by mistake).
If it was not a mistake –  there is not answer or does not press “1”- then something is wrong.  we will call the relatives of the person who clicked the button (me as her relative in this case) or other designated phone to inform them ofthe alarm triggered by the person and the real state of alarm. The process will repeat itself, until alarm is deactivated or a configurable number of times, through AWS Step Functions feeded with the appropriate Lambdas.

The overall architecture for Phase 1 looks like this.

![alt text](https://github.com/DanGOTO100/IoTAlarmsystem/blob/master/grandamarchitecturephase1.png)


Phase 2 is the predictive prescription. The data logged in Amazon DynamoDB from the alarm activation combined with other external data (time of the action, temperature, and moon phase) can be used to train a predictive model. 
Amazon SageMaker helps us to create this model, train it with a few clicks, and set up the endpoint to obtain predictions. 


![alt text](https://github.com/DanGOTO100/IoTAlarmsystem/blob/master/grandamarchitecturephase2.png)

# Dependencies

The dependencies of the code in this repository are to have a DynamoDB table (check AWS documentation for (Amazon DynamoDB)[https://aws.amazon.com/dynamodb/]) and also AWS Step Functions to orchestrate the Lambdas,as specified in the artchitecture (see (AWS Step Functions)[https://aws.amazon.com/step-functions/] documentation).
