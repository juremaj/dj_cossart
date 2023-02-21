
# Installation

## Database  (Host)

To install datajoint i followed these instructions first:
https://tutorials.datajoint.org/setting-up/local-database.html

More specifically to install docker: 
https://docs.docker.com/engine/install/ubuntu/

Then I launched the MySQL/datajoint docker image available (with instructions) here:
https://github.com/datajoint/mysql-docker

I also checked if the mysql database was set up properly (also see in link above)


## Conda and Python (Client)

I set up a new conda env `dj_cossart` and installed datajoint there as described in documentation. For this I mostly followed the instructions here (but not fully, see below):
https://datajoint.com/docs/core/datajoint-python/0.14/getting-started/

IMPORTANT: I did two things differently than on the link. 

1) After datajoint I additionally installed `jupyter lab` using conda forge (this is important for later)
2) when configuring environment variables I changed the hostname (by default they want you to use `tutorial-db.datajoint.io`  or some other database that they host, but I set it to the local one) : `DJ_HOST=127.0.0.1`


# Our dj_cossart GitHub repo and testing

The final step I made to test it was to clone the github `dj_cossart` repo to the home directory on the 2p-server:

`git clone https://github.com/juremaj/dj_cossart`

cd'd into the directory and ran `jupyter lab`. Because of port-forwarding 8888 I just accessed jupyter lab through my computers localhost. Then I created a notebook with the test code they provide on the website (https://datajoint.com/docs/core/datajoint-python/0.14/getting-started/). I put in the default username and password (`root` and `simple`)And I got the following output that I was connected to the database:

```
[2023-02-14 17:46:38,828][INFO]: Connecting root@localhost:3306
[2023-02-14 17:46:38,952][INFO]: Connected root@localhost:3306
```
