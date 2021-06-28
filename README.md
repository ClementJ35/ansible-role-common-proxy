# Ansible Role: Common Proxy

[![Ansible Role: Common Proxy](https://img.shields.io/ansible/role/55479?style=flat-square)](https://galaxy.ansible.com/clementj35/proxy)
[![Ansible Role: Common Proxy](https://img.shields.io/ansible/quality/55479?style=flat-square)](https://galaxy.ansible.com/clementj35/proxy)
[![Ansible Role: Common Proxy](https://img.shields.io/ansible/role/d/55479?style=flat-square)](https://galaxy.ansible.com/clementj35/proxy)

This role manages proxy settings of Linux systems.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: clementj35.proxy
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    common_proxy_apache2_configure: 'false'
    common_proxy_apt_configure: 'false'
    common_proxy_bash_configure: 'false'
    common_proxy_dnf_yum_configure: 'false'
    common_proxy_git_configure: 'false'
    common_proxy_profile_configure: 'false'
    common_proxy_wget_configure: 'false'
    common_proxy_systemd_configure: 'false'

Choose which parts of the system should be configured with a proxy.

    common_proxy_server: "127.0.0.1"

Configure which proxy server to use.

    common_proxy_port: "8080"

Configure the proxy port.

    common_proxy_exceptions:
      - 127.0.0.0/8
      - ::1

Configure proxy exceptions like e.g. local hosts.

    common_proxy_apt_proxy_server: "{{ common_proxy_server }}"
    common_proxy_apt_proxy_port: "{{ common_proxy_port }}"
    common_proxy_apt_proxy_username: ""
    common_proxy_apt_proxy_password: ""
    common_proxy_apt_proxy_exceptions: []

Configure proxy for APT or Aptitude. Set to blank to remove.

    common_proxy_dnf_proxy_server: "{{ common_proxy_server }}"
    common_proxy_dnf_proxy_port: "{{ common_proxy_port }}"
    common_proxy_dnf_proxy_username: ""
    common_proxy_dnf_proxy_password: ""

Configure YUM or DNF proxy. Set to blank to remove.

    common_proxy_apt_external_repositories: []
    common_proxy_apt_exceptions: []

Configure how to handle APT sources. This ensures that external repositories are fetched through the proxy but local repositories can bypass it.

## Dependencies

  - None

## OS Compatibility

This role ensures that it is not used against unsupported or untested operating systems by checking, if the right distribution name and major version number are present in a dedicated variable named like `<role-name>_stable_os`. You can find the variable in the role's default variable file at `defaults/main.yml`:

    role_stable_os:
      - Debian 11
      - Debian 10
      - Ubuntu 18
      - CentOS 7
      - Fedora 30

If the combination of distribution and major version number do not match the target system, the role will fail. To allow the role to work add the distribution name and major version name to that variable and you are good to go. But please test the new combination first!

Kudos to [HarryHarcourt](https://github.com/HarryHarcourt) for this idea!

## Example Playbook

    ---
    - name: "Run role."
      hosts: all
      become: yes
      roles:
        - clementj35.proxy

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

MIT

## Author Information

- [ClementJ35](https://github.com/ClementJ35/)

This role was created in 2020 by [clementj35](http://clementj35.de/).
