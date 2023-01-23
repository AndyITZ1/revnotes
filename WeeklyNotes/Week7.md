# Week 7 DevOps/AWS

## Mockito and JUnit

### What is Mockito?
- Mockito is a "mocking" framework utilized wit


## Docker

### What is containerization?
- **Containerization** is the packaging of software code with all the libraries and dependencies needed to run the code to create a lightweight executable object otherwise known as a **container**.
- The purpose of containerizing an application is to allow to be portable in the sense of it (application) can be ran **reliably regardless of the host environment**.
    - Note: that this DOES NOT mean that you can simply run a container on any OS (operating system) it should be noted that **application containers** made on a certain OS (Linux, Windows, OSX) should be utilized on that OS as the host OS. Please refer to Docker section for more information. 

### What is a container?
- Containers are rather executable objects we can utilized and contained within them are an application with its dependencies. Containers separate the containerized application from other containers and from the host kernel.
- In essence, we can run multiple containers and they share/use the same kernel of the host system that they are on.

### What is the difference between using a container and a VM?
- While both are somewhat similar in the sense of being able to execute software on another system that isn't necessarily local (doesn't have to be the original system that made the application). 
- The difference is that containers only package the application and any dependencies it may need and does not store/package a whole operating system. 
- So to explain lets think of VMs (virtual machines) as a way of being able to run another operating system on the one that you are using at the moment. This of course means that the non-hosting OS will need some space for its own kernel to work (which means it will require a lot of memory space). This is a way of being able to run things like Linux on Windows or have Windows on a Mac. 
- Now, containers specifically "application containers" hold only the packaged software/application. This means those applications still require an OS to properly work so in this case they utilize the host system's kernel to work with and execute as a process. 
- This also means that containers are "lightweight" in the sense that it doesn't take a lot of space to package an application compare to a whole OS. And it is faster as we ARE NOT trying to boot an OS every single time as the application is expected to run using the current host's OS. 

### What is a container image?
- Containers are built from **images** which is a static file thats stores the executable code needed to create a container and stores everything like configuration settings, libraries and workloads that should run on the container.
- In short, **images** are a collection of files, including binaries, source code and dependencies needed to a deploy the container environment. 

### What is the difference between a container image and the container itself?
- A container image describes the container environment and acts sort of like the "template" for containers in what the containers has and has for configurations.
- During runtime, the container is the instance of that image that is a process that runs the way it was set up by the image. 

### What is virtualization?
- **Virtualization** is the process/concept that allows for creating/simulating the same environment for an application or basically the software layer so that it can be utilized on any host system. With Docker containers we are virtualizing the application and on it dependencies for it to be used and replicated on another host OS environment.

### What is isolation?
- Isolation is the idea of whatever is held in the container is separate from the host and can run independently on the engine it's running on. In a sense we want to isolate the contents of the container to keep it from being affected by the host operating system and any other processes on the host system.
- Most importantly, the goal of using the container is for that containerized application to work the way it does as it was simulated originally for. Meaning the application will run the same way regardless of the host operating system its be ran on the only same thing it has besides itself, is the runtime environment. 
- Isolation can be of several forms or a combination of some or all of these forms. This includes file system isolation, network isolation and even isolation of resource usages such as CPU and memory. How we can do these isolations really depends on the OS features and functionalities used to achieve this. A good example is Docker containers for the Linux OS, we can features like Linux's cgroups, seccomp filters, and kernel namespaces to place configuration/restrictions on how the container and it contents execute. 
    - cgroups allow placing resource usage limits on the a group of processes
    - seccomp allows for filtering system calls made by a process
    - namespaces limit what the application/process can see on the hosting system

