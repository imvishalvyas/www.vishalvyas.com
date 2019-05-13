### Generate a pair key on ssh server : 
```
ssh-keygen -t rsa
```
```
Generating public/private rsa key pair.

Enter file in which to save the key (/root/.ssh/id_rsa):

Enter passphrase (empty for no passphrase):

Enter same passphrase again:

Your identification has been saved in /root/.ssh/id_rsa.

Your public key has been saved in /root/.ssh/id_rsa.pub.

The key fingerprint is:

SHA256:1Je7TcRc58MxO5C6qBJ6qy44L+nxT8xHSXfBHUpNy48 root@slave1

The key's randomart image is:

+---[RSA 2048]----+

|          .o++ooo|

|         ...+B+o=|

|       ....o+o+=.|

|      ..o .o oo o|

|       oS . oE.. |

|    o..  . . +   |

|.o  .+...   . .  |

|=.o..o..         |

|.=+++oo          |

+----[SHA256]-----+
```




### Copy key to client machine : 
```
ssh-copy-id -i id_rsa.pub root@10.80.253.12
```


it will ask you the password.





Now you can login to client machine without password.
```
root@master:~# ssh 10.80.253.12
```
```
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.10.0-28-generic x86_64)


 * Documentation:  https://help.ubuntu.com

 * Management:     https://landscape.canonical.com

 * Support:        https://ubuntu.com/advantage


413 packages can be updated.

226 updates are security updates.


Last login: Wed May  2 13:58:36 2018 from 10.80.253.11
```
