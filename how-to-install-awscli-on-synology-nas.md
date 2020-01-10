# How to install awscli on Synology NAS

Model: Synology DS416play

My NAS is called `cherry`, and its IP address is defined in `/etc/hosts`.

SSH into the NAS and become root:

```
$ ssh samuel@cherry
samuel@cherry:~$ sudo su -
```

Check that `python` is installed. It should be there.

```
root@cherry:~# which python
/bin/python
root@cherry:~# python --version
Python 2.7.12
```

Install `pip`. By default, `pip` is installed into `.local/bin` but we'll move it to the global `/bin` so that all users can execute it.

```
root@cherry:~# curl -O https://bootstrap.pypa.io/get-pip.py
root@cherry:~# python get-pip.py --user
root@cherry:~# cp -i ~/.local/bin/* /bin/.
root@cherry:~# pip --version
pip 19.3.1 from /usr/local/lib/python2.7/site-packages/pip (python 2.7)
```

Install `awscli`. By default, `aws` and other scripts are installed into `.local/bin` but again, we'll move it to the global `/bin` so that all users can execute it.

```
root@cherry:~# pip install awscli --upgrade --user
root@cherry:~# cp -i ~/.local/bin/* /bin/.
root@cherry:~# aws --version
aws-cli/1.17.0 Python/2.7.12 Linux/3.10.105 botocore/1.14.0
```

