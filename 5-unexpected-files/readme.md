# Exercise 5 -  avoiding unexpected files in the bagging area

## Problem
Extra files can end up in the baked image which can:
- take up space (and time)
- expose how the image was built
- expose some development practices
- expose some secrets!

## Principle
Docker ignore files

## Detail
With lots of files to copy you don't want to list them separately, it's longwinded and brittle with changes.
The dockerfile copy instruction will use a `.dockerignore` file to skip copying files or folders we don't want, much like a .gitignore file

## Exercise
- Build the image using the Dockerfile.original file
- Run the image and record the ouput in your results
- Add a .dockerignore file with a listing of the files you think should be skipped
- Build the image again
- Run the image and record the ouput in your results
