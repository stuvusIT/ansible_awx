# awx

This role sets up a local AWX installation using the Docker installation.
Non-containerized installation is not supported by AWX as of writing.

The data can be found in `/var/lib/awx`.

## Requirements

Ubuntu

## Role Variables

| Name                | Default/Required    | Description                                      |
|---------------------|:-------------------:|--------------------------------------------------|
| `awx_arch`          | `amd64`             | Architecture of the target CPU                   |
| `awx_postgres_data` | `/var/lib/postgres` | Location of the data of the PostgreSQL container |
| `awx_tunables`      |                     | Dict of all installer tunables                   |

## Example Playbook

```yml
- hosts: awx
  roles:
  - awx
     awx_tunables:
       awx_secret_key: secretsecretkey
       host_port: 127.0.0.1:8080 # Bind to localhost
       awx_official: true # Use official AWX branding
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
