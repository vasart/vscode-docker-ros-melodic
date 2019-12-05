# Visual Studio Code remote development in a container for ROS Melodic
This repo lets you develop code for ROS Melodic in a docker container. Workspace files will be mounted into the docker from the local file system. You then work with VS Code as if everything were running locally on your machine, except now they are isolated inside a container.

This gives you a list of benefits:
* Consistent and easily reproducible development environment and toolchain.
* Host OS could be different from Ubuntu 18.04 Bionic Beaver.
* No worrying about impacting your local setup.

## Install Visual Studio Code from Microsoft repo
```
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /tmp/microsoft.gpg
sudo install -o root -g root -m 644 /tmp/microsoft.gpg /etc/apt/trusted.gpg.d/
echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
sudo apt-get update
sudo apt-get install --yes code
```

## Install remote development in a container extension
```
code --install-extension ms-vscode-remote.remote-containers
```

Then launch VS Code, open the folder containing this repo, say yes to open remote container.

If you run some code make sure to use `gui:=false` to prevent RQT, RViz, and Gazebo from running
```
roslaunch my_package run.launch gui:=false
```

Enjoy!
