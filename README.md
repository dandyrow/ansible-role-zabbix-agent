Ansible Role - Zabbix Agent [![CI](https://github.com/dandyrow/ansible-role-zabbix-agent/actions/workflows/CI.yml/badge.svg?branch=master)](https://github.com/dandyrow/ansible-role-zabbix-agent/actions/workflows/CI.yml)
=========

An Ansible role that installs and configures the zabbix agent on Linux. Supports setting up agent for use with autoregistration and psk encryption.

Install from Ansible Galaxy using this command: `ansible-galaxy install dandyrow.zabbix_agent`

View Ansible Galaxy page [here](https://galaxy.ansible.com/dandyrow/zabbix_agent).

Role Variables
--------------

Variables listed below used to configure the Zabbix agent. For more detail on these values see the Zabbix documentation [here](https://www.zabbix.com/documentation/current/en/manual/appendix/config/zabbix_agentd).

### Required Variables

These variables are required for the role to run. The default value listed is set in `defaults/main.yml`.

`zbx_dir: [Default: /etc/zabbix]` - Change to the directory where Zabbix conf file is located.

`zbx_version: [Default: "6.2"]` - Change to desired version of Zabbix agent to install.

`zbx_agent_server: [Default: "127.0.0.1"]` - The IP address(s) and/or DNS name(s) of the Zabbix server or proxy which should passively monitor this agent.

`zbx_agent_server_active: [Default: "127.0.0.1"]` - The IP address(s) and/or DNS name(s) of the Zabbix server or proxy which should actively monitor this agent.

### Optional Variables

These variables can optionally be set to configure the Zabbix agent for your usecase.

`zbx_agent_hostname:` - Defines the hostname which the Zabbix agent will use for the host.

`zbx_agent_hostmetadata:` - Defines the host metadata used for during autoregistration to apply templates (optional).

`zbx_agent_hostinterface:` - Defines the host interface used during autoregistration to setup passive checks (optional).

`zbx_agent_pskid:` - Sets the PSK ID for the agent.

`zbx_agent_psk:` - Sets the PSK which will be stored in the file `{zbx_dir}/zabbix_agent.psk` on the host. The value of this must be longer than 32 characters and contain only letters and numbers otherwise the agent will fail to start.

Supported Platforms
-------------------

 - Ubuntu:
   - 22.04 Jammy
   - 20.04 Focal

 - Debian:
   - 11 Bullseye
   - 10 Buster
  
 - Archlinux

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - role: dandyrow.zabbix_agent
```

License
-------

GPL-3.0-only

Author Information
------------------

This role was created in 2022 by Daniel Lowry as part of a wider personal infrastructure as code project.
