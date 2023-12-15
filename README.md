# Scalable Web App using AWS Elastic Beanstalk DynamoDB CloudFront and Edge Location

![Picture showing the words Cloud Project and icons for the services used](https://miro.medium.com/v2/resize:fit:720/format:webp/0*QxQrWd3s2eX-BpiX.jpg)

In this project based on a real-world scenario, I was responsible for implementing a hypothetic application that would need to support the high demand of a large number 
of users accessing it simultaneously. This application would be used in a large presential/online hybrid conference, with a random draw at the end. The 10,000 attendees 
would need to register their emails on a website, to guarantee their participation. The app needed to have a scalable structure to handle a peak of simultaneous accesses.

On AWS I utilized Elastic Beanstalk to deploy the web application, DynamoDB to store the e-mails, CloudFront to cache the static and dynamic files on Edge Locations,
near the users. This structure guaranteed a good performance, along with the stability and scalability needed to handle sudden demand spikes.

![Picture showing the solution architecture for the project](https://miro.medium.com/v2/resize:fit:720/format:webp/0*lPupHmOv9guPuobI.jpg)

First I created a database on Amazon DynamoDB, to store the attendees e-mails. Next, using Elastic Beanstalk, the necessary structure was provisioned using a base of two
EC2 instances in a Scaling Group, ready to add two more instancies automatically when the base two use exceed 50% CPU use. During this stage I also uploaded the web app code. 
In a single step, Elastic Beanstalk provisioned the structure and deployed the web app!

![picture of Elastic Beanstalk provisioning the structure](https://miro.medium.com/v2/resize:fit:720/format:webp/0*gh_H9wcn0oQ0r9jf.png)

To validate the functioning, I did a test sign-up, which gave me an error. On CloudWatch logs, I could verify that the error came from a lack of permission on the role used by 
Elastic Beanstalk, which was quickly corrected using Amazon IAM. After the fix, the sign-up was a success.

With the application running and the structure ready, I went to the Delivery Optimization Stage, to make sure the online attendees would not have to deal with slowness when accessing 
the app. I used Amazon CloudFront to cache store the app on edge locations, allowing online attendees to use shorter routes to reach the application. Speed and agility are crucial 
to every application usability!

Lastly, I ran a test to validate the structure’s scalability. One of the EC2 instances wan a stress test, pushing the CPU use to above 50%. As configured by Elastic Beanstalk, the 
Scaling Group was activated, automatically provisioning a new EC2 already connected to the Elastic Load Balance, relieving the use of the already existing instancies. After the test, 
and with the CPU use reduced, the additional instance was automatically deactivated.

![Picture showing usage graphs](https://miro.medium.com/v2/resize:fit:640/format:webp/0*HW-ApH8YY93K504F.jpeg)

It’s incredible how it’s possible to provise a scalable structure, highly available and with excellent performance in a matter of minutes. Using the AWS tools, it was possible to quick 
setup the structure and make it available to users around the world. This is just a small example of the infinite potencial of what cloud technology is giving us.

![picture of the hyphothetical app](https://miro.medium.com/v2/resize:fit:720/format:webp/0*JAmhHze2BPSrk8i_.png)


