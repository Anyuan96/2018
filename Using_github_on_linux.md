Using github in Linux
1. install Git:
	>> apt-get install git
	set usercofig
	>> git config --global user.name ""
	>> git config --global user.email ""
2. setup SSH service
	install SSH
	>> apt-get install ssh
	view the status of SSH service
	>> ps -e | grep sshd
3. Procedure SSH KEY
	>> ssh-keygen -t rsa -C ""
4. Copy SSH KEY
	>> gedit ~/.ssh/id_rsa.pub
5. New SSH key on Github.com
6. Test the connection to Github.com
	>> ssh -T git@github.com
	When Permission denied
	>> eval "($ssh-agent -s)"
	>> ssh-add
	When -agent：未找到命令
	>> ssh-add
7. Clone repo to local with SSH
	>>git clone ________
	view remote vision
	>>git remote -v
8. Upload new file
	>> git add ___
	>> git commit -m ""
	>> git push origin master
9. Renew local repo.
	>>git pull
