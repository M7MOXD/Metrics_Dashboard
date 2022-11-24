**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

_TODO:_ run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation

![img_1](./answer-img/Screenshot%20from%202022-11-23%2022-31-14.png)

## Setup the Jaeger and Prometheus source

_TODO:_ Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.

![img_2](./answer-img/Screenshot%20from%202022-11-23%2022-32-16.png)

## Create a Basic Dashboard

_TODO:_ Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

![img_3](./answer-img/Screenshot%20from%202022-11-23%2023-38-31.png)
![img_3.1](./answer-img/Screenshot%20from%202022-11-24%2016-50-52.png)

## Describe SLO/SLI

_TODO:_ Describe, in your own words, what the SLIs are, based on an SLO of _monthly uptime_ and _request response time_.

- The Service Level Objective(SLO) is the expected or overall projected performance goals in specific timeframe whereas the Service Level Indicator(SLI) defines or records the achieved performance level against the proposed SLO. Incase of the monthly uptime, the SLI would be a recording of the 90% of the service uptime against the expected SLO of 99.9% in a month. Meanwhile, for the request response time; the SLI will be an achieved average response time of 95ms against the expected SLO of 100ms in a specific month.

## Creating SLI metrics.

_TODO:_ It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs.

A. _Uptime_

- This covers the total amount of time that a service is available to the customer. In our case, the service should mostly be up and running, and if the service is down then the reasons must be investigated and mitigated based on the SLIs so as to ensure that we always offer our customer the best service for the projected service level objectives(SLOs) in on a monthly uptime basis.

B. _Error Rate_

- This encompasses the intensity at which the service fails in a specific time. That being said, it is crucial that all errors with our services are investigated and dealt with accordingly so as to esnure that our service is operating with minimal faults or fast recovery from errors.

C. _Traffic_

- This includes the total amount of requests that are made to the service in a specific time. This should also cover all concurrent requests from various users per a specific time. In our case, it will be capture to the amount of traffic so that we can easily sense on how the service is able to couple up with issues inline with service's traffic overload.

D. _Network Usage_

- This covers the amount or percentage of network bandwidth that a service requires in a specific time so as to fully to handle all of the request payload. This is is crucial because sometimes network performance can be a barrier or booster to the performance level of our service.

E. _Latency_

- This covers the total time to process a request and offers the right feedback to the customer or client. It is therefore crucial that we measure the latency so that our customers are not frustrated due to long waiting time for the requests to be fully processed.

## Create a Dashboard to measure our SLIs

_TODO:_ Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

![img_4](./answer-img/Screenshot%20from%202022-11-23%2023-59-25.png)

## Tracing our Flask App

_TODO:_ We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

![img_5](./answer-img/Screenshot%20from%202022-11-24%2000-00-47.png)

## Jaeger in Dashboards

_TODO:_ Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

![img_6](./answer-img/Screenshot%20from%202022-11-24%2000-03-31.png)

## Report Error

_TODO:_ Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name: Error on backend/app/app.py

Date: November 24 2022, 17:12:25.241

Subject: Fails to add the name and distance of the star

Affected Area: ./reference-app/backend/app/app.py" for the /star endpoint

Severity: High

Description: 500 Internal Server Error The application issues the 500 error upon the addition of the star to the database. Meanwhile, inspecting the span everything appears to be ok but there seems to be an issue caused by the mongodb://example-mongodb-svc.default.svc.cluster.local:27017/example-mongodb, which is not available on the local cluster. Hence, the MongoDB Driver and URL must be available on our local cluster.

![img_7](./answer-img/Screenshot%20from%202022-11-24%2017-20-15.png)
![img_8](./answer-img/Screenshot%20from%202022-11-24%2017-24-10.png)

## Creating SLIs and SLOs

_TODO:_ We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

- Uptime: The application/service should be up and running for atleast 99.9% of the time on monthly basis.
- Latency: The average request response time should not exceed 15ms on monthly basis.
- Error Rate: The 20X status codes should be recorded for not less than 99.9% of the total requests whereas the 50X and 40X status codes should be recorded for less than 0.1% on all of the http requests made in month.
- Saturation: he overall capacity of a service (such as the percentage of memory or CPU used). CPU should be less than 96% within a month.

## Building KPIs for our plan

_TODO_: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

A. Uptime

- CPU Usage: This captures the amount or percentage of the cpu being used by an active service or pod.
- Memory Usage: This captures the amount of memory being used by an active service or pod
- Uptime: The total time that a service is available for usage

B. Error Rate

- http 40x errors: This captures all of the 40x errors per second
- http 50x errors: This captures all of the 50x errors per second

C. Latency

- Jaegar Span's Duration: This captures the duration of the tracing of the service's spans
- Latency: This captures the total http's response time

D. Saturation

- Resource Capcity: CPU, RAM usage per pod. . Needed to measure saturation

E. Network Usage

- Network capcity: successful request per second / request per second. To measure any network bottlenect

## Final Dashboard

_TODO_: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.

![img_11](./answer-img/Screenshot%20from%202022-11-23%2023-38-31.png)
![img_12](./answer-img/Screenshot%20from%202022-11-23%2023-59-25.png)
![img_13](./answer-img/Screenshot%20from%202022-11-24%2017-32-16.png)
![img_14](./answer-img/Screenshot%20from%202022-11-24%2017-56-18.png)

- Uptime: The total time that the services are up and running
- Errors: The http 40X and 50X errors encountered by the services
- Latency: The http request response time
- CPU Usage: The amount of cpu used by containerized applications especially the backend and frontend service
- Memory Usage: The amount of memory used by the containerized applications especially the backend and frontned service
- Jaegar Spans: The trace for the backend and frontend service
