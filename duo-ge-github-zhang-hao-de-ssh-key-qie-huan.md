# 多个Github账号的SSH key切换

由于某些原因，需要在两个不同的GitHub账号上面提交代码。但是由于我只有一台电脑，所以就需要在这台电脑上生成两个ssh key，并且在提交代码的时候可以根据库的不同而自动切换。

## 如何生成key？

`$ ssh-keygen -t ed25519 -C "youremail@example.com"`

详见[新增 SSH 密钥到 GitHub 帐户](https://docs.github.com/cn/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

## 如何生成第二个key？

跟上面过程一样，注意不要重名即可。

假设第二个名字为id\_ed25519\_second

## 在.ssh/下创建config文件时的区别（关键）

第二个Host要用 第二个SSH key的名字.github.com

eg:\`Host id\_ed25519\_second.git.com'

其他相同。

## 测试配置是否正确

`$ ssh -T git@github.com` `$ ssh -T id_ed25519_second.git.com`

## 使得key可以自动切换（关键）

这里推荐直接从github上面重新克隆，对于第二个账户，在终端输入：

`$ git clone git@id_ed25519_second.git.com:username/repo.git`

作者：[itmyhome](https://blog.csdn.net/itmyhome1990)

