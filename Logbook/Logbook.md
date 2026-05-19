Project Title: Cloud technologies portfolio report
Student: Paul Otto
Student ID: 241046

Week 1 and 2 Setup and Initial Exploration
The objective of Week 1 was to establish a reliable local development environment capable of supporting containerised workloads, gain foundational familiarity with Docker, and develop an initial understanding of the provided boilerplate application. Completing these tasks ensures that subsequent stages such as image creation, multi container orchestration, and cloud native deployment are built on a stable and well documented foundation.
1. Environment Setup
Docker Desktop was installed on Windows 11 using the WSL2 backend to ensure compatibility with modern Linux-based container tooling. Before installation, virtualisation support was confirmed in the BIOS, and WSL2 was configured as the default subsystem. 
The installation was verified using the commands docker version and docker info, both of which confirmed that the Docker Engine was running correctly. A functional test was then performed by running the hello-world container, validating image retrieval, container creation, and runtime execution.
2. Introductory Docker Tutorials
To build foundational competency, the introductory Docker tutorials were completed. These reinforced the conceptual distinction between images (immutable templates) and containers (runtime instances), while providing hands on experience with essential commands such as:
•	docker pull
•	docker run
•	docker ps
•	docker stop
•	docker rm
The tutorials also included practical exercises:
•	Running a NGINX container with port mapping to expose a local web server
•	Building a simple custom image using a Dockerfile
•	Inspecting container metadata using docker inspect
•	Experimenting with volumes to understand persistent storage behaviour
These tasks demonstrated how Docker abstracts application execution from the host environment and highlighted the operational benefits of isolation, reproducibility, and portability.
3. Boilerplate Application Exploration:
The boilerplate application was cloned from the tutor’s repository and executed locally without containers to establish a baseline understanding of its architecture. After installing the required dependencies, the application was launched using its native runtime.
The analysis focused on:
•	Backend API structure
•	Frontend components
•	Supporting modules
•	Routing logic and API endpoints
•	Data flow between components
•	Required environment variables
•	PostgreSQL database dependency
•	Runtime behaviour observed through browser testing
This exploration provided early insight into how the application could later be decomposed into containerised components and how its services might map onto a cloud native architecture.
Findings
•	Docker Desktop installed successfully and integrated correctly with WSL2 after resolving initial configuration issues.
•	Core Docker commands and workflows were understood and validated through hands on exercises.
•	Practical tasks demonstrated how Docker isolates workloads and ensured reproducibility.
•	The boilerplate application ran successfully in a non containerised environment, providing a clear baseline for future containerisation.
•	The application’s architecture revealed clear service boundaries and dependencies, particularly the PostgreSQL database and environment configuration.
Reflection:
Week 1 established a strong technical foundation for the remainder of the project. While Docker installation was mostly straightforward, resolving WSL2 configuration issues was essential for smooth operation. The introductory tutorials were valuable in reinforcing core container concepts that will be directly applicable when designing images and orchestrating multi container deployments.
Exploring the boilerplate application clarified its internal structure and highlighted several considerations for containerisation, including dependency management, environment configuration, and service boundaries. Overall, Week 1 provided a clear understanding of the application’s baseline behaviour and prepared the environment for more advanced cloud native development in the following weeks.
Deploy the application into a Kubernetes environment, establish reliable service‑to‑service communication, and validate internal networking behaviour. 
I created the required Kubernetes manifests, including Deployment and Service YAML files for both the backend and frontend components. The backend service was deployed first to ensure API availability, followed by configuration of the frontend to communicate with it using Kubernetes’ internal DNS. Where external access was required, I exposed services using NodePort (and Ingress where applicable). I then tested multi‑pod behaviour, internal routing, and service discovery across the cluster.
During deployment, several issues emerged. Pods were repeatedly restarting due to incorrectly configured environment variables, and services were initially unreachable from outside the cluster. I also encountered DNS resolution problems between the frontend and backend services. These were resolved by correcting ConfigMap and Secret definitions, adjusting the service type to NodePort, and relying on Kubernetes’ built‑in DNS for inter‑service communication. Once fixed, the application behaved consistently across multiple pods. 
week 4 deepened my understanding of Kubernetes’ service discovery mechanisms and the importance of declarative configuration. Deploying a multi‑component system highlighted how small misconfigurations can cascade into larger failures. Overall, I gained confidence in structuring and deploying containerised workloads in a cluster environment.
Evaluate the application’s behaviour under load, test horizontal scaling, and improve system resilience and performance.
I scaled the application using Kubernetes ReplicaSets and conducted integration testing across the frontend and backend. I reviewed container restart policies, validated self‑healing behaviour, and began preparing the screencast and supporting documentation. Load testing was performed to observe how the system responded under increased traffic and higher replica counts.  
Load testing revealed increased latency when scaling to higher replica numbers, and I observed occasional inconsistent API responses during rapid scaling events. The frontend also failed to update correctly after backend changes, requiring a refreshed build and redeployment. Backend optimisations were applied to improve response handling, and I ensured the service remained stateless to support horizontal scaling effectively.
Reflection:  
in week 5 reinforced the importance of stateless design in distributed systems and provided practical insight into Kubernetes’ scaling behaviour. I gained a clearer understanding of performance trade‑offs and how system bottlenecks emerge under load. These lessons will directly inform future architectural decisions.
Complete the final integration of all system components, produce the required documentation and screencast, and prepare the project for submission. 
I finalised the full system integration and produced the architecture diagram, project report, and a refined README.md with deployment instructions. A 5–7 minute screencast was recorded to demonstrate system functionality, including setup, deployment, and scaling. I also performed final verification of the Kubernetes deployment and cleaned the Git repository to ensure a professional submission.
Minor inconsistencies appeared during the final deployment due to cached container images, which were resolved by applying explicit version tags. The screencast required multiple recordings to achieve a clear and structured narrative. Documentation also needed refinement to meet academic standards, leading to a full rewrite in a formal tone
This final week emphasised the importance of version control for container images and the value of clear technical communication. Producing the screencast and documentation strengthened my ability to present a complete cloud‑native system confidently. The project concluded with a fully functional, well‑documented deployment running in Kubernetes.s