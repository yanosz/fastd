fastd
=========

This role installs and configures fastd, the Fast and Secure Tunnelling Daemon.

It is used to provide an Internet-Exit for VPN nodes.

Please note, that neither any dhcp, nor any radvd configuration is provided by this role - it's the fastd-Stuff only


Role Variables
--------------

See: http://fastd.readthedocs.org/en/v16/manual/config.html

    fastd_bind: (List of bindings - default: '0.0.0.0:10000'
    fastd_drop_capabilities: (default: yes)
    fastd_forward: (default: no)
    fastd_hide_ip: (default: yes)
    fastd_hide_mac: (default: yes)
    fastd_interface: name of the VPN-interface (default: fastd-exit)
    fastd_syslog_level: (default: info)
    fastd_methods: see http://fastd.readthedocs.org/en/v16/manual/methods.html
    - 'salsa2012+umac' (default)
    - 'null' (default)
    fastd_mode: (default: tap)
    fastd_mtu: (default: 1426)
    fastd_on_pre_up:
      mode: sync/async (default: sync)
      command:
    fastd_on_up:
      mode: sync/async (default: sync)
      command:
    fastd_on_down:
      mode: sync/async (default: sync)
      command:
    fastd_on_post_down:
      mode: sync/async (default: sync)
      command:
    fastd_on_connect:
      mode: sync/async (default: async)
      command:
    fastd_on_establish:
      mode: sync/async (default: async)
      command:
    fastd_on_disestablish:
      mode: sync/async (default: async)
      command:
    fastd_on_verify:
      mode: sync/async (default: async)
      command:
    fastd_pmtu: (default: auto)
    fastd_repository_key: (default: '6664E7BDA6B669881EC52E7516EF3F64CB201D9C')
    fastd_secret: fastd private key (default: will be generated)
    fastd_secure_handshakes: (default: yes)
    fastd_status_socket: (default: '/tmp/fastd_status')
    pgp_keyserver: (default: 'pool.sks-keyservers.net')


Example Playbook
-------------------

```
- hosts: servers
  vars:
    fastd_bind:
    - any port 10000 interface "eth2"
    fastd_on_verify:
      command: true
      mode: async
  roles:
    - fastd-exit
```

License
-------

GPLv3

