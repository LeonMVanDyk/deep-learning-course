# Dockerfile for Host on the internal Allan Gray network

Some of the attendees may be experieicing the problems I have.

I have a powerful personal laptop, but it came with Windows Home.  Windows Home does not support Hypervisor, and therefore cannot run Docker for Windows.

## Possible Solutions

1. Install the (much) older Docker Toolkit, which creates a docker image on a headless version of Virtualbox.
    * We use Docker Toolbox on our build machine and have had problems with it.  Also, I'm not sure how compatible it is with the latest docker features.  I didn't want to fiddle around and waste time.
1. Install Ubuntu and dual boot.
    * Just got back from leave, don't have time by tonight.
1. Get things running on my work computer and Remote into that.
    * I've chosen this for now.  I'll probably go back to number 2 at some point, as I've been meaning to do that for a while.


## Modified Docker file    

The Dockerfile as supplied will not build on a computer on the Allan Gray internal network because Websense intercepts or HTTPS traffic.  You get this error:

````
RUN pip install --upgrade pip
 ---> Running in 89da8b59fb4a
Could not fetch URL https://pypi.python.org/simple/pip/: There was a problem confirming the ssl certificate: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:749)
````

I have modified the Dockerfile to work on an Allan Gray computer by specifying `--trusted-host`s.  I have also copied in the Allan Gray root certificate; it may not be needed to build, but may prevent issues further down the line.