### What are the benefits of containerization?
- Containerization allows for our application to be more secure in terms of virtualization and isolation.
- Containers are lightweight in that they can share the same OS's kernel and what is "containerized" is application and dependencies but not an entire OS, making it small/lightweight
- Containers are flexible in the sense loose-coupling of the application, where a container can execute on its own because it has its dependencies packaged with it and that we don't need other containers or software to be ran with the single container to perform its functionality.
- Similar to Java applications which follow the WORA (Write Once Run Anywhere), containers are standardized and thus portable that we shouldn't have to worry about the host system environment it is being executed in. 
- Containers are scalable in that since they are lightweight we can create an image to make another image that may contain more things likes adding on other applications or other configurations.
    - In this way we can achieve to types of scaling, horizontal and vertical. Where horizontal scaling, involves increasing the amount of applications performing the same task. While with vertical scaling, we increase the power of a single application hence what the application can do even more.

### Containers vs VMs Extended Notes
- Both are isolated, virtual processes that can run on their own on the host machine.
- VM main difference is that it doesn't just have the application and its depedencies but also the full operating system of that VM in each instance of it. 
- With containerization/containers, we avoid having full OS being separate for each container as the containers all run on the same OS (the host OS). This is where the benefit of lightweight comes in.
- A more simple breakdown of 3 scenarios
    - No Virtualization
        - This is when we just use/application without any form virtualized processes. Just downloading/installing the app directly on our computer. This may include installing the dependencies/libraries needed as well
        - This all then just interacts with the kernel as necessary
    - Containerization 
        - Application and dependencies/libraries are within a container
        - Containers share and utilize a container engine like the Docker Engine to run and execute, this engine is what really interacts with the kernel for the containers.
    - VMs (Virtual Machines)
        - Applications w/ dependencies and the OS used inside VM
        - Note that theses OS can/may differ as they aren't the host OS in that they are running on the host system
        - Virtual machines are managed/hosted/created by the hypervisor this is what allows for the VMs to run on the host system. 
- VMs
    - Pros
        - near total isolation in that basically whatever is needed the OS + Application + Dependencies is all there 
        - provides virtualization - basically virtualizing the whole OS making it portable to another host device
        - Ensures that an application runs reliably regardless of the host.
    - Cons
        - can be bulky and expensive in the resources utilized this includes the host systems memory and CPU being used up to run the VMs and their specific OSes.
Containers
    - Pros
        - Lightweight - no need to spin up guest OS
        - enable layers of isolation/partial isolation, this can be determined based on implementation
        - Provide a virtualized view of certain resources
            - sort of like limiting what the container can really utilized like capping memory, or using part of the filesystem (this could be simulating the host OS file system but truely its some section of the filesystem faraway from the actual host OS root)
        - Package an application in an isolated environment (this means only stuff for that application and not including a whole OS)
        - Ensures that an application runs reliably regardless of the host.
    - Cons
        - having layers of isolation defeats or doesn't necessarily meet the idea of total isolation. 
            - we may need strict isolation so that the application isn't influence or affected by the host OS or any other processes in any way
            - the opposite case is that is may be necessary sometimes to share resources between processes in differing containers.
    
### What is Docker?
- Docker is an open source platform that allows developers to build/deploy/run/update/and manage containers. In this sense Docker provides a platform as a service (PAAS) that uses OS-level virtualization to deliver a software application in packages in containers.
- Containers are executable components that combine applicatoin source code with the operating system libraries and dependencies required to run that code in any environment.

### What is Docker Architecture?
- Docker adheres to a client-server architecture in which the client is the command line interface or a user interface in which you use to run commands and interact with **Docker objects**, which these Docker objects are managed by the **Docker Daemon** which is in a sense the server.
- The Docker architecture describes the primary components that allow you to run and interact with Dockerized applications basicallly applications inside Docker containers.

### How does the flow of Docker Architecture look like?
- The client essentially includes all the commands that are given to manage the docker containers and images. Note that while the docker daemon is what manages the actual docker containers and images, the commands are there to act sort of like requests coming from the client to the server to do some action to the resources which are the containers and images.
- The docker host is basically the computer the docker daemon runs on and holds the containers and images being used locally on this computer. It should be noted that containers and images can be obtained from the registry which is centralized to hold and share docker images. 
- The docker daemon in effect the server is what really manages the containers and images or as a whole docker objects.
- We may use the term REST API in the sense of how client connects to the docker daemon, where client sends requests (run commands) and the docker daemon accordingly responds (manages or grabs/builds/deletes docker objects).

