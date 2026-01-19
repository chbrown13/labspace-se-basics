# Introduction

👋 Welcome to the **SE Basics** workshop! 

In this workshop,[^1] you will gain hands-on experience with several core tools and activities to support software engineering work in practice. By the end of this workshop, you should gain a deeper understanding of:

* What is software engineering
* How common tools and practices fit into software development


## 🙋 What is software engineering?

Software engineering is a discipline that encompasses:[^2]
*  the **_process_** of software development; 
* **_methods_** for software analysis, design, construction, testing, and maintenance; and 
* **_tools_** to support the processes and the methods.

Together, these concepts help teams build software that is not only functional, but also reliable, maintainable, and scalable.
 
## 🔄 Software Development Lifecycle (SDLC)

Most software projects, regardless of language or domain, follow a variation of the _software development lifecycle_:[^3]
1. **Requirements:** Understanding requirements for the system
2. **Design:** Deciding the structure of the system
3. **Implementation:** Translating the design into a concrete system
4. **Testing:** Verifying the system behaves as expected
5. **Deployment and Maintenance:** Release, monitor, and fix the software

We will cover each of these phase in detail during class this semester. For this workshop, you will receive a high-level overview of tools and practices that impact the SDLC.

## Getting Started

This workshop is built on Docker Labspaces. Docker Labspaces provide fully packaged learning labs, workshops, and demos for technical concepts. To launch the workshop, run the following command in your terminal (requires Docker):

```docker compose -f oci://chbrown13/labspace-se-basics up -d```

Next, open your browser to http://localhost:3030. You should see the workshop in your browser. Select "Load VS Code here" to display a development environment in your browser alongside the workshop activities.

<img src="/.labspace/images/labspace.png" />

[^1]: The content of this workshop is based on the [Engineering Basics](https://github.com/chrisparnin/EngineeringBasics) workshop by Dr. Chris Parnin

[^2]: Definition adapted from "Software Engineering: A Practitioner's Approach" (Pressman)

[^3]: As defined by this class, specific terms and phases will vary based on company, team, process, etc.
