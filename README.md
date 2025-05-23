The included Vagrant environment can be used for testing. To install Vagrant with Homebrew:

```
brew install vagrant
```

Or you can get binaries [from Hashicorp](https://developer.hashicorp.com/vagrant/install).

You will also need a [Vagrant provider](https://developer.hashicorp.com/vagrant/docs/providers). I used [VirtualBox](https://www.virtualbox.org) while developing.

## Testing

Run these commands to provision the VM and connect:

```
vagrant up
vagrant ssh
```

On the VM run these commands:

```
sudo apt update
sudo apt install puppet-agent -y
```

Run the Puppet manifest:
```
cd /vagrant
sudo puppet apply -v jenkins.pp
```

Copy the setup wizard's admin password:

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Go to the Jenkins web ui:

http://localhost:8000

Paste in the admin password. You can now proceed with the setup wizard.

(We obviously would skip the setup wizard if we were pulling in an existing Jenkis config and plugins.)

## Cleanup

Back on the host, run:

```
vagrant destroy
```
