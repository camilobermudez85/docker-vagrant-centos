## vagrant-centos (tagged)

Docker image derived from smerrill/vagrant-centos with slight modifications
to provide different centOS image versions as tags. Below is the README
from the original project, for more info go to the project page.

WARNING: Any side effects due to the centOS version variations have not been thoroughly evaluated,
use it under your own risk, or better yet, help me improve it.

## vagrant-centos

This is a _monolithic_ Docker image (e.g. it runs /sbin/init) that runs sshd.
Because of this, it is possible to use all Vagrant provisioners with it.

This is not really the way Docker is meant to be used, but it does result in
configuration management testing with almost no overhead that can be used on a
wide variety of cloud platforms.

### Sample Vagrantfile
(Replace {tag} with the appropriate version.)

    Vagrant.configure("2") do |config|
      config.vm.provider "docker" do |d, override|
        d.image = "camilobermudez85/vagrant-centos:{tag}"
        d.has_ssh = true

        # This is needed if you have non-Docker provisioners in the Vagrantfile.
        override.vm.box = nil

        # Ensure Vagrant knows the SSH port. See
        # https://github.com/mitchellh/vagrant/issues/3772.
        override.ssh.port = 22
      end
    end


#### Caveats

- The container does not (and cannot) run udev.
  - This may cause services like Avahi to fail to start.
- The container may not load kernel modules. This affect iptables.
