Problem 1：ssh: connect to host gitlab.xxxx.com port 22: Connection timed out
solution:使用命令$ ssh -vT git@github.com，查看建立ssh连接的过程，发现DNS解析出的github ip是错误的，修改host文件，在C:\Windows\System32\drivers\etc\hosts，可能是由于开了VPN，修改完成后丝滑git

<img width="623" height="119" alt="image" src="https://github.com/user-attachments/assets/a265efc4-a8c5-4a7c-94eb-5d3bd1fa4009" />

查询DNS域名解析站点：http://www.ip33.com/dns.html

