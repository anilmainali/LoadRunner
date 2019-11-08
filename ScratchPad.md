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


