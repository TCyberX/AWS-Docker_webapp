<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy an App with Docker

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eb)

**Author:** Albert  
**Email:** tapcyberx@gmail.com

---

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-compute-eb_c4df13c84)

---

## Introducing Today's Project!

### What is Docker?

Docker is a software platform that utilizes operating system-level virtualization to deliver software in standardized units called containers. These containers are useful because they are isolated, executable packages that contain everything needed to run a piece of software. In this project, I used Docker to deploy an application locally with Docker Desktop and then ran the same container with a custom image to Elastic Beanstalk.

### One thing I didn't expect...

One unexpected aspect of this project was the ease with which I understood containers; their management via the Docker Desktop version on my local computer proved to be remarkably intuitive and straightforward.

### This project took me...

This project required approximately two hours to complete. The most challenging aspect was the setup of AWS Beanstalk, as it involves numerous considerations and requires careful attention to detail in each step. However, the most rewarding aspect was witnessing the successful deployment of a web application using custom images.

---

## Understanding Containers and Docker

### Containers

Containers package everything an application needs to run. They are useful because they ensure applications run the same way, every time, regardless of the computer or environment. This solves the common problem of "it only works on my machine."

A container image serves as a blueprint or template for creating containers. It provides Docker with precise instructions regarding the contents of each container, encompassing the application's code, necessary libraries, and any other required files.

### Docker

Docker is an open-source platform facilitating the development, deployment, and execution of applications through the use of containers. Docker Desktop provides comprehensive management capabilities for containers, enabling users to create new containers, modify their configurations, and monitor their performance.

The Docker daemon is a background process that manages Docker containers on your computer, handling the building, running, and distribution of them.

---

## Running an Nginx Image

Nginx functions as a web server, a software application essential for hosting websites and web applications. To enable website accessibility, a web server is required to transmit website files to user browsers.

The command I ran to start a new container was docker run -d -p 80:80 nginx.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-compute-eb_6245f5bb10)

---

## Creating a Custom Image

The Dockerfile serves as a document containing all the necessary instructions for constructing a Docker image. Docker utilizes the Dockerfile to comprehend the required environment setup for an application, including the installation of necessary software packages.

My Dockerfile instructs Docker on three key aspects: Firstly, "FROM nginx:latest" signifies that our image is initialized as a copy of the most recent Nginx image. Secondly, "COPY index.html /usr/share/nginx/html/" replaces the default Nginx HTML file with my custom `index.html`, enabling the Nginx server to serve my web content. Lastly, "EXPOSE 80" specifies that the container should accept web traffic on port 80, making it easier for users and other services to access my web application.

The command I used to build a custom image with my Dockerfile was (docker build -t my-web-app .). The '.' at the end of the command tells Docker to find the Dockerfile in the current directory.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-compute-eb_4c741d1913)

---

## Running My Custom Image

I encountered an error when running my custom image because it was trying to use the same port as a previously running container. I resolved this by stopping the container that was using that port.

In this example, the container image serves as a blueprint, providing Docker with instructions on the application code, dependencies, libraries, and other components to be included in a container. The container itself represents the operational software instantiated from this image, currently functioning as a web server and displaying the index.html file.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-compute-eb_74b5c3d619)

---

## Elastic Beanstalk

Elastic Beanstalk is a service that facilitates the straightforward deployment of cloud applications, eliminating the need for users to manage the underlying infrastructure.

Deploying my custom image with Elastic Beanstalk took about 10 minutes to figure out and understand the concepts. I really enjoyed learning about it!

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-compute-eb_26d5573b23)

---

## Deploying App Updates

To demonstrate the deployment of application updates using Elastic Beanstalk, I modified the application by updating the index.html file and saving the changes in the designated folder. I then verified these modifications by accessing the file through Google Chrome, confirming that the updated image, as reflected in the code, was displayed correctly.

My app updates didn't show up in my live environment immediately because... To deploy my changes, I only had to...

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-compute-eb_5b7034684)

---

---
