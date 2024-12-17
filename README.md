# ansible_old_mac

Ansible playbook for old macs...

## General Info

Initially, I wouldn't really have distinguished between old/new Mac but I just dove into using Homebrew and it was taking hours. Had I done a little research prior I would have noticed it isn't even supported anymore on Monterey. So I modified my approach to use MacPorts which has worked just fine. It isn't as hip as HomeBrew, I guess, but works on older macs easily so maybe its way cooler.

**NOTE:** The version of ruby I am using is right now old and particular to a project I am working on. You probably want something newer. You can modify the variable in the all.yml file to change the ruby version.

## Instructions

Basically, fork or clone this repository then modify and run.

Below is my rebuild process.

1. Refresh installation of Mac using Command R during boot. Takes a couple of hours.
2. Update OS. Another 45 minutes with reboot.
3. [optional] Change hostname
4. [optional] Update DNS to the internal DNS server for local name resolution
5. [optional] Add the new hostname to the local DNS server
6. [optional] Set a static IP via reserved DHCP.
7. Install x-tools. Another 20 minutes.
   
```bash
xcode-select --install
```

8. Download then install MacPorts. You can download from [here](https://www.macports.org/install.php). Click on **your version of OSX**
9. Download and install Python for mac. You can get [here](https://www.python.org/downloads/)
10. Install Python which also installs `pip`. Make sure to click on the **Install Certificates.command** when the installation completes.
11. Upgrade pip

```bash
pip3 install --upgrade pip
```

12. Install Ansible on the Macbook

```bash
pip3 install ansible
```

13. Clone or fork this repo.
14. Modify the **hosts** file to the hostname of your Mac. You can check by running the `hostname` command.
15. Modify the **group_vars/all.yml** to your username. NOTE: It is expected the username is already created on the Mac as this is required during installation/rebuild.
16. Run playbook from Macbook. It is meant to be run using **ansible-pull** from your git repo. It needs to be **run using sudo**. Takes about an hour to complete on my MacBook.


```bash
# If a public repo then run the following from the Mac. Replace with your values.
sudo ansible-pull -U https://github.com/<Your Account>/your_git.git
```

```bash
# If a private repo then run the following from the Mac. Replace with your values.
export OAUTH_TOKEN="Insert your github oauth token here"
ansible-pull -U https://oauth2:$OAUTH_TOKEN@github.com/ProServicesStorage/ansible_configs.git
```
