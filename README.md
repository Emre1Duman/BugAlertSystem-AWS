## Python Bug Alert System with AWS integration
### Project Summary:

- Designed and developed a distributed system that sends bug alerts to Slack or Trello via webhooks using Python APIs and AWS.
- Postman was utilised to input dummy bugs, which were then retrieved with an HTML request through a Python API and sent to an AWS Simple Queue Service (SQS).


Two applications within the project:

- Functionality of Application 1 (GettingBugs Dir):
  - Receives dummy bugs from Postman with priorities (High, Medium, Low).
  - Sends received bugs to AWS Queuing Service (SQS).

- Functionality of Application 2 (SendingBugs Dir):
  - Utilises a scheduler to regularly check SQS for bugs.
  - Removes bugs from the queue.
  - Routes bugs to either Slack or Trello based on their priority via WebHooks.


<img src="https://github.com/Emre1Duman/BugAlertSystem-AWS/blob/main/Diagrams/Before%20Docker.png" width="700" height="600"/>


### AWS & Docker:

Originally, both Python applications were running on localhost, but recognising the need for online hosting, I opted for a solution involving Docker and AWS.

- Following thorough research, AWS emerged as the optimal choice, providing tailored services such as ECR, ECS, and EC2.
  - Given the project's use of SQS, sticking to the AWS ecosystem made sense.
- The deployment process involved creating a Dockerfile.
  - It included specifications for the latest Python version, commands to execute the pre-defined requirements file, and the initiation command for the application.
  - Since I utilized two Python applications for this project, both were containerized separately.
- The containers were then hosted on Elastic Container Registry (ECR).
  - Subsequently, Elastic Container Service (ECS) was employed to deploy these containers onto EC2 instances.


<img src="https://github.com/Emre1Duman/BugAlertSystem-AWS/blob/main/Diagrams/After%20Docker%26Cloud2.0.png" width="800" height="680"/>
