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
