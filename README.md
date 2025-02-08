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
# Config via GUI on gitlab (create user, group, branch...)
# Install gitlab-runner, connect runner bot to proj
```bash
curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash
sudo apt install gitlab-runner
gitlab-runer register
vi /etc/gitlab-runner/config.toml
nohup gitlab-runner run --working-directory /home/gitlab-runner/ --config /etc/gitlab-runner/config.toml --service gitlag-runner --user gitlab-runner 2>&1 &
```
Config sudo to let gitlab run command without password
```bash
visudo
```
or use
```bash
sed -i '21i\gitlab-runner ALL=(ALL) NOPASSWD: /bin/cp*' /etc/sudoers
sed -i '21i\gitlab-runner ALL=(ALL) NOPASSWD: /bin/pkill*' /etc/sudoers
sed -i '21i\gitlab-runner ALL=(ALL) NOPASSWD: /bin/chown*' /etc/sudoers
sed -i '21i\gitlab-runner ALL=(ALL) NOPASSWD: /bin/su shoeshop*' /etc/sudoers
```
