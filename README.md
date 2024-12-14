# ansible_old_mac
Ansible playbook for old macs...

## General Info

I having been playing around with Ansible lately and one of the use cases I have found is for a Mac rebuild.

I am currently testing with MacOS Monterey on a MacBook 12-inch, Early 2016.

Initially, I wouldn't really have distinguished between old/new Mac but I just dove into using Homebrew and it was taking hours. Had a done a little research prior I would have noticed it isn't even supported anymore on Monterey. So I modified my approach to use MacPorts which has worked just fine. It isn't as hip as HomeBrew I guess, but works so who cares. Also, VS Code is no longer supported on Monterey

## Instructions

Unfortunately the overall process with a Mac is more manual. Some steps can still be automated!

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

8. Download then install MacPorts. You can download from [here](https://www.macports.org/install.php). Click on your version of OSX 
9. Download and install Python for mac. You can get [here](https://www.python.org/downloads/)
10. Install Python which also installs `pip`. Make sure to click on the **Install Certificates.command" when the installation completes.
11. Upgrade pip

```bash
pip3 install --upgrade pip
```

12. Install Ansible on the Macbook

```bash
pip3 install ansible
```

13. Modify the **hosts** file to the hostname of your Mac. You can check by running the `hostname` command.
14. Modify the **group_vars/all.yml** to your username. NOTE: It is expected the username is already created on the Mac as this is required during installation/rebuild.
15. Run playbook from Macbook. Takes about an hour to complete on my MacBook.

```bash
sudo ansible-pull -U https://github.com/ProServicesStorage/ansible_old_mac.git
```