### What is Docker CLI (Command Line Interface) client?
- The command line interface (CLI) is what Docker developers typically use for interacting with the Docker daemon via commands.
- The set of commands used with Docker are prefaced by the `docker` command.
- The CLI client doesn't have to be any same machine running the Docker daemon in order to communicate.

### What is the Docker daemon?
- **Docker daemon** is a long running process that is responsible for managing docker objects.
- You can execute the docker daemon using `dockerd` along with that you can add flags to the command to configure the daemon.
- Besides, flags, you can use a config file to configure the docker daemon
- The docker daemon will persist all docker data into a particular directory and it can communicate with other docker daemon.
- With Docker Services, we can set up multiple docker daemons to be used as a **swarm** which is to behave as a cluster.

### What is Rest API in the context of Docker?
- The Rest API relevant to Docker are the command used by the CLI client and applications to interact with the Docker daemon. So bascially similar how we may use links and requests to pull/store data with regular APIs

### What are Docker registries?
- **Docker registries** are a centralized place where Docker images are stored and allowing for accessibility to images that can be used by Docker hosts. One such registry is the Docker Hub which is a public registry managed by Docker that docker hosts can pull images from and push images to by default.

### What are Docker objects?
- **Docker objects** are the building blocks that are managed by the **docker daemon**. These are typically the images and containers. Images are the templates that outline all dependencies for a particular container and it's primary process. Containers are the runnable instance of a set of processes and their dependencies.

### What is the typical flow of using Docker?
- First is using hte CLI commands like `docker build ...` or `docker pull ...` to acquire the image. Again the image layouts what is needed to create and run a container.
- With that the **docker daemon** will either pull your image from a registry or create the image (depending on the build/pull command)
- Upon getting the image, you can use `docker run ...` to create the container and start it. 
    - if you didn't get the image, this command will also implicitly pull that image from Docker Hub or a registry
- After the container is running, this is the starting point of the container's lifecycle since it was instantiated
- If the primary process doesn't finish on its own (where the container will exit on its own), then commands are used to manage a container's lifecycle to make sure it stop and start. 

### What are Docker images?
- Docker images are basically blueprints for a docker container, prior to building a container, an image must be created or pulled from a registry like Docker Hub.
- There is only one imager per container as containers are based on an image. You can create multiple containers from one image
- **Images can be built on top of each other**, which means that we can utilize a base image to add more libraries/dependencies and even our application to get another image. 
    - `From` keyword
- Just like any software there could be multiple versions of an image.
- We can **build an image** by using the `build` command and the required **Dockerfile** as a set of instructions as where to run the command.
- Similarly to how we can pull an image from a registry to use it, we can also push an image to the registry to basically share it on a registry like Docker Hub. 

### What is a Dockerfile?
- A **Dockerfile** defines everything needed to build a docker image. It outlines the starting point, dependencies, and commands that make up the processes needed for an image to be turned into a container. 
- In short, a **Dockerfile** provides instructions on how to build an image, and an image outlines on how a docker container is created. 
- As noted earlier, images can be built on top of another image, so when we first start writing in the **Dockerfile** we start with the `From` keyword and an image name or `scratch`. The image name is to specify a **parent image** that we intend to build on.
    - The word scratch is used instead with there are no image we are basing an image off of.
- `RUN`commands are set up next and there can be multiple as they are used to set up the environment the container will be running in. These commands are executed prior to starting a container.
- `COPY` command allows us to add files from the build context to an image.
    `COPY myApp.java myApp` this command will copy the `myApp.java` file and place it into an image called `myApp`
- `EXPOSE` command allows use specify/outline the port that the container will be opened on.
- `CMD` runs a command at the end of the **dockerfile** when the container is fully created. This command is only ran once and if there are multiple `CMD` commands, only the last one runs.
- Each instruction forms another layer of the docker image and these layers are **cached** to speed up the build.
- Again dockerfile commands are used to do stuff like installing software in the container, copying/adding files from our local and remote systems, defining environment variables for the container, and executing commands such as running the app in the container. 

