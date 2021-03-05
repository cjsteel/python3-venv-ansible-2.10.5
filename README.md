# python3-venv-ansible-2.10.5

venv / provenance example

### Requirements

```shell
sudo apt update
sudo apt install python3-pip python3-venv
```

### Determine available versions of Ansible

This will give you a list of the versions of Ansible that can be installed.

```shell
pip3 install ansible==
```

In my case, the latest available released version is 3.0.0 but I want 2.10.5

### Create python3 virtual environment

```shell
python3 -m venv ~/.venv/ansible-2.10.5
```

### Activate environment

```shell
source ~/.venv/ansible-2.10.5/bin/activate
```

Notice that your command prompt is now prefixed with name of the active virtual environment.

In my case my new command prompt looks like this:

```shell
(ansible-2.10.5) csteel@p1u20:
```

### Testing and confirmation

You can confirm that the default python3 pip3 command is now the one in your new virtual Python environment using the `which` command:

```shell
which pip3
```

Example output:

```shell
/home/csteel/.venv/ansible-2.10.5/bin/pip3
```

### Install Ansible to the venv

Since the virtual environment is active we can now install our targeted version of Ansible to the target venv. This may take a while:

```shell
pip3 install ansible==2.10.5
```

### Ansible install Confirmation

We can confirm our installation using the `which` command using `ansible-galaxy`as our parameter:

```shell
which ansible-galaxy
```

perform a version check as well:

```shell
ansible-galaxy --version
ansible-playbook --version
```

**In my case the version information did not match the version I installed!** I installed version 2.10.5 but the version information showed 2.10.6. Hummmm, some investigating is required. 

Output example (Notice version different from ansible install version):

```shell
ansible-galaxy 2.10.6
  config file = None
  configured module search path = ['/home/initial/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/initial/.venv/ansible-2.10.6/lib/python3.8/site-packages/ansible
  executable location = /home/initial/.venv/ansible-2.10.5/bin/ansible-galaxy
  python version = 3.8.5 (default, Jul 28 2020, 12:59:40) [GCC 9.3.0]
```

pip freeze

Interesting, when I run `pip freeze` both **ansible** and **ansible-base** show the correct version.

```shell
(ansible-2.10.5) initial@ss01:~$ pip3 freeze > ~/.venv/ansible-2.10.5/requirements.txt
```

```shell
cat ~/.venv/ansible-2.10.5/requirements.txt
```

```shell
ansible==2.10.5
ansible-base==2.10.5
cffi==1.14.5
cryptography==3.4.6
Jinja2==2.11.3
MarkupSafe==1.1.1
packaging==20.9
pycparser==2.20
pyparsing==2.4.7
PyYAML==5.4.1
```

### Saving my venv to github

```shell
git@github.com:cjsteel/python3-venv-ansible-2.10.5.git
```

```shell
echo "# python3-venv-ansible-2.10.5" >> README.md
git init
git add README.md
git commit -m "initial commit"
git branch -M main
git remote add origin git@github.com:cjsteel/python3-venv-ansible-2.10.5.git
git push -u origin main
```





Copyright 2021 Christopher Steel (chris.steel@gmail.com) Apache License 2.0