Containerisation is the process of creating small, lightweight applications to act as individual services on a host. Containers are easy to deploy, scale out, and stop with as much automation as possible. Containers are a popular solution for microservices and the like, and can often be more cost effective to run than a dedicated server would. Moreover, containers are quick to restart and reset, as well as test and develop for. Popular containerisation engines include docker and kubernetes.

# Azure Container Instances
Azure container instances are a fast and easy way to deploy containerised environments in a [[PaaS]] service. Microsoft provides the host and operating system that the containers run on, but all applications and containers themselves are made by the user.

# Microservices
Microservice architecture describes a service design methodology where components and services are divided into atomized environments, seperated logically. This means individual parts can be updated seperately, as well as scaling and deploying resources for each module individually. 

# Azure Functions
Azure Functions are a "serverless compute" option. They are based on an event-driven architecture, where a specified event wakes the function and activates it. The rest of the time, there are no provisioned machines. Functions scale automatically with demand, and are ideal for short, individual operations that start and end definitively.
## Stateless or Stateful
This describes whether the function has knowledge of its past operations. A stateless function is completely restarted every time it is run however a stateful one (also called durable) is given a context when it restarts.





--- 
#azure #cloud #containers #theory 