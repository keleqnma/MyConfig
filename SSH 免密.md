使用ssh-keygen生成密钥，将公钥文件上传至目标机器即可实现免密登陆，使用命令生成密钥:

    ssh-keygen -t rsa -C 'comment'

- -t rsa: 指定使用 rsa加密;

- -C: 添加备注, 备注会加到公钥文件最后，方便区分；

运行命令会有交互输入，全部使用默认值直接回车就行，默认会在家目录的.ssh/文件夹下生成四个文件:

- authorized_keys: 存放远程免密登录的公钥,主要通过这个文件记录远程机器的公钥。

- id_rsa: 生成的私钥文件

- id_rsa.pub: 生成的公钥文件

- known_hosts: 已知的主机公钥清单

然后通过ssh-copy-id命令复制本机公钥到目标机器上，运行命令:


    ssh-copy-id -i ~/.ssh/id_rsa.pub user_name@hostname


运行成功后即可使用ssh user_name@hostname 免密码登陆。

