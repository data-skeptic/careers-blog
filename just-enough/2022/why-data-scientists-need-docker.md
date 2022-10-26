> "I don't know what to tell you, it works on my computer."

The quote above was an all to frequently heard platitude in many software development groups prior to 
advancements in software tooling such ad Docker.

Docker is a software tool that enables users to run containers.  Containers were introduced to solve a number of 
problems in the packaging and deployment of software.  Everyone's kitchen is set up the owner's unique way.  In 
software, it's much the same.  No programmer starts from scratch.  In all modern software, developers leverage 
libraries written by people they've never met or heard of.  The end result is a software application bundled 
together from many independent sources.  The maintainers of those imported libraries can change the code at any 
time, typically improving their library, but not always!

Modern programming languages offer package management tools (e.g. pip for python) which assist programmers in 
defining the exact set of libraries and versions should be used in the compilation process.  Were this the only 
problem developers faced trying to get software to run on someone else's machine, docker might never have been 
invented.

Getting a software application written on a developer's local machine to run on a server demands more 
configuration and setup than just package management.  First and foremost is the operating system.  The majority 
of software engineers use Mac or Windows, with the minority using Linux on their local computer.  Inversely, 
Linux is the most popular operating system for servers.  Even within Linux, one can find competing flavors.  Top 
of mind, I've had to work with Ubuntu, Debian, AWS Alpine, Red Hat, FreeBSD, and several others throughout my 
career.  Each is painfully unique compared to the others.

Beyond the operating system and the programming language, many applications leverage popular "utility" software 
such as FFMEG (manipulate video), ImageMagic (manipulate images), or Pandoc (render documents) in their 
operations.  These need to be installed in essentially the same way on the server for your software to be able to 
run them.  Security settings and networking configurations are two of many other reasons by taking a precise 
snapshot that defines the full state of a particular computer and everything installed on it is an incredibly 
difficult problem.

Unlike the package management tools that essentially solved this for software library management, the diversity 
of possible differences between two machines left little hope for a direct attack on this problem.  Instead, 
docker was introduced to great fanfare.  Docker took an entirely different approach, inspired by the large, 
standard shipping containers you see on cargo ships and attached to trucks.  Those shipping containers may have 
cargo as diverse as nuclear waste, farm equipment, or beanie babies.  Once the doors are closed and locked, every 
shipping container is essentially the same.  It can be hitched, lifted, stacked, and managed as a fungible, 
standard box with little or no concern for the contents themselves.

Taking inspiration from shipping containers, docker gave us software containers.  As with their namesake, once 
the container door is closed, operations engineers (often called DevOps) should have little or no trouble "taking 
it from there".  While teamwork is often required, practitioners seem to agree that we should treat machines like 
cattle, not like pets.  By taking the time to implement your solution inside a Docker container, you enable 
another type of software professional who may not have your background to handle the operations and management of 
your production ready code without having to burden them on the particulars.

## Getting Started

First, install docker on your local machine following the [official 
tutorial](https://docs.docker.com/get-docker/).

Second, define a Dockerfile.  An example of one is below.  For your first one, your best bet is to Google around 
for a project similar to your needs which you can use as a starting point.  Search at 
[https://hub.docker.com](https://hub.docker.com/) for inspiration.

Below is an minimalist pseudocode Dockerfile.  All Dockerfiles start with `FROM [something]`.  Here I've choosen 
Ubuntu because I find it's a friendly version of Linux that less experienced colleagues learn faster than 
alternatives.  After the first line, there are a variety of commands with `RUN` and `CMD` being the two I use the 
vast majority of the time.  The purpose of `RUN` is intuitive and self explanatory - execute the exact command 
provided on the machine image that is being built.  You'll want to have many `RUN` statements that set up all 
your dependencies and configure things to be just right.  You'll likely need to `COPY` and `ADD` a few things 
along the way.

	FROM ubuntu:22.04

	COPY requirements.txt /
	RUN apt-get install -r requirements.txt
	RUN pip install -r requirements
	ADD my_app /app

	CMD ["/app/start.sh"]

The `CMD` command differs from `RUN` in that it happens when the container is executed, not when the container is 
built.  A Dockerfile is nothing more than a basic text file with a nice recipe in it.  That text file needs to be 
"built" using a command like this one:

```
docker build -t my-app-v1 .
```

The `docker` cli app should be installed on your machine via the setup described above.  That app has several 
functions of which `build` is being used here to build an *image* from the Dockerfile.  The `-t my-app-v1` adds a 
tag to this image and the `.` indicates that the current directory is the place where the Dockerfile is located, 
so be in the root of your project when you execute this.

The resulting docker image can be thought of as a brand new computer ready to be unboxed.  To boot it up, we 
execute a command such as:

```
docker run -it my-app-v1
```

The `run` function here (different from the `RUN` in the Dockerfile) tells docker to run the image that was 
built.  Here the `-it` switch indicates that you wish to run an *interactive terminal* (i.e. have a command line) 
from which you can interact with the machine.  When getting a project set up, you often wan to do that so that I 
can manually execute installation steps one by one and observe their outputs.  With each successful install, I 
typically add that line to the Dockerfile so that it's automated on the next build.

Even on a mature image, I sometimes need to "go inside" and do some debugging.  For that, I need the `-it` flag 
as well.  When running your docker image in production, you definitely don't need or want an interative terminal.  
Instead, the `-d` for daemon mode is preferred.  An example with some other niceties is provided below.

	docker run -d \
	  --env-file .env \
	  -p 3000:3000 \
	  my-app-v1

In addition to demonstrating the `-d` option, I've snuck in two further enhancements I use often.  The 
`--env-file` allows me to tell docker where to get environment variables from.  On a production server, you 
should set those directly on the machine.  But in the case of docker, I wouldn't want my local environment 
variables to be inherited by my docker image.  Instead, I use the same `.env` file I have for local development.

The `-p` flag is for port mapping.  In this case, I'm asking to intercept traffic for my `localhost` that is on 
port 3000, and to route that to port 3000 on the image.  That way, if my docker image is serving up a web app of 
any kind (on port 3000), then I can load that in my browser and interact with the docker container via the web as 
if it were running on a server.

When you `docker run` an image, all the `RUN` commands have already been run and are baked into the image.  the 
`CMD` commands, on the other hand, are going to be execute at the time you initialize a new container from the 
image.  Typically a `CMD` executes a batch file or other simple command to launch a web application inside the 
newly minted docker container.

As mentioned, I sometimes need to debug something in a container that is already mature.  In that case, I don't 
want to have to change the Dockerfile to "hack" my way into it.  Instead, when I do `docker run` I switch `-d` 
for `-it` and I add the option `--entrypoint "/bin/bash"`, which overrides any `CMD` and instead gives me a 
terminal that I can us.

## Answering the question

Data scientists need Docker because it's a ubiquitous standard from which they benefit in three key ways:

1) Less problems

2) More control

3) Greater scalability

As a data scientist, you're going to be constantly asked to learn new tools and techniques.  No one person can 
learn all the things, so you have to prioritize the solutions most beneficial to your own career.  That's 
personalized advice I can't uniquely give in a static blog post, but playing the odds, it stands to reason that 
in your career as a data scientist, you'll be asked to use docker.  Having first hand experience with it should 
give you the confidence to add it to your resume, which might be one of the key requirements that gets you the 
interview.  With docker, uour work will be easier and less filled with annoying technical details to fix so that 
you can focus on the problem you're actually trying to solve.


