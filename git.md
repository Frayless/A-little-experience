Git存储流程：

<img width="1113" height="622" alt="image" src="https://github.com/user-attachments/assets/bdb187cb-528b-4310-8f44-f6b3c39fad38" />


Problem 1：ssh: connect to host gitlab.xxxx.com port 22: Connection timed out
solution:使用命令$ ssh -vT git@github.com，查看建立ssh连接的过程，发现DNS解析出的github ip是错误的，修改host文件，在C:\Windows\System32\drivers\etc\hosts，可能是由于开了VPN，修改完成后丝滑git

<img width="623" height="119" alt="image" src="https://github.com/user-attachments/assets/a265efc4-a8c5-4a7c-94eb-5d3bd1fa4009" />

查询DNS域名解析站点：http://www.ip33.com/dns.html
其他的解决方法,使用github的443端口，改用https协议($ git config --local -e)，我使用时均不生效

Problem2：使用git上传repositories使用的命令
```python
ssh-keygen -t rsa -C "youremail@example.com"  #生成SSH密钥
git config --global user.name = 'username'   #你gitlab登录的用户名
git config --global user.email = 'useremail'  #你的gitlab email
git init #在要上传的文件夹目录下
git remote add origin git@github.com:your-username/your-repository.git  #关联远程仓库
git remote -v  #查看远程仓库添加是否成功
git add .
git commit -m "Initial commit"
git branch -M main #确保主分支是main
git push -u origin main
```

Problem3:fatal:refusing to merge unrelated histories
```
git pull origin master --allow-unrelated-histories
```
fatal:Please enter a commit message to explain why this merge is necessary.
Solution:i->insert模式，ESC，输入":wq"+enter


Problem4: github文件上有白色箭头，无法点开。先删除其他目录下的.git文件（我记得cmake的时候也会同样报错？）
```
git rm --cached <file name>  #上述删除.git的文件名
git add .
git commit -m  "delete .git"
git push -u origin main
```
