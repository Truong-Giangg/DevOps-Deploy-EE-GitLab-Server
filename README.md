# DevOps-Deploy-EE-GitLab-Server
```bash
curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
sudo apt-get install gitlab-ee=15.11.3-ee.0
sed -i '3i\192.168.184.131 git.elroydevops.tech' /etc/hosts
sed -i 's/gitlab.example.com/git.elroydevops.tech/' /etc/gitlab/gitlab.rb
gitlab-ctl reconfigure
```
Add host to access on windows machine
File C:\Windows\System32\drivers\etc\hosts
Content: 192.168.184.131 git.elroydevops.tech
Username: root
Password:
```bash
cat /etc/gitlab/initial_root_password
```
