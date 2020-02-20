Download docker:
> https://hub.docker.com/editions/community/docker-ce-desktop-mac

# Flask/Docker App Setup
### From Scratch:
`cd <your/dir>`

`mkdir flask-docker`

`cd flask-docker`

`touch requirements.txt`

`mkvirtualenv dockerpresentation`

`workon dockerpresentation`

`pip install flask`

`pip freeze > requirements.txt`

`touch Dockerfile`

`code Dockerfile`
### Clone This Repo
`cd <your/dir>`

`git clone git@github.com:fjordski/docker-flask-demo.git`

`mkvirtualenv dockerpresentation`

`workon dockerpresentation`

`pip install -r requirements.txt`

# Overview of Docker and What Problem It Solves
Docker was the follow up to Virtual Machines. Maybe some of you are familiar with Virtual Machines, they're a lot of fun, and certainly serve a purpose.
For example, do you have a mac but you need to test a bug on Internet Explorer? You aren't launching IE on the mac soooo what do you do? Launch a VM with
a Windows operating system! This gives you sort of a Russian Doll scenario with a computer inside a computer (which could also have yet another..and so on).
What's the problem with VM's then? They're MASSIVE and huge resource hogs. You are literally spinning up an entirely new computer, complete with full OS and
lots of other things you most likely don't need for your use case. Truth be told, for devs, you most likely just need to launch a single process or application, containers do exactly that. Docker and Kubernetes are the two leaders in container service providers but Docker has taken the
lead in terms of ease of use and learning curve.


# VMs vs Containers
# VM
- A VM utilizes its own BIOS, software network adapters (in turn these use the host’s adapters),
disk storage (a file on the host machine), a CPU, RAM, and a complete OS. During setup, you determine
how many of the host’s cores and how much of the host’s memory you want the VM to access. When the VM boots,
it goes through the entire boot process (just like any other hardware device). VMs often boot faster
than comparable hardware.


# Containers
- Instead of abstracting the hardware, containers abstract the OS. Each container technology features an explicit purpose, limiting the scope of the technology. Docker’s runs Linux, whereas Citrix’s XenApp runs Windows Server. Every container shares the exact same OS, reducing the overhead to the host system. Recall each VM runs its own copy of the OS, adding overhead for each instance.
- Containers exist to run a single application.


# How Does Docker Make My Life Easier?
- You know our massive document called 'Getting started on OSX'? Or even the install steps listed at the beginning of this document? Docker eliminates that.
  - Could potentially just be as simple as `docker-compose up -d --build`
- it fixes the "well it works on MY machine" problem
- makes local dev and production identical, perfect for development
- Docker enables you to build a container image and use that same image
across every step of the deployment process.
- Thusly speeds up deployment


# Basic Docker command
> https://docs.docker.com/engine/reference/builder/#from

FROM -> Example -> FROM (image-name)
- Pulls down a base image from Docker registry
- (explain base images, Docker registry etc)

WORKDIR -> Example -> WORKDIR (/path/to/workdir)
- Used to define the working directory of a Docker container at any given time.
- any other Docker command will be ran in the directory set by WORKDIR

ADD -> Example -> ADD (src) (dest)
- copies new files, directories or remote file URLs from <src> and
adds them to the filesystem of the image at the path <dest>

CMD -> Example -> CMD ["python", "app.py"]
- executes a command via provided list


### Build image
`docker build -t flask-tutorial:latest .`

### Run image
`docker run -d -p 5000:5000 flask-tutorial`

### See That Container Is Running
`docker container ls`

### Kill Container
`docker kill <hash>`

### Prove Localhost Isn't Available

### Rrun Without Daemon Mode (daemon just means a process that runs in the background)
`docker run -p 5000:5000 flask-tutorial`


