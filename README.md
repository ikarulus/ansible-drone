# Ansible Drone

[![Stack](https://raw.githubusercontent.com/paralect/stack/master/stack-component-template/stack.png)](https://github.com/paralect/stack)

[![All Contributors](https://img.shields.io/badge/all_contributors-2-orange.svg?style=flat-square)](#contributors)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-drone-blue.svg?style=flat-square)](https://galaxy.ansible.com/paralect/drone)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square)](https://github.com/paralect/ansible-mongo/blob/master/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)


[![Watch on GitHub](https://img.shields.io/github/watchers/paralect/ansible-drone.svg?style=social&label=Watch)](https://github.com/paralect/ansible-drone/watchers)
[![Star on GitHub](https://img.shields.io/github/stars/paralect/ansible-drone.svg?style=social&label=Stars)](https://github.com/paralect/ansible-drone/stargazers)
[![Follow](https://img.shields.io/twitter/follow/paralect.svg?style=social&label=Follow)](https://twitter.com/paralect)
[![Tweet](https://img.shields.io/twitter/url/https/github.com/paralect/ansible-drone.svg?style=social)](https://twitter.com/intent/tweet?text=I%27m%20using%20Stack%20components%20to%20build%20my%20next%20product%20🚀.%20Check%20it%20out:%20https://github.com/paralect/ansible-drone)

An ansible role for the [drone](https://github.com/drone/drone) CI deployment with Github/Bitbucket Cloud integration and PostgreSQL database.

## Role Variables

Available variables:

|Name|Default|Description|
|:--:|:--:|:----------|
|**`drone_version`**|`latest`|Version of Drone CI, see other versions [here](https://hub.docker.com/r/drone/drone/tags)|
|**`drone_admins`**|`""`|List of users with admin access to the drone, readme [more]( http://docs.drone.io/user-management)|
|**`drone_agents`**|`[{name: "Nancy"}]`|Name of the docker agent container, you can add more than one agent|
|**`drone_host`**|`""`|The url, where drone instance will be publicly available. Typically you would have nginx in front of Drone CI|
|**`drone_secret`**|`hTirsXmrY4YsyK79ELgB`|Drone secret key, used for private communication between agent and web UI [more info](http://docs.drone.io/install-for-github)|
|**`drone_integration`**|`github`|Integration type used by Drone CI. Available types: {`github`,`bitbucket_cloud`}|
|**`drone_github_client`**|`""`|Github oauth application client identifier, [more info](http://docs.drone.io/install-for-github)|
|**`drone_github_secret`**|`""`|Github oauth application client secret, [more info]( http://docs.drone.io/install-for-github)|
|**`drone_bitbucket_key`**|`""`|Bitbucket Cloud oauth application client key, [more info](http://docs.drone.io/install-for-bitbucket-cloud/)|
|**`drone_bitbucket_secret`**|`""`|Bitbucket Cloud oauth application client secret, [more info](http://docs.drone.io/install-for-bitbucket-cloud/)|
|**`drone_postgress_password`**|`droneRocks23@p`|A password to postgress db used by drone|
|**`drone_postgress_user`**|`drone`|A username to postgress db used by drone, [read more](http://docs.drone.io/database-settings)|
|**`drone_postgress_db`**|`drone`|A name of to postgress db used by drone, [read more](http://docs.drone.io/database-settings)|
|**`drone_postgress_data_dir`**|`/drone-postgres-data`|A directory on a host machine, where postgresql data stored|
|**`nginx_drone_internal_host`**|`http://localhost:8000`|Internal drone ui http url used by nginx to proxy traffic. For example: http://localhost:8000|

## Dependencies

[Docker](https://www.docker.com/) must be installed on the server in order to use this role. If you don't have docker on your server we recommend [angstwad.docker_ubuntu](https://github.com/angstwad/docker.ubuntu) Ansible role.

Example of using `angstwad.docker_ubuntu`:
```yml
---
- name: Setup drone ci server
  hosts: drone
  become: true
  roles:
    - { role: angstwad.docker_ubuntu }
```

## Quick example

Example of the playbook file:

```yml
---
- name: Deploy drone CI server
  hosts: drone
  become_user: root
  become: true
  roles:
    - role: paralect.drone
      # Version of Drone CI, see other versions here: https://hub.docker.com/r/drone/drone/tags/
      drone_version: latest

      # the url, where drone instance will be publicly available
      # typically you would have nginx in front of Drone CI
      drone_host: http://178.62.116.103

      # Drone secret key, used for private communication between agent and web UI
      # more info: http://docs.drone.io/install-for-github/
      drone_secret: hTirsXmrY4YsyK79ELgB

      # Drone integration type
      drone_integration: bitbucket_cloud

      # Bitbucket Cloud oauth application client key and secret, more info http://docs.drone.io/install-for-bitbucket-cloud/
      drone_bitbucket_key:
      drone_bitbucket_secret:

      # A password to postgress db used by drone
      drone_postgress_password: droneRocks23@p
      # A username to postgress db used by drone, read more: http://docs.drone.io/database-settings/
      drone_postgress_user: drone
      # A name of to postgress db used by drone, read more: http://docs.drone.io/database-settings/
      drone_postgress_db: drone
      # a directory on a host machine, where postgresql data stored
      drone_postgress_data_dir: /drone-postgres-data
```

## Change Log

This project adheres to [Semantic Versioning](http://semver.org/).
Every release is documented on the Github [Releases](https://github.com/paralect/node-mongo/releases) page.

## License

Ansible-drone is released under the [MIT License](https://github.com/paralect/ansible-mongo/blob/master/LICENSE).

## Contributing

Please read [CONTRIBUTING.md](https://github.com/paralect/ansible-drone/blob/master/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
| [<img src="https://avatars3.githubusercontent.com/u/681396?v=4" width="100px;"/><br /><sub><b>Andrew Orsich</b></sub>](https://github.com/anorsich)<br />[📖](https://github.com/paralect/ansible-drone/commits?author=anorsich "Documentation") [🤔](#ideas-anorsich "Ideas, Planning, & Feedback") [💻](https://github.com/paralect/ansible-drone/commits?author=anorsich "Code") [📖](https://github.com/paralect/ansible-drone/commits?author=anorsich "Documentation") [🤔](#ideas-anorsich "Ideas, Planning, & Feedback") [👀](#review-anorsich "Reviewed Pull Requests") | [<img src="https://avatars2.githubusercontent.com/u/6461311?v=4" width="100px;"/><br /><sub><b>Evgeny Zhivitsa</b></sub>](https://github.com/ezhivitsa)<br />[📖](https://github.com/paralect/ansible-drone/commits?author=ezhivitsa "Documentation") |
| :---: | :---: |
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification. Contributions of any kind welcome!
