# networkit-demo

## Installing networkit and requirements
https://networkit.iti.kit.edu/documentation/
```
sudo apt-get install python3-numpy python3-scipy python3-matplotlib python3-pandas python3-pip
sudo pip3 install jupyter networkx tabulate cython
sudo pip3 install networkit
```

## Running in a Vagrant virtual machine
Installing networkit on Mac OS, I encountered problems related to the C++ compiler. If you have a Mac, I recommend using Vagrant to install NetworKit on an Ubuntu virtual machine. https://www.vagrantup.com/docs/
```
vagrant init ubuntu/trusty64
```
This will create a file called `Vagrantfile`. Add the following lines to `Vagrantfile`. Port forwarding enables you to access Jupyter notebooks running on port 8888 of the guest (virtual) machine from localhost:8889 on the host (e.g. Mac). The default memory allocation of 512 Mb is insufficient for installing networkit.
```
config.vm.network "forwarded_port", guest: 8888, host: 8889
config.vm.provider "virtualbox" do |vb|
   # Customize the amount of memory on the VM:
   vb.memory = "4096"
end
```
Start the virtual machine.
```
vagrant up
vagrant ssh
```
Now you are in the Ubuntu vm. Install networkit and its dependencies as above.

Running a Jupyter notebook in the synced folder of the virtual machine.
```
cd /vagrant
jupyter notebook --ip=0.0.0.0 --no-browser
```
## Getting data for the demo
The demo notebook uses the `wikispedia-paths-and-graph` dataset available from http://snap.stanford.edu/data/wikispeedia.html.

Download `wikispeedia_paths-and-graph.tar.gz` and unzip it into the same directory as `networkit-demo.ipynb`.
