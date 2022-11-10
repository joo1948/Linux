**[보내는쪽]**

`$ ssh-keygen`
``` shell
  Generating public/private rsa key pair.
  Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa):
  Created directory '/home/ubuntu/.ssh'.
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:
  Your identification has been saved in /home/ubuntu/.ssh/id_rsa.
  Your public key has been saved in /home/ubuntu/.ssh/id_rsa.pub.
  The key fingerprint is:
  SHA256:53PUzAOH2HaTwrMFoo3HZ8WWi7YZfUERYGJ4XoPWcB8 ubuntu@c0b48953fe5c
  The key's randomart image is:
  +---[RSA 2048]----+
  |          o+==+Eo|
  |         *.O+B=o.|
  |        o O %+Bo.|
  |         . =+%o..|
  |        S ..o+=. |
  |         o .o  . |
  |          o .    |
  |           o     |
  |                 |
  +----[SHA256]-----+
   
```
`$ ssh-keygen -t rsa`

`$ scp $HOME/.ssh/id_rsa.pub 계정@접속할 도메인:id_rsa.pub`

**[받는쪽]**

`$ ssh-keygen`

`$ $HOME/.ssh/에 authorized_keys 만들기`

**[보내는쪽]**

`$ ssh-copy-id 계정@접속할 도메인`

`$ ssh계정@접속할 도메인`
