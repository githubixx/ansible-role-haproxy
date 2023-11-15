<!--
Copyright (C) 2023 Robert Wimmer
SPDX-License-Identifier: GPL-3.0-or-later
-->

ansible-role-haproxy
=====================

This Ansible role is used in my blog series [Kubernetes the not so hard way with Ansible](https://www.tauceti.blog/posts/kubernetes-the-not-so-hard-way-with-ansible-the-basics/). This role isn't intended to be a general purpose role for [haproxy](http://www.haproxy.org). It's only used to run on Kubernetes nodes, listen on `localhost` and forward requests for Kubernetes services like  `kube-scheduler`, `kube-controller-manager`, `kubelet` and `kube-proxy` to `kube-apiserver` and making all available Kubernetes API servers highly available for that services.

For this purpose this role only configures one frontend in TCP mode where the services mentioned above send their requests to and one backend with a list of all Kubernetes API servers available. To figure out which `kube-apiserver` are available the template expects a Ansible host group called `k8s_controller` (see [k8s_api_endpoint.cfg.j2](https://github.com/githubixx/ansible-role-haproxy/blob/master/templates/etc/haproxy/k8s_api_endpoint.cfg.j2).

This role currently only supports Ubuntu 22.04 and `haproxy` v2.4 which comes bundled with that Ubuntu version.

Requirements
------------

None

Changelog
---------

see [CHANGELOG.md](https://github.com/githubixx/ansible-role-haproxy/blob/master/CHANGELOG.md)

Role Variables
--------------

```yaml
# Address which haproxy service is listening for incoming requests
haproxy_frontend_bind_address: "127.0.0.1"

# Port which haproxy is listening for incoming requests
haproxy_frontend_port: "16443"

# Port where kube-apiserver is listening
haproxy_k8s_api_endpoint_port: "6443"
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - githubixx.haproxy
```

License
-------

[GNU General Public License v3.0 or later](https://spdx.org/licenses/GPL-3.0-or-later.html)

Author Information
------------------

[http://www.tauceti.blog](http://www.tauceti.blog)
