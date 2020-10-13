# motd_news

This role enables or disables motd_news on ubuntu systems.

Ubuntu's motd_news unfortunately is quite persistent when you try to disable or remove it, so this role tries to provide a way to disable it in the way it was apparently intended.

## Badges

[![Ansible Role Workflow Status](https://img.shields.io/github/workflow/status/marauderxtreme/ansible-role-motd-news/Ansible%20Role?label=Ansible-Role&logo=github "Ansible Role Workflow Status")](https://github.com/MarauderXtreme/ansible-role-motd-news/actions?query=workflow%3A%22Ansible+Role%22)
[![Markdownlint Workflow Status Badge](https://img.shields.io/github/workflow/status/marauderxtreme/ansible-role-motd-news/Markdownlint?label=Markdownlint&logo=github "Markdownlint Workflow Status")](https://github.com/MarauderXtreme/ansible-role-motd-news/actions?query=workflow%3AMarkdownlint)
![Ansible Quality Score](https://img.shields.io/ansible/quality/51225?label=Galaxy%20Quality%20Score&logo=ansible)
![Ansible Role Downloads](https://img.shields.io/ansible/role/d/51225?label=Galaxy%20Downloads&logo=ansible)

[![Ansible Role](https://img.shields.io/ansible/role/51225?label=ansible-galaxy%20install&logo=ansible)](https://galaxy.ansible.com/marauderxtreme/motd_news)

## Role Variables

The following variables are available and set to following the following defaults in `defaults/main.yml`

```yml
motd_news_enable: false
motd_news_urls: https://motd.ubuntu.com
motd_news_wait: 5
```

- `motd_news_enable` (bool) controls if the motd_news is enabled or disabled with the cache being truncated
- `motd_news_urls` (string) whitespace separated urls of news services
- `motd_news_wait` (string) timeout in seconds for fetches

## Example Playbook

This role writes files as or from root so `become` is needed.

```yml
- hosts: motd_news_disable_hosts
  become: yes
  roles:
    - motd_news

- hosts: motd_news_enable_hosts
  become: yes
  roles:
    - { role: motd_news, motd_news_enable: true }

- hosts: motd_news_other_url_hosts
  become: yes
  roles:
    - { role: motd_news,
        motd_news_enable: true,
        motd_news_urls: "https://motd.example.com https://motd.ubuntu.com"
      }
```

You can of course define those variables on `playbook_vars`, `group_vars` or `host_vars` level.

## License

MIT

## Author Information

Christoph Kepler <development@kepler.international>

## Is it any good

[Yes](https://news.ycombinator.com/item?id=3067434)
