# Exercise 4 - Understanding layers

## Problem
Rebuilding the image takes a long time

## Principle
Layers

## Detail
For each line (instruction) in the dockerfile, during build, a new interim container is spun up and the output is stored as a layer in the docker image.
Instructions that haven't changed can use a cache of the output on subsequent builds but only until the first instruction that implies changes, after that, all instructions are built from stratch.
So the order matters - what will change least often? what will change most often?

The number of instructions also matters, more instructions = more layers = bigger image that is slower to build.

## Exercise
- Build the original dockerfile, record the number of layers
- Build it again, record how many layers are pulled from cache
- Change the Rakefile to add a blank line
- Build the original dockerfile, record how many layers are pulled from cache

- Clear your docker build cache: `docker builder prune -a` (confirm with `y`)

- Create a better version of the docker file that considers which order layers should be in
- Build that and record the number of layers
- Build it again, record the number of layers pulled from cache

### Stretch
- Adapt your dockerfile.better to have fewer layers (hint, look at how files are copied)
- Record this in the results

### Super stretch
1. Adapt your dockerfile.better to have even fewer layers (hint, look at how apk and npm commands are used)
   - record the number of layers in the results
2. Building (or pulling) similar images can use cached layers too, but only if built on the same build context / machine
   - clean your build cache then 
   - build the original dockerfile for app1 and then app2 from exercise 3. 
   - see how many layers app2 build uses from the first one
