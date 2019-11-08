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


