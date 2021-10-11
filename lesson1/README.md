# Lesson 1: Running Docker and Dockerfiles

## Running an image
You can download pre-built images (mainly from dockerhub by default). To run and interactive terminal with an image: `docker run --rm -it ruby:2.7.4`. Once it finishes, you'll have an interactive terminal running `irb` in ruby 2.7.4 on a debian os.

### this command broken down
- `docker` is the docker cli. `docker --help` for more info
- `run` is the main Docker command that runs images. It runs a command in an image once, then exits.
