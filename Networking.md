
### What is Networking ?

*Networking* -  connecting different  computers through networks

#Network = Computer - switches  - routers - internet

*Firewall* -  keep safety, shouldn't come trough or go out 
*Wireless access point* -  connect all of them without cable

### What is Docker ?

*Docker* -  contain all needed things into a single, lightweight unit called a **container**. Building , running and shipping applications.

Docker :
 1. #Images - **read-only snapshot** that includes:
- The **operating system layer** (like Ubuntu or Alpine Linux)
- Your **programming language runtime** (e.g., Python, Node.js)
- All **dependencies/libraries** your app need
- Your **code**
- The **startup command** (how to run the app)

 2. #Containers - process that isolated environment for running application, lightweight, use OS of host, quick
 3. #VirtualMachine - software that lets you run another computer system _inside_ your main computer ---> through  software called *hypervisor* divides your real computer’s resources (CPU, memory, disk) and gives each virtual machine its own **slice**.
 
4. #DockerArchitecture:
		There are **3 main parts**:
		1.**Docker Client (CLI)** 🧑‍💻
		 2. **Docker Daemon (Server)** ⚙️
		 3. **Docker Objects (Images, Containers, Volumes, Networks**
5. #DockerHub - **online platform** where you can store, download and share image


6. #DockerfileStructure 
	 1. *Base image  - **foundation or starting point** of your Docker image.
		 1.  *alpine* - very small, lightweight Linux distribution that make smaller, efficient your container
		 2. Workdir - 
		 3. copy
		 4. 
	
7. #DockerCommands
		1. *run* - start the image
		2. build -t name .
		
8. #DockerVolume - **shared folder** between your computer and the Docker container. It’s used to **save data permanently** — even after the container is deleted.
	1. Named volume: stored by Docker
	2. Bind mount:  code and container share the same files instantly.

9. #Kubernetes - tool that **helps you run and manage lots of applications in containers**,**makes sure these containers run smoothly** across many computers (servers)
10. #EnvironmentVariable - a little piece of information your app can use while it’s running.
	1. ex: env port == 5000
11. #Portforwarding - **connect your computer or a container to the outside world** through a specific “door” (port).
	- Every computer or container has **ports** (like doors) that apps use to communicate.
	- By default, a port inside a container is **not visible outside**.
	- Port forwarding **opens a door from outside to the container** so people can access your app.
 12. #shell - **program that lets you talk to your computer** using **commands** instead of clicking things. ex: mkdir kamron
 
