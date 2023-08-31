# Future Careers (Microservices Architecture)

## _The platform that helps you manage your job applications_

> Future Careers is a web based service that searches the web for IT related jobs and consolidates search results to make it simpler for users to manage their job applications.

Future careers was built as a demonstration application to showcase the skills of the developers. The [First Version](https://github.com/alx-software-engineering-portfolio-2023/FutureCareers "Future Careers") of future careers was built with a monolith architecture and used Flask, a python web framework to deliver the project. This version has been updated to use a microservices architecture with a mix of different programming platforms.

The application will consist of 4 services that make up the application namely:

- a _Web User Interface_
- a _Web Scraper_
- a  _Job Applications Manager_
- and a _Notifications Manager_

The list of services could have been broken down further to promote the single responsiblity principle, however due to the nature and time constraints of the project these 4 services shall suffice.

## Services and Features

This section lists the different services and their features. It will be followed by a detailed description of the architecture as it should be when hosted on a production server.

### The User Interface

> The User interface is served by a dedicated WebUI service. It makes requests to the job applications manager, web scraper and notifications manager services to consume and/or send services requests. It acts as an intermediary/gateway between the user and the backend services.

### The Web Scraper

> The Web scraper service runs a background service periodically searching for job listings from a list of websites. It then consolodates the search results and saves them to a database which maybe then queried by other services.

### Job Applications Manager

> The Job applications manager performs services related to managing a users job applications. Users will be able to save jobs, track application statuses, 

### Notfications Manager

> The notifications manager

## DevOps (Development & Operations)

DevOps is the union of people, processess and tools. It promotes a culture of delivering software from development to production continously and quickly with the aid of automation tools and piplines.

Although is iterative in nature (continous integration), the planning, coding, building, testing, releasing, deploying, operating and monitoring will only be performed once for this project.

Each service will be developed in a separate repository with it's own technology stack. This allows each service to have it's own continous integration / continous delivery pipeline. This means that the delivery of new features is not dependant on the delivery of the application as a whole before they are delivered and can be used by other services.

### Planning

- Development

The code of the application will be hosted in separate repositories which will enable each service to be developed and deployed separately and in parallel to one another. Each service will utilize an appropriate technology stack and manage its own development cycle. Each service will outline in it's repository the interfaces that can be consumed by other services.

- Operations

DevOps encourages the use of automation throughout the development and deployment cycle. This means that operational infrastructure should take advantage of automation workflows that assist in provisioning it. IaC (Infrastructure as Code) tools such [terraform](https://www.terraform.io/ "terraform") and [ansible](https://www.ansible.com/ "ansible") that are supported by cloud providers become invaluable tools in ensuring the quick deployment (and destruction) of infrastructure.

This project will provision infrastructure using the IaC approach and provision a single node [kubernetes](https://kubernetes.io/ "kubernetes") cluster running containerized instances of the different services to ensure a high availablity of the application in production on both [Microsoft Azure](https://azure.microsoft.com/en-us/ "Azure") and [Google Cloud Platform](https://cloud.google.com/ "GCP").


### Coding

As specified in their respective sections above, a complete and detailed specification of the features, technology stack, design decisions and interfaces of each service will be detailed in the respective service's repository.

The links to the repositories and a basic overview of the technology stack can be viewed in the table below:

|   | [WebUI](https://www.google.com "Future Careers We User Interface Repository")  | [Web Scraper](https://www.google.com "Future Careers Web Scraper Repository") | [Applications Manager](https://www.google.com "Future Careers Applications Manager Repository") | [Notifications Manager](https://www.google.com "Future Careers notifications Manager Repository") |
|---|---|---|---|---|
|Language & Web Framework| (HTML, CSS, JavaScript) [Next.js](https://nextjs.org/ "Next.js") | Python [FastAPI](https://fastapi.tiangolo.com/ "FastAPI")| [C#](https://dotnet.microsoft.com/en-us/ "dotnet") [ASP.NET WebAPI](https://dotnet.microsoft.com/en-us/apps/aspnet "ASP.NET") | [TypeScript](https://nodejs.org/en "TypeScript") [Express](https://expressjs.com/ "Express")|
|Libraries|[Nextauth.js](https://next-auth.js.org/ "Nextauth.js") | [BeautifulSoup](https://beautiful-soup-4.readthedocs.io/en/latest/ "BeautifulSoup4") | | [SendGrid](https://sendgrid.com/ "SendGrid") |
|Database System|  | [MongoDB](https://www.mongodb.com/ "MongoDb") [Redis](https://redis.io/ "Redis") | [SQL Server](https://www.microsoft.com/en-us/sql-server/ "SQL Server") | [PostgreSQL](https://www.postgresql.org/ "PostgreSQL") |

The repository for the Azure IaC can be viewed [here](http://www.google.com "Future Careers Azure IaC Repo") and for the GCP IaC [here](http://www.google.com "Future Careers GCP IaC Repo")

### Building

Each service will output a CRI compatible image using [docker](https://www.docker.com/ "docker") that can be hosted in kubernetes. Before building the container image unit tests will be run for each service and also checked with [sonarqube](https://www.sonarsource.com/products/sonarqube/ "sonarqube") for code quality and security analysis in a CI/CD pipeline with [github actions](https://github.com/features/actions "github actions").

### Testing

Integration testing and quality assurance will be done on the production environment where the application will be hosted. It is recommended to set up a quality assurance (QA) environment within the pipeline before deploying to production for testing but due to the nature of the project this will be overlooked. Additionaly testing will be done by the developers on the own machines using a [lightweight kubernetes](https://microk8s.io/ "microk8s") environment on their local development or virtual machine.

### Release, Deploy, Operate and Monitor

