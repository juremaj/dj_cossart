
# Installation

## 1) Database  (Host)

To install datajoint i followed these instructions first:
https://tutorials.datajoint.org/setting-up/local-database.html

More specifically to install docker: 
https://docs.docker.com/engine/install/ubuntu/

Then I launched the MySQL/datajoint docker image available (with instructions) here:
https://github.com/datajoint/mysql-docker

I also checked if the mysql database was set up properly (also see in link above)


## 2) Conda and Python (Client)

I set up a new conda env `dj_cossart` and installed datajoint there as described in documentation. For this I mostly followed the instructions here (but not fully, see below):
https://datajoint.com/docs/core/datajoint-python/0.14/getting-started/

IMPORTANT: I did two things differently than on the link. 

1) After datajoint I additionally installed `jupyter lab` using conda forge (this is important for later)
2) when configuring environment variables I changed the hostname (by default they want you to use `tutorial-db.datajoint.io`  or some other database that they host, but I set it to the local one) : `DJ_HOST=127.0.0.1`


## 3) Our dj_cossart GitHub repo and testing

The final step I made to test it was to clone the github `dj_cossart` repo to the home directory on the 2p-server:

`git clone https://github.com/juremaj/dj_cossart`

cd'd into the directory and ran `jupyter lab`. Because of port-forwarding 8888 I just accessed jupyter lab through my computers localhost. Then I created a notebook with the test code they provide on the website (https://datajoint.com/docs/core/datajoint-python/0.14/getting-started/). I put in the default username and password (`root` and `simple`)And I got the following output that I was connected to the database:

```
[2023-02-14 17:46:38,828][INFO]: Connecting root@localhost:3306
[2023-02-14 17:46:38,952][INFO]: Connected root@localhost:3306
```

## 4) Setting up environment
I think for this we can simply clone the calcium imaging workflow ([link](https://github.com/datajoint/workflow-calcium-imaging)) and install it from the `dj_cossart` conda environment locally by using:

`pip install -e .`

Another dependency is `jupyter lab` anything else?

## 5) Configuring database users and permissions

see:
https://docs.datajoint.org/python/admin/3-accounts.html

# Launching

## After server restart
If the server is restarted we need to re-launch the docker container. To do this we navigate to `~/mysql-docker` where the image from above is stored. We can then activate the container with:

`sudo docker-compose up -d`

we can then test if the sql database is running by trying to sign in (with the default `root`/`simple` user):

`mysql -h 127.0.0.1 -u root -p`

we can then follow the normal steps as we would if the server was not restarted (see just below).

## Regular use (without server restart)

We first need to navigate to the folder of this repository and activate the conda environment:

```
cd ~/dj_cossart
conda activate dj_cossart
```

And from here we can just use VSCode or launch `jupyter lab`...
