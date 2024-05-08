
DevSecOps :- Mini-Project-1

**CONTAINER MONITORING with cAdvisor**

Container monitoring is the activity of continuously collecting metrics and tracking the health of containerized applications and microservices environments, in order to improve their health and performance and ensure they are operating smoothly. 
Containers have become one of the most popular ways to deploy applications, bringing benefits such as making it easier for organizations to improve their application portability and operational resiliency. 
In Cloud Native Computing Foundation (CNCF)’s 2018 survey, 73% of respondents indicated they are currently using containers in production to boost agility and speed up the rate of innovation. Container monitoring is a subset of observability — a term often used side by side with monitoring which also includes log aggregation and analytics, tracing, notifications, and visualizations. 
Compared to traditional monitoring solutions, modern monitoring solutions provide robust capabilities to track potential failures, as well as granular insights into container behavior. This page covers why, when, and how you should monitor your containers, and what challenges and solutions you can look out for.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Why monitor your containers?**

Having insight into metrics, logs, and traces greatly benefits operators of containerized platforms. 
Understanding what is happening not just at the cluster or host level, and also within the container runtime and application, helps organizations make better informed decisions, such as when to scale in/out instances/tasks/pods, change instance types, and purchasing options (on-demand, reserved, and spot). 
DevOps or systems engineers can also improve efficiency and speed resolution by adding automation, such as using alerts to dynamically trigger scaling operations. For example, by actively monitoring memory utilization, you can identify a threshold and notify operators as resource consumption approaches resource limits, or you can automate additional nodes to be added before available CPU and memory capacity is exhausted. If you set a rule to alert at, say, 70% utilization, you can dynamically add instances to the cluster when the threshold is reached.

**Challenges with container monitoring**

1. **Containers are ephemeral**
They can be quickly provisioned, and just as quickly destroyed. This behavior is one of the primary advantages to using them but it can be a struggle to track changes, especially in complex systems with high churn.

2. **Containers share resources**
Resources like memory and CPU are shared across one or more hosts, making it difficult to monitor resource consumption on the physical host, which makes it hard to get a good indication of container performance or application health.

3. **Insufficient tooling**
Traditional monitoring platforms, even those well suited for virtualized environments, may not provide sufficient insight into metrics, logs, and traces needed to monitor and troubleshoot container health and performance.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://github.com/Pawan-1008/devops/assets/109577088/d0ea0f16-828c-4e45-83a8-995261a9403b)

cAdvisor (Container Advisor) provides container users an understanding of the resource usage and performance characteristics of their running containers. It is a running daemon that collects, aggregates, processes, and exports information about running containers. Specifically, for each container it keeps resource isolation parameters, historical resource usage, histograms of complete historical resource usage and network statistics. This data is exported by container and machine-wide.

cAdvisor has native support for Docker containers and should support just about any other container type out of the box. We strive for support across the board so feel free to open an issue if that is not the case. cAdvisor's container abstraction is based on lmctfy's so containers are inherently nested hierarchically.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://github.com/Pawan-1008/devops/assets/109577088/8acbd326-c04d-4821-bd55-221432360487)

**Step :- 1**
First we’ll run the containers using following commands and images

--> docker run -dit  --name box1  nginx
--> docker run -dit  --name box2  lovelearnlinux/webserver:v1
--> docker run -dit  --name box3  centos 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://github.com/Pawan-1008/devops/assets/109577088/9c5d790e-89e2-408d-87b0-e8cd5268c999)

**Step :- 2**

checking the stats of the containers using,

--> docker stats -a

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------


![image](https://github.com/Pawan-1008/devops/assets/109577088/b9f0f137-3f97-4461-ba21-738d6af7acbc)

**Step :- 3**

checking the processes of the specific containers using,

--> docker top container_name  

here, we use box2 container

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------


