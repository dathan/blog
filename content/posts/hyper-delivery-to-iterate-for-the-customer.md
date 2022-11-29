---
title: "Hyper Delivery to Iterate for the Customer"
date: 2022-11-29T12:06:24-04:00
draft: false
---

As software engineers, especially product engineering, one of our core objectives is to deliver software solutions to customers quickly, while still maintaining the quality of the product. It is not enough to simply produce a product and ship it out - we need to ensure that the product fits the customer’s needs, and can evolve to meet the customer’s changing demands. To achieve this, we need to establish a set of software delivery practices that prioritize speed and iteration to find product market fit.


One of the most important considerations for software delivery is iteration. Iteration is the process of continually improving our product based on feedback from the market and our users. It’s a way of fine-tuning our product to ensure it is meeting the needs of our customers. Iteration is also a quick indicator that a feature or set of features needs sunsetting, a process of removing the feature from the site if customers are not finding value in it.

When it comes to delivering a consumer application, several key practices can help ensure successful iteration. These include:

1. Automated Builds: Automated builds are a must when it comes to software delivery. Automating builds saves time and increases the speed of iteration.

2. Continuous Integration: Continuous integration (CI) is a practice of merging code changes into a single version of the product. This allows us to quickly test our changes and detect any bugs or errors that may have been introduced.

3. Automated Testing: Automated testing is a critical component of any software delivery process. Automated tests ensure that our code is functioning as expected and that our product is meeting the needs of our users.

4. Monitoring and Metrics: Monitoring and metrics are essential to understanding how our product is performing in the market. We need to be able to track usage, detect errors, and measure the success of our iteration process.

5. Continuous Delivery: Continuous delivery (CD) is a practice of continuously delivering new features and updates to our users. This allows us to quickly respond to customer feedback and ensure our product is always up to date.

Above is a generic good practice set of rules AFTER a team agrees to the project layout, workflows, infrastructure to use, definition of delivery to a customer to include tools with the product, and a dashboard measuring the value of the product from internal product metrics. What about building from scratch? How do you ensure delivery quickly to the customer and then phase in best practices to ensure quality?


## Tips on starting up and keeping delivery velocity

### Agree on a project layout and framework and endpoint interface with a client

This step defines when to write a cronjob, versus making an endpoint for the front-end client to consume. This also sets up a workflow of how to add endpoints, and what permissions are needed to view said endpoints.

### Each Software Engineer is given Ownership of a full-stack implementation

The goal is to get the product out to the user and verify that the solution provided makes sense. You can spend years trying to guess if something works, or the customers you are building for could tell you as you build it.  

To enable teams, allow them to achieve the product specifications in a silo following the established workflows, using a small set of infrastructure to deliver a monolith to the customer as quickly as possible. This also means that as a team you're prepared to refactor during iterations of the initial product offering.

### Workflows 

Workflows are common patterns used to add functionality to the product. For instance, using a Front Controller for an MVC framework. This gives direction on how to add an endpoint, and also it gives confidence to the team that login does not have to be implemented multiple times. Additionally use the same language to move fast, and start with a monolith so each developer is developing in the same development environment with Github actions pushing to production.


### Start Simple and only add complexity when needed

Initially, after the team agrees on a layout, and workflows, next pick 4 infrastructure items to start with. For instance containers, k8s, Postgres, and cronjobs. Do not add more tools until you have users. Remember 100s of new users a week, with a simple backend, allows you to iterate much faster. The scale comes in when virality and or product market fit comes in. Thus do not make a complex backend. Consistency and simplicity will get you very far. Pre-scaling is a time sync. Add
comlexity like a message bus, when your solving asyncronous problems that polling cannot solve, such as scaling a team.

### Conclusion

By implementing these practices, we can ensure that our software delivery process is efficient, effective, and successful. Our goal should always be to find the best product-market fit for our users. With the right processes in place, we can ensure that our software is always meeting the needs of our customers.

