# Ansible

This is my [Ansible](http://docs.ansible.com/) repo.  [There are many like it, but this one is mine.](https://youtu.be/2G551KpNnA0)

Ansible is a great tool to wrap [mostly] idempotent ad-hoc tasks into code with minimal effort.  This repository is contains the meat I have used in a _personal_ capacity to get things done.  

These playbooks are very opinionated.  I tend to prefer CentOS 6.x, and these playbooks reflect that.

Also I eschew pain where it is unnecessary, hence the gtfo of `selinux` and `iptables`.  [Sorry](https://youtu.be/bFEoMO0pc7k).

## Use

This originally started as the following:
> I have a freshly kickstarted host sitting on the wire with root passwd login ... 
> how can I lay a [Plex](https://plex.tv/) config on this thing as quickly, data-driven, and idempotently as possible?

Hence this repo.

You can let these roles loose ad-hoc via an: `ansible-playbook -u root -k -i 192.168.1.10, main.yml`

I have tried to make things as both modular and data-driven as possible so as to promote reuse.

## Roles

| Role             | Description 
-------------------|-----------
**selinux**        | Mic drops `selinux` and reboots your host given the change.
**firewall**       | Also drops `iptables` to the floor.
**epel**           | Does the needful to setup [EPEL](https://fedoraproject.org/wiki/EPEL) as a `yum` repo.
**base-bootstrap** | Wraps up errata which isnt encompassed by other playbooks, mostly just `yum` packages.
**git-client**     | Sets up a local `git` client, including caching `github.com` keys for `root`.
**runit**          | Sets up a [`runit`](http://smarden.org/runit/) instance using [Ian Meyer's](https://github.com/imeyer) awesome [packagecloud.io runit repo](https://packagecloud.io/imeyer/runit).
**hostname**       | Sets up a **very** opinionated hostname. :trollface:
**mount**          | Bootstraps mounting my [Drobo](http://www.drobo.com/) over CIFS
**plex**           | Pulls down a versioned [PlexPass](https://plex.tv/) RPM.
**sabnzbd**        | Clones a versioned tag from GitHub of [SABnzbd](http://sabnzbd.org/) code.  Depends upon runit role.
**sickbeard**      | Also clones a versioned tag from GitHub of [Sick-Beard](http://sickbeard.com/) code.  Leveraged runit role.
**couchpotato**    | You guessed it. This role clones a versioned tag from GitHub of [CouchPotato code](https://couchpota.to/).  Supported via runit.

# License and Authors

* Author: Nick Silkey <nick@silkey.org>

```text
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
```
