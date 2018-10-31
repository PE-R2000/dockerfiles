# (Please note that the original software licenses still apply)

# Using the PopART image in Linux
Please note that the following instructions must be executed in Linux environments only.

You should adapt and run the following command: `docker run --rm --env QT_X11_NO_MITSHM=1 -ti -e USERID=$UID -e USER=$USER -e DISPLAY=$DISPLAY -v /var/db:/var/db:Z -v /tmp/.X11-unix:/tmp/.X11-unix -v $HOME/.Xauthority:/home/developer/.Xauthority -v "/your/data/dir:/data" pegi3s/popart`

If the above command fails, try running `xhost +` first. In this command, you should replace:
- `/your/data/dir` to point to the directory that you want to have available at `PopART`. 

Running this command opens the [PopART](http://popart.otago.ac.nz/index.shtml) Graphical User Interface. Your data directory will be available through the file browser at `/data`.
