# Lesson 1: Running Docker and Dockerfiles

## Running an image
You can download pre-built images (mainly from dockerhub by default). To run and interactive terminal with an image: `docker run --rm -it ruby:2.7.4`. Once it finishes, you'll have an interactive terminal running `irb` in ruby 2.7.4 on a debian os.

### this command broken down
- `docker` is the docker cli. `docker --help` for more info
- `run` is the main Docker command that runs images. It runs a command in an image once, then exits. There are a LOT of flags and other configs you can pass in, but you usually don't run this command by hand with all of those configs present.
- `--rm` "Automatically removes the container when it exits" essentially this flag deletes this when it's done running. We'll usually --rm our containers to keep docker bloat to a minimum.
- `-it` are the combined `i` and `t` flags, which are `--interactive` and `--tty`. In short, if you want the container to be interactive and continue running, you'll need both of these flags.
- `ruby:2.7.4` is the `ruby` image with the `2.7.4` tag. Docker lets you tag hashes the same way you can tag hashed in github. The convention is `[THING]:[TAG](-VARIANT)` where usually the variant is what linux kernal it's on, like `ruby:2.7-buster`. Often you can add `-slim` to have minimal system packages installed as well, so `ruby:2.7.4-slim-buster` is ruby 2.7.4 installed on debian buster with very few dependencies (like `curl`, for example) installed.

### What you'll see when this runs
First you'll see something like this:
```
Unable to find image 'ruby:2.7.4' locally
2.7.4: Pulling from library/ruby
df5590a8898b: Already exists
705bb4cb554e: Already exists
519df5fceacd: Already exists
...
```

The hashes on the left are hashed build steps. These are the build steps, like `apt-get install ruby` that have been built and published so you don't need to run those steps locally. They are necessarily in order (although more recently you're able to have multiple build scripts).

After that you will see a ruby irb prompt. Note this is inside the container. Once you exit the container, it gets torn down.

## Docker ps

## Images are ephemeral: How to have them do something useful?
- volumes
