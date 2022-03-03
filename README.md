## This workshop is based on Kelsey Hightower's excellent Craft Kubernetes Workshop on github.

You can find it here: [link](https://github.com/kelseyhightower/craft-kubernetes-workshop)

Kubernetes is all about applications and in these labs you will utilize the Kubernetes API to deploy, manage, and upgrade applications. 

During this workshop you will be working with the following Docker images:
* [kelseyhightower/monolith](https://hub.docker.com/r/kelseyhightower/monolith) - Monolith includes auth and hello services.
* [kelseyhightower/auth](https://hub.docker.com/r/kelseyhightower/auth) - Auth microservice. Generates JWT tokens for authenticated users.
* [kelseyhightower/hello](https://hub.docker.com/r/kelseyhightower/hello) - Hello microservice. Greets authenticated users.
* [nginx](https://hub.docker.com/_/nginx) - Frontend to the auth and hello services.