### What are other commands used in a dockerfile?
- `VOLUME` is used to create a mount point in the image and thus container with a particular name, which is used to access files in this directory that will be shared with resources outside of the container.
- `WORKDIR` sets the working directory in the image and eventual container of commands that follow

### What is difference between a base image and a parent image?
- A **base image** is an empty image slate that is utilized to build an image on when we use `FROM scratch`. This is used when we have no specified pre-existing image that we are using to build the current image.
- A **parent image** is the pre-existing image that we may specify that we want to build on top of using `FROM parent-image-name`


### What are the states of a docker container?
- Docker containers can have states, which indicate what a container is currently doing. 
- States:
    - **Created**, identifies that a container has been created by the docker daemon, but not started
    - **Restarting**, container is being restarted
    - **Running**, container has been started and is running
    - **Paused**, container has been paused by the daemon
    - **Exited**, container has completed its process and has stopped
    - **Dead**, indicates that while you have remove "part of the container" using the daemon, part of it is still active and using resources which means the daemon failed to remove it entirely. 

### What are Docker best practices?
- The goal for docker containers are to be **ephemeral** in the sense that containers should be easy to *tear down* as they are *build up* and they require only minimal configuration.
- Furthermore containers should be lightweight and as well as images should lightweight.
- Lightweight containers relies on other best practices like the **build context, leveraging multi-stage builds and image cache**
- Build context refers to the working directory that is to sent over to the Docker daemon when image is created. So the less files in the directory the faster the building process is and also the lighter an image is.
- Images are previously used are cached and with images being layered we can take advantage of this speed up the process when building other images. It reduces the amount of times need to pull from the remote storage or rebuild image layers. 
    - However this can be a con is even though some layers are cached, they may not be properly updated.
        - If you have `RUN apt-get update` this is the same string read everytime and will not be executed if the cached image was built the same way everytime with no change. 
- Other best practices:
    - Separate each dockerfile command to a line so that the file becomes readable
    - Use docker volumes for having persistent data
    - Use secrets for sensitive data, use config files for configurations that aren't sensitive
    - Containers should ideally serve one purpose and applications should be decoupled as much as possible
    - Having the least number of "ultimate layer" for an image possible
        - defined by different commands in the dockerfile


## AWS

### What is EC2?
- EC2 or Elastic Cloud Compute, is a computing service provided on the AWS cloud platform. It allows user to use a remote virtual computer that can pretty much run everything a local computer could do, and you can configure the device to meet any requirements you may neede from RAM to storage capacity. 
- As with any other AWS services, you are technically renting out some part of the AWS Cloud meaning you will be billed based on your usage of the specific service's billing charge rate. 
- EC2 besides resizability also offers things like security, reliability, high-performance and cost effective infrastructure to meet the needs of clients/users. 
    - It's high performance, in that the virtual device you are using is run with the best hardware and software provided by AWS
    - It's cost-effective in that AWS has high-performance gear and more things like more storage and/or RAM, which can be all expensive on their own to locally build your computer/system/server
- EC2 also offers users with a selection of operating systems along w/ pre-configured resources to use for the EC2 instance. There's is an option in which lets user saved a default + user-defined configuration for the next time they create and configure a new AMI (Amazon Machine Image)
- Users are given the option to upload their own operating system, but AWS offers usually the most preferred set of operating systems available for EC2 (Amazon Linux, Windows, Ubuntu, SUSE Linux, and Red Hat)

