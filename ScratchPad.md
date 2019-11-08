Interview preparation:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>> 


Checkpoints:

You need to check whether you got the correct response or not (page)


Let’s say i want to put a text check before a login transaction. And you know once you send the log in transaction to the server from the server you get a response like:
Welcome to the web tours page and there might be some other information like which will be there on the page. This is a right response time and this i what you are supposed to get. 

But you might get another response aswell.404, page not found or some other response. This is a negative response. So you want to check if you get a right response or not. 

VUGEN ITSELF DOES NOT DISTINGUISH THIS RESPONSE OR THE OTHER RESPONSE. RIGHT OR WRONG.
aS LONG AS IT GETS RESPONSE ITS FINE.BUT IT DOES NOT DISTINGUISH WHETHER IT GOT THE RIGHT RESPONSE OR NOT. VUGEN DOES NOT HAVE THE CAPABILITY TO DISTINGUISH WHICH ONE IS RIGHT AND WHICH ONE IS WRONG RESPONSE. 
SO TO EMPOWER THE VUGEN YOU ADD A CHECK POINT.
with a text "Welcome".now you have given a vugen extra power. now as soon as you got the response it will start to search for the text welcome in that response. If it is there then it will mark the transaction as Pass. And if it is not there then it will mark the transaction as failed. 
So you are empowering the vugen to mark which one is correct response and which one is an incorrect response. 
This is the significance of check points. 

ALWAYS REMEMBER THE TEXT CHECK GOES BEFORE THE REQUEST AND NOT AFTER THE REQUEST.

Function:
```
// Set up check for successful login by looking for "Welcome"

web_reg_find

web_reg_find("Text=Welcome",
        "SaveCount=Welcome_Count",
        LAST );

// Check result
    if (atoi(lr_eval_string("{Welcome_Count}")) > 0){
        lr_output_message("Log on successful.");
        }
     else{
          lr_error_message("Log on failed");
          return(0);
     }

```



# Performance Terminology

Credit: https://www.microfocus.com/media/documentation/loadrunner_and_performance_center_document.pdf

Quantitative aspects of performance testing are gathered during the monitoring phase. Let’stake
a closer look at main terms used in performance monitoring.

Two of the most important measures of system behavior are bandwidth and throughput.

**Bandwidth** is a measure of quantity, which isthe rate at which work can be completed, whereas
throughput measuresthe actualrate at which work requests are completed.

**Throughput** can vary depending on the number of users applied to the system under test. It is
usually measured in terms of requests persecond. In some systems, throughput may go down
when there are many concurrent users, while in othersystems, it remains constant under pressure
but latency beginsto suffer, usually due to queuing. How busy the variousresources of a
computersystem get is known astheir **utilization.**

The key measures of the time it takesto perform specific tasks are queue time, service time, and
response time.

Service Time and Queue Time
Service time measures how long it takesto process a specific customer work request.
When a work request arrives at a busy resource and cannot be serviced immediately, the request is
queued. Requests are subject to a queue time delay once they begin to wait in a queue before
being serviced.
Response Time
Response time isthe most important metric and will be used consistently throughout the book to
refer to the sum of service time and queue time. It can be divided into response time at the server
or client asfollows:
l Latency measured at the server. Thisisthe time taken by the server to complete the execution
of a request. This does not take into account the client-to-server latency, which includes
additional time for the request and response to crossthe network.
l Latency measured at the client. The latency measured at the client includesthe request queue,
the time taken by the server to complete the execution of the request, and the network latency.
Deep application usage understanding isrequired in order to build proper mix of activities and
their popularity among the users.


# Performance Testing Calculator

PerfTractor: Performance Testing Tool Prices and Calculators

Little's Law Calculator : calculate the

Number of Vusers

Pacing Time (seconds)

Total Test Data required

Total Virtual Users that can run on that Load Generator

Demo Links: Lists of sample web applications which will helpful to learn performance testing tool concepts


# Possible LoadRunner Questions.

What kind of scripting challenges you have faced in your project?

What kind of challenges you have faced in controller?

