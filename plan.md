# The plan

## Experimenting with distributed system design.

### Backend
- CLassy -> Naive Bayes Classifier for sentimental analysis. Written in Golang. Has controllers to receive files, perform sentimental analysis then returns rating. Might actually be easier to write in Python and expose via flask, but considering we wish to learn more Golang we can write the classifier in Python and call it from the Golang service.

- Redis -> Cache analysis results by storing signature of analyses and using signature to quickly retrieve previously computed results. Cache recent results so users requesting same result quickly do not initiaite unecessary compute plus receive results quickly.

### Frontend
- Frontman -> React frontend. Simple form GUI allowing user to upload text file for analysis. Accepts email and any extra metadata we wish to collect.

### Production
- k8s cluster with n containers distributing application load. Write automation tests to test high availability and fault tolerance of the cluster.

### DevOps stack

- Docker pipeline to build services and frontend images and promote to enterprise image hub (maybe Azure Container Storage or ECS).
- Deployment pipeline to deploy the full stack including layer 7 LB (nginx), Cache (redis), application stack.
