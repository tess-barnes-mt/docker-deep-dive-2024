# Exercise 2 - Choosing better base images

## Problem 
Image is too big; takes too long to download or spin up new containers

## Principle 
Using the right base image

## Detail 
The trick is build in ONLY what you need. Most docker images are based on a linux distribution.
There are many different flavours of linux os and combinations of primary langue the image is tailored for.

Fully featured < — > skinny

## Exercise
build the original dockerfile and note the size of the image it creates

```shell
docker build -t docker-deep-dive/ex2/original -f Dockerfile.original .
```

Find a better base image on dockerhub that still does what you need but will be smaller. 
Create an improved dockerfile in `Dockerfile.better` and build it to check the difference.
```shell
docker build -t docker-deep-dive/ex2/better -f Dockerfile.better .
```

Record the impact in `results.md`

Check in your changes, push and you're done!