Can we have multiple LG’s?

How do you decide the number of LG’s required for your project?

How did you do error handling in your project?

Difference Between web_reg_save_param_ex and web_reg_save_param?

Stacy has received the Transactional Volumes and number of concurrent users as part of NFR for the Peak hour. She is expected to test the system, if it can handle the load at the peak hour and also make sure SLA’s are met. Which test is she supposed to do?
She has to execute Load Test. In some organizations, it’s also called as peak load test.
Note: Load test is done for the peak hour. Idea is, If SUT can handle load at peak hour, then it can handle load at any hour.

Did you face any scripting challenges related to security?
What is the difference between Baseline Testing and Benchmark Testing?
Baseline testing:
Let’s say, you have execute a load test for your first release. You record all your response times for this test in your test report. In the second release, again you rerun the same test as there are some changes to your application. <Changes could be either software or hardware in nature>. Results from your second test will be compared to the first test and this kind of testing is baseline testing.
 
BenchMark Testing:
Before you start your test (Lets Say Load test), NFR will be collected from the client. Client usually shared the expected Response time for the application. In some organizations, we call this “Expected response Times” as SLA’s. As a performance tester, you are suppose to compare your results with the SLA’s provided by the client. This is called BenchMark testing.
 
Ideally, Baseline results should not exceed benchmark results.
 
Let’s consider this example…
Assume that there are some standards for completing the marathon. Let’s say that it needs to be done in 5:00 Hrs. Now this is the benchmark. Let’s say, you starting your marathon and completed in 4:30 mins. Now this become baseline for your next marathon.


For a script, if the run-time settings are changed in the controller, will it change in the Vugen?

No. It will not change. Run time settings for a script will remain unchanged, if changed from controller. Changed / Updated run time settings are applicable only for that Test Scenario.


When will the Vuser reach “Pass / Fail” status in controller?

Once the test is done, the users usually reach “Stopped” status irrespective of whether transactions have passed or failed. Users move from “Run” Status to –> “Gradual Exiting” Status –> “Exiting” status to finally —>”Stopped” status.
Rarely, we see users reach “pass / Fail ” Status. This will happen when you use “lr_exit” function in Vuser Script.
Refer to below screensho


How do you capture response times of each element associated with the page?

Capture / Record your script in the URL mode. Identify all the HTTP resources / elements related to a particular transaction. Use lr_start_sub_transaction and lr_end_sub_transaction appropriately as shown below to capture the response times of each element.


What is the Wasted time in the transaction response time and does your response time captured include this wasted time?


A) Well, the “Wasted time” will distinguish between the actual time taken for processing the request and time wasted for doing other activities like displaying information.
For the web scripts, time taken to execute web_reg_find and web_reg_save_param and for these functions to find the text in the response buffer will be considered as wasted time.
In Vugen, this wasted time is part of response time. But, however, in controller this time is not considered in the response time.


How will Cache impact response times?

Cache may impact response times. For the Page Element / Resource for which it is cached in, request will not go the server to fetch it and hence there will not be any response. Hence the transaction for which this component / resource belongs, response times may be lesser than the actual ones. Moreover, there will not be any load created by this cached in elements.


What is the difference between lr_error_message and lr_debug _message?

1. The lr_debug_message sends a debugging message to the console window of Load Runner Controller

2. The lr_error_message sends an error message to the console window of Load Runner Controller

3. lr_error_message occurs when there is an error in the code of the application. On the other hand lr_debug _message occurs when there is a flaw in the functionality of the program. lr_error_message throws an error message in LoadRunner while lr_debug _message throws a debug message in Load runner


What is the significance of Vuser_init Action?

Everything that needs to be initialized is placed here in this action. As shown below, vugen will load run-time settings, Run Mode, User Agent etc..
 

Where do you set ‘HTTP request connect timeout’?

In Runtime Settings –> Internet Protocol –> Options –> HTTP-Request Connect Timeout

# Resourses

https://admhelp.microfocus.com/lr/en/12.56-12.57/help/WebHelp/Content/Tutorial/Analysis.htm

