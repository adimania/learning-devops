# What is scaling?
When we make an application on our laptops, we run it for one user. In advanced stages of development, we may test it for multiple mock users. Quality testers usually do a load test to simulate hundreds or thousands of user. Even without going into production, an application built with one user in development has to go to a scale of hundreds. In production, the application might see tens of thousands of users. In such scenarios, one would need to scale the application to handle these many users.

While scaling, one always need to scale for maximum expected traffic, and not for average. 

In principle there are two kinds of scaling:
* **Horizontal Scaling:** When we handle additional traffic by simply adding more instances of application or the system.
* **Vertical Scaling:** When we handle additional traffic by increasing the capacity of the same application instance.

#What should one prefer?
As much as possible, always go for horizontal scaling. This is because, at the end, there would always be a limit on how much resources one can add to a single instance of application or system. While, *theoretically*, horizontal scaling offers infinite scaling. 