### What is AMI (Amazon Machine Image)?
- Amazon Machine Image is a supported and maintained image provided by AWS that provides the information required to launch an instance (EC2 or any other AWS service that utilizes AMIs). The information required could be the OS the instance is going to utilized and the various configurations in terms RAM, storage space and more. 
- You can choose to also customize an AMI's configurations to be saved for use next time when you want to launch an instance without really having to go configure every piece of configuration you want for an instance. 
- Similar to docker images, you can use AMIs to launch multiple instances using the same image or use different AMIs for differently configured instances.
- Even more EBS snapshots, block device mapping specifying volumes attach to an instance, launch permissions for user access can be included in an AMI. 
- AMIs are not bound to a region, you can copy an AMI to be utilized in a different AWS region. AMIs can be registered and deregistered and you can search for some. 

### What is EBS (Elastic Block Storage)?
- **Elastic Block Store** or EBS is a block storage system used to store persistent data. EBS can be used w/ EC2 instances providing highly available block-level storage volumes basically SSD memory. EBS Volumes are independent of EC2 instances in that they run on their own and not necessarily tied to an EC2's lifecycle and they are "devices" when mounted on an EC2 instance. 
- EBS benefits:
    - **Reliable and secure storage** each EBS volume automatically responds to its "Availability Zone" to protect from component failure
    - **Secure** Amazon's flexible policies allows for users to specify who can access EBS volumes and also encryption is provided for the EBS volume
    - **Higher performance** - 

### What is AWS S3?
- S3 or Amazon Simple Storage Service is an object storage service that offers high scalability, availability, security and performance. Data is stored as an individual object that is put into a **bucket** and rather than in some of hierarchyy like that of a file system/directory structure.
- Most types of files can be stored using the service. This considers customer of all sizes and industries can use it to store and protect any amount of data for different range of use case such as websites, mobile apps, backup and restore, enterprise applications and more.
    - This includes files for backup and storage, application hosting, media hosting, softwares, static website hosting. 
- You can access/connect to S3 via a URL and the URL will contain the object's name and the bucket's name
- You use a REST API to connect to S3 and the browser does a HTTP PUT request to put the objects in the bucket


### How do you configure S3 Buckets?
- To upload any data to Amazon S3, you need to create an S3 bucket in an AWS Region. 
- Again every object stored in Amazon S3 is inside a bucket. Which can be used to group objects together in the same way you would use a directory to for grouping files in a file system. 
- Creating the Bucket:
    - You need to sign into the AWS management console and open S3
    - Choose `Create bucket`
    - Then enter the bucket name in `Bucket name`, this name should be DNS-compliant. Along with that the name must:
        - Be unique across all of Amazon S3
        - Be between 3-63 characters long
        - Cannot contain uppercase characters
        - Start with a lowercase letter or number
    - Chooose AWS Region
    - Bucket settings, uncheck Block Public Access if needed
    - Create bucket


## DevOps


### What is DevOps?
- **DevOps** stands for Development and Operations, is a methodology/combination of philosophies and practices that is used to automate and integrate processes between software development and IT teams. It works in the concept of having a team composed of both developers and IT operations working together throughout a product's lifecycle, in order to increase the speed and quality of software deployment. Basically it combines development, deployment, and maintenance of code into a streamlined process. 
- Tools used in **DevOps** include ones used to tackle DevOps fundamentals like **continuous integration, continuous delivery, automation, and collaboration**. 
- The goal of DevOps is to expedite the app development lifecycle through automation workflows and measuring application performance continuously. 

### What are the steps/phases for DevOps?
- **Source Code Control**: This involves pushing and pulling written source code to a repository for version control
- **Building and Testing Automation**: This is usually testing the basic functionality of code and creating a new working build 
- **Deploy to Staging**: This is deploying a working build to a temporary environment where more tweaks/polishing may be done to the working build prior to moving it out into the next step.
- **Acceptance Testing**: This involves more complext testing of the build which includes system, integration testing, and user testing within the staging environment.
- **Deployment of Build**: After a build has gone through of all of its testing, the working build is then moved to a production environment where it becomes accessible by end users. 

### What is Agile?
- Agile is philosophy utilized as an approach to creating software and addressing the software development life cycle. Agile focuses on producing the code through iteration and collaboration rather than working on the whole project at once.

### How does DevOps approach software development?
- DevOps approaches creating software and producing code systematically.

