# Exercise 6 - More secure builds

## Problem
When we have to install dependencies from a private registry we will need to authenticate. 
However, we don't want the credentials stored in version control. 
We also don't want our credentials visible in the layers manifest or build logs for the deployment image.

## Principle(s)
- Multi-stage builds
- Build variables

## Detail
We can use build variables to inject values at run time and set environment variables for use deeper in.

We can also create stages in our dockerfiles. Earlier stages and their layers are discarded. Only the last stage is baked so our credentials won't be stored in a layer we push.

## Exercise

- Attempt to build the image using the original file. PS This is expected to fail. `docker build -t docker-deep-divd/ex6/original -f Dockerfile.original --progress=plain .`
- Create a better dockerfile that uses build arguments and environment variables to get the build to work `docker build -t docker-deep-divd/ex6/better -f Dockerfile.better --progress=plain --build-arg TOKEN=your-pat-token .`
- Run it to check it works `docker run --rm docker-deep-divd/ex6/better`
- Check the layers of the baked image by running `docker history docker-deep-divd/ex6/better`
- Create a multistage version to make sure the build arguments and tokens are not baked into the final image `docker build -t docker-deep-divd/ex6/multistage -f Dockerfile.multistage --progress=plain --build-arg TOKEN=your-pat-token .`
- Check the layers of the multistage baked image by running `docker history docker-deep-divd/ex6/multistage`
- Run it to check it works `docker run --rm docker-deep-divd/ex6/multistage`
  
Remember to record your results at each stage!

## References
https://docs.docker.com/build/guide/build-args/

https://docs.docker.com/build/building/variables/

https://docs.docker.com/reference/cli/docker/image/history/

https://docs.docker.com/build/building/multi-stage/

