# Overview

This demonstration is intended to show off the CI/CD possibilities of Kubernetes; specifically Review Apps. Review Apps are 'per branch' deployments which are then accessible via their own URL. They are useful as they allow a developer to show their work at any stage to anyone who might be interested. 

# App

The application is a Hello world application with a little extra. If the environment variables `BRANCH` or `THIS_SERVICE` are present in the environment they will be returned when the application are called. This 'branch awareness' can be very useful when orchestrating a fleet of microservices for example.

# Review Apps

Review Apps are created by the CI/CD when new branches are pushed to Github. Review Apps are deployed into their own namespaces which allows easy cleanup with `kubectl delete namespace {{ namespace }}`. This cleanup process is not implemented in this demo but would be fairly trivial to achieve by various methods.


# Kubernetes

The standard NGINX ingress controller is being used. A wildcard DNS record for the staging domain is pointing to the ingress controller TCP loadbalancer meaning that no DNS changes are required for spinning up new Review Apps.

Currently there is no provision for a production deploy but one could easily be added. My preferred method would be an simple extra step which is activated by a git tag.