### How does Agile relate to DevOps?
- Agile focuses on creating software and adapts to change quickly can seem contradictory to DevOps systematic approach. The **end goal of both** is to produce working and valuable products more efficiently.
- They differ in that DevOps pertains to the entire system/project and working together to produce, test, deploy and maintain the code base. While Agile allows for each step of the process to be changeable wheenver and wherever needed.
- Agile philosophies can be adopted into DevOps pipeline in the sense of continuous feedback loops that are common in Agile. Continous integration, continuous delivery, and continuous deployment are used and sought to be automated as phases in the DevOps. 

### What is Continuous Integration?
- Continuous Integration is a software development process of regularly and consistently merging code into a central repository and reviewing new code to ensure proper integration with the previous established code base. 
- You may use things like Github, Gitlab to perform this process.
- In general the central repo should be a version control software which provides the benefit of being able to track changes in code, allow for code to be merged and/or rollbacked if necessary. The more code is committed or merged the less conflicts with integrations arise. 

### What are the benefits to having Continuous Integration?
- **Continuous Integration** establishes the foundation for an automated DevOps pipeline with the following benefits:
    - It ensures the team is working with the most up-to-date code
        - Frequently pushing code allows developers to account for changes made by other team members
    - Allows for detection of broken builds quickly
        - Version control software can have detect the root cause and allows for rollback of changes
    - Code can be tested easily by making separate branches for testing/development based on the main code
    - Reduces risks in development when a large codebase is established
    - Reduces the overall amount of bugs in a project. 

### How to make Continuous Integration work best?
- The best way for code to integrate well is to test it by running test suites after a commit is made. This help minimize conflicts. But it is also recommended to also practice Test Driven Development in general.
- **Test Driven Development** is the practice of developing code based on written test cases as opposed to writing test cases based on developed code. So the cycle of development follows writing tests first and then writing code to pass those tests.


### What is Continuous Deployment?
- **Continuous Deployment** is the process of deploying software to production environments as long as changes are tested for stability and correctness, and this testing is done automatically. When **Continuous Deployment** is achieved (after Continuous Delivery), every committed change to the code base creates and deploys a new build to the production environment. 
- This is the ultimage goal for establishing "a true DevOps" pipeline as it ensures all steps for creating a product including code creation, testing, building and deployment are automated and work seamlessly together. 

### What are risks/costs to Continuous Deployment?
- Creating/Establishing a Continuous Deployment pipeline requires a more substantial investment in the engineering and testing culture
- The documentation of processes needs to be commmunicated to the development, production, and testing teams
- Ongoing maintenance of deployment pipeline is needed to ensure work continues smoothly, which can increase production costs
- Communication of completed features and progress otherwise **feature flags** are required for coordination between departments 

### What are the benefits to Continuous Deployment?
- Faster development process w/ out pausing for deployment 
- New releases are less risky, in that as small changes can be recognized and fixed allowing for better/quicker feedback
- Increased team communication and regular streams of improvements are held in high regard by customers

### What is Continuous Delivery?
- **Continuous Delivery** is the paradigm in which building/management/ and testing of produced software is automated such that deployments can happen at the push of button. **Continuous delivery** is only achieved when code integration, testing and product building is automated as this allows for frequent deployments.
- Frequent deployments may not always be the case if you are following some regular schedule for deployment
    - Also the deployment process may be kept manual to allow for final user acceptance tests to be performed as a final safety check to ensure business needs are met. This is due to the difficulty and costof creating tests to evaluate user experience


### What are benefits of Continuous Delivery?
- Reduced Risk in Deployment
    - New builds aren't deployed automatically, which mean faulty code is less likely to be pushed to production
    - Less pressure on development team by allowing for small and more frequent changes 
- Predictable Progress
    - With a pipeline the deployment process is more predictable in that we kind of know when we are deploying, so development team can focus on the production of code rather than the steps to deploy the new codebase
- Frequent Feedback
    - With increasing the efficiency of producing code, more smaller and incremental changes can be applied more often and we can always rollback changes if something errors





