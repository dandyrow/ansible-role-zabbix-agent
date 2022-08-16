Ansible Role - Zabbix Agent [![CI](https://github.com/dandyrow/ansible-role-zabbix-agent/actions/workflows/CI.yml/badge.svg?branch=master)](https://github.com/dandyrow/ansible-role-zabbix-agent/actions/workflows/CI.yml)
=========

An Ansible role that installs and configures the zabbix agent on Linux.

Role Variables
--------------

Variables listed below used to configure the Zabbix agent alongside default value, see `default/main.yml`. For more detail on these values see the Zabbix documentation [here](https://www.zabbix.com/documentation/current/en/manual/appendix/config/zabbix_agentd):

`zbx_version: "6.2"` - Change to desired version of Zabbix agent to install. Used in `zabbix_repo` role to install corresponding repository to version of Zabbix to install.

`zbx_agent_server: "127.0.0.1"` - The IP address(s) and/or DNS name(s) of the Zabbix server or proxy which should passively monitor this agent.

`zbx_agent_server_active: "127.0.0.1"` - The IP address(s) and/or DNS name(s) of the Zabbix server or proxy which should actively monitor this agent.

`zbx_agent_hostmetadata: ""` - Defines the host metadata used for during autoregistration to apply templates (optional).

`zbx_agent_hostinterface: ""` - Defines the host interface used during autoregistration to setup passive checks (optional).

`zbx_pskid: ""` - Sets the PSK ID for the agent.

`zbx_psk: ""` - Sets the PSK which will be stored in the file `/etc/zabbix/zabbix_agent.psk` on the host. The value of this must be longer than 32 characters and contain only letters and numbers.

Dependencies
------------

This role depends on `dandyrow.zabbix_repo`. This role installs the repo for the version corresponding to the value set in `zbx_version`.

Supported Platforms
-------------------

 - Ubuntu:
   - 22.04 Jammy
   - 20.04 Focal

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - dandyrow.zabbix_repo
    - dandyrow.zabbix_agent
```

License
-------

GPL-3.0-only

Author Information
------------------

This role was created in 2022 by Daniel Lowry as part of a wider personal infrastructure as code project.