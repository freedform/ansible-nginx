# nginx

Role nginx gives full control over NGINX process and all its configuration files.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [nginx](#nginx)
  - [nginx_acls](#nginx_acls)
  - [nginx_actions](#nginx_actions)
  - [nginx_base_dir](#nginx_base_dir)
  - [nginx_file_group](#nginx_file_group)
  - [nginx_file_owner](#nginx_file_owner)
  - [nginx_state_action](#nginx_state_action)
  - [nginx_version](#nginx_version)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.20`

## Default Variables

### nginx

Nginx config

**_Required:_** `true`, only in case `nginx_actions: deploy_config`<br />
**_Type:_** dict<br />

#### Example usage

```YAML
nginx:
  global:
    parameter: value
  events:
    parameter: value
  http:
    parameter: value
  servers:
    vhost-1.example.com:
      http:
        parameter: value
      https:
        parameter: value
    vhost-2.example.com:
      http:
        parameter: value
      https:
        parameter: value
```

### nginx_acls

Optional mapping of ACL filenames to their directive content, deployed to nginx_base_dir.
Each value is a dict of directives where the value can be a string or a list of strings.

**_Type:_** Dict<br />

#### Example usage

```YAML
nginx_acls:
  geoblock.conf:
    allow:
      - 192.168.1.0/24
      - 10.0.0.0/8
    deny: all
```

### nginx_actions

List of actions the role does, accepts one or more actions.
Use comma without spaces as a delimiter for multiple actions.

**_Required:_** `true`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  nginx_actions: deploy_config
  nginx_actions: install,deploy_config
```

### nginx_base_dir

Main configuration directory

**_Type:_** String<br />

#### Default value

```YAML
nginx_base_dir: /etc/nginx
```

### nginx_file_group

NGINX files group name

**_Type:_** String<br />

#### Default value

```YAML
nginx_file_group: root
```

### nginx_file_owner

NGINX files owner name

**_Type:_** String<br />

#### Default value

```YAML
nginx_file_owner: root
```

### nginx_state_action

Controls state of NGINX process

**_Required:_** `true`, only in case `nginx_actions: state_control`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  nginx_state_action: reloaded
  nginx_state_action: started
  nginx_state_action: stopped
```

### nginx_version

NGINX version for installation

**_Type:_** String<br />

#### Default value

```YAML
nginx_version: 1.24.0-2ubuntu7.6
```

## Dependencies

None.

## License

MIT

## Author

freedform
