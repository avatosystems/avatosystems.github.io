# Introduction

Avato® is a hybrid integration platform that provides businesses with a robust technology foundation that securely, quickly, and simply integrates previously fragmented and incompatible systems and data.

Developed for the most complex, regulated environments, Avato de-risks digital transformation and delivers unmatched value.

Unlike other solutions in this space, Avato is priced to not "break the bank", so you can afford to create multiple clusters, enabling you to "divide and conquer" and implement your dream enterprise architecture.

![Avato Screen Shot](_assets/Avato-Product.jpeg)

Avato runs on any operating system, can run on-prem, in your own data center, or in the cloud. Physical hardware or VM, containers, Helm and or Terraform deployment models are all available. Avato's friendly HTML5 user interface is accessible from desktop, tablet and mobile alike, ensuring you have easy access to address the health of your critical infrastructure from anywhere, anytime, with just a few clicks.

In this article, you'll learn how to install Avato in just a few minutes.
Skip ahead to the [Docker Installation Guide](#docker-installation-guide) section below to get started.

## Applications

Avato excels in the following types of scenarios, any of which can literally save your organization millions of dollars and years of effort:

- You're a financial institution facing a major conversion project. Avato can isolate connected systems and mirror the old systems' APIs so that connected applications are not affected by the conversion.

- You're a credit union facing a core banking transformation. You're looking forward to your new banking system being up, but your existing vendors aren't able to cost-effectively support the new core banking system. Avato can adapt their API connections and protocols, so they don't need to change anything - their applications continue connecting as they always have.
  
- You're any organization that needs to feed data into a new GL system like Oracle NetSuite, and want to keep two years or more of historical data from your old system. You can implement stable reliable integration in Avato including any imaginable merging, splitting and correlation rules, and will iteratively feed past months of data through the interfaces, proving the veracity of the rules and getting data conversion as a side effect.
  
- You're a public health authority that needs to automate an antiquated supply system across channels, vendors and locations, but you're dealing with legacy systems like Meditech that don't even provide integration APIs. Avato can adapt to any form of data and operate with any system, modern or legacy, and can reliably throttle massive amounts of transactions, sparing your EHR system while completely and reliably automating the entire process. See [How Avato helped Integrate Health Systems in British Columbia](https://avato.co/content/how-avato-helped-british-columbias-provincial-health-services-authority/) for a case study.


- As discussed at Open Banking Expo - Avato can help with your Open Banking / Open Finance implementation by adapting your existing legacy and modern systems alike, so they can share data and adapt to the protocols necessary to enable FinTechs to connect customers to your diverse data sources.  
 


> NOTE: You will need valid Avato credentials as part of the process described here. **If you do not have such credentials,
please visit <a href="https://avato.co/one/request" target="_TOP">avato.co/one/request</a> to request access to Avato distributions.**

> NOTE: Any use of Avato is subject to end user evaluation license at <a href="https://avato.co/one/eula" target="_TOP">avato.co/one/eula</a>.
You accept this agreement by installing or using the software.

To learn more about Avato, join the discussion in the AvatoSphere community at <a href="https://community.avato.co" target="_TOP">community.avato.co</a>, follow us on LinkedIn at <a href="https://www.linkedin.com/company/avatosystems/" target="_TOP">company/avatosystems</a>, follow our YouTube channel at <a href="https://www.youtube.com/@avatosystems" target="_TOP">@avatosystems</a>, get updated packages and configuration on GitHub at <a href="https://github.com/avatosystems" target="_TOP">github.com/avatosystems</a>, or visit our website at <a href="https://avato.co" target="_TOP">avato.co</a>.

[![Avato Screen Shot](_assets/Darren-at-OBExpo.png)](https://community.avato.co)

## Recent Blog Posts

- [The Transformative Benefits of the Avato Hybrid Integration Platform for Credit Unions](https://avato.co/the-transformative-benefits-of-the-avato-hybrid-integration-platform-for-credit-unions/)
- [Unveiling the Hidden Dangers: How Avato Navigates the Data Minefield of Core Banking Migration ](https://avato.co/avato-data-core-banking-data-migration-transformation-pitfalls/)
- [Harness the Benefits of 12 Factor Apps for Your Integration Project](https://avato.co/harness-the-benefits-of-12-factor-apps-for-your-integration-project/)

# Docker Installation Guide

The fastest way to deploy Avato into a new environment is to use Docker Compose.
Here we describe doing that in 3 easy steps, that will likely take less than two minutes.


> TIP: A video demonstration of these steps for Windows is available at <a href="https://youtu.be/SvQEBi0fLD8?si=IU7f2xURjjqaG4Xy" target="_TOP">youtu.be/SvQEBi0fLD8?si=IU7f2xURjjqaG4Xy</a>. Note however it's even simpler than that now! See [**three steps**](#installation) below for *container-first* installation.

##  Pre-requisites

- Docker Compose or Docker Desktop installed onto your machine
- A basic understanding of how Docker works (optional, but recommended!)
- Valid Avato credentials (see note in Introduction above)

## Installation

Start with the docker-compose.yml file at
<a href="https://github.com/avatosystems/core/blob/main/docker-compose.yml" target="_TOP">avatosystems/core/blob/main/docker-compose.yml</a> or
<a href="https://avato.co/one/new" target="_TOP">avato.co/one/new</a>).
For your first installation, make sure the file is in a clean new folder and open the file in your favorite editor.

1. Edit the file and add your Avato username and password to the lines where it says `AVATO_UPDATE_CORE_USERNAME=` and `AVATO_UPDATE_CORE_PASSWORD=`.

2. Open a terminal window at location of the `docker-compose.yml` file.

3. Type `docker-compose up` and hit enter.

**That's it!**

Avato is up and running with a MariaDB database. You can log in with admin/password at
<a href="https://localhost:8443/avato" target="_TOP">https://localhost:8443/avato</a>.


## Next Steps

You will likely want to start by changing your password - click on the user gadget and choose `Change password`.

Then, explore the application, and review the documentation included with the distribution at <a href="https://localhost:8443/avato/docs/" target="_TOP">https://localhost:8443/avato/docs/<a/>.

We recommend you start with the Quick Start guide you will find there, which walks you through the user interface and helps you get a basic understanding of the platform.

Then, install the tutorials and work through them as you build your first real-time integrations, API transformations, automations, tasks, workflows and schedules.

## Important Directories

The first-time execution of the application will have created local `properties`, `packages`, `deploy`, `staging` and `core` folders in your current directory.

These allow quick and easy access to modifying your properties and custom packages from an IDE, as well as from the Avato web UI. They also enable version control from the host, and make real-time editing / testing possible, both inside and outside the container.

These mappings also allow restarts to be super-quick - the Avato core is only downloaded when it is missing, and the platform is only rebuilt when you've made changes within the local `properties` or `packages` folders.

> **BENEFIT:** An Avato container without changes to its configuration (hardware dependent) should now ***restart in under 10 seconds.***

## Updating Avato

You can update Avato as new versions become available by simply running the command ```docker exec avato ant update``` while your Avato container is running, or from the HTML5 UI when the platform/updates package is installed.
Other available Avato ant commands like "hot-deploy" can be executed in similar fashion - run ```docker exec avato ant help``` for more information.

## In Closing

Please keep in mind the above steps are written with the intention of getting an instance of Avato running quickly as
possible. For users with more experience using Avato, Docker and/or Docker Compose, we understand that more time may be spent in
customizing certain parameters in the 'docker-compose.yml' file, including configuring custom bindings to your local storage.
Customizing your Avato configuration involves updating the properties.xml, packages.txt, and using the user interface, as described in the documentation.

If you have any questions, please check our community forum at <a href="https://community.avato.co" target="_TOP">community.avato.co</a>, or email us at <a href="mailto:support@avato.co">support@avato.co</a>.

Avato® is a registered trademark of Avato Systems Inc. All other trademarks are property of their respective owners.
