# plopoyop.adguardhome

Install & configure AdGuard Home DNS server

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [adguardhome_config](#adguardhome_config)
  - [adguardhome_disable_resolved_stub](#adguardhome_disable_resolved_stub)
  - [adguardhome_dns_bind_hosts](#adguardhome_dns_bind_hosts)
  - [adguardhome_dns_port](#adguardhome_dns_port)
  - [adguardhome_service_enabled](#adguardhome_service_enabled)
  - [adguardhome_service_state](#adguardhome_service_state)
  - [adguardhome_system_group](#adguardhome_system_group)
  - [adguardhome_system_user](#adguardhome_system_user)
  - [adguardhome_users](#adguardhome_users)
  - [adguardhome_version](#adguardhome_version)
  - [adguardhome_web_address](#adguardhome_web_address)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.19`

## Default Variables

### adguardhome_config

Any AdGuardHome.yaml setting. Recursively merged over the role defaults
(schema version 35); lists replace the default lists.

**_Type:_** dict<br />

#### Default value

```YAML
adguardhome_config: {}
```

#### Example usage

```YAML
adguardhome_config:
  dns:
    upstream_dns:
      - "https://dns.quad9.net/dns-query"
  filtering:
    rewrites:
      - domain: "nas.home.arpa"
        answer: "192.0.2.10"
        enabled: true
```

### adguardhome_disable_resolved_stub

When systemd-resolved is running, disable its stub listener on port 53 and
point /etc/resolv.conf to the resolved upstream servers

**_Type:_** boolean<br />

#### Default value

```YAML
adguardhome_disable_resolved_stub: true
```

### adguardhome_dns_bind_hosts

Addresses the DNS server listens on

**_Type:_** list<br />

#### Default value

```YAML
adguardhome_dns_bind_hosts:
  - 0.0.0.0
```

### adguardhome_dns_port

DNS server port

**_Type:_** number<br />

#### Default value

```YAML
adguardhome_dns_port: 53
```

### adguardhome_service_enabled

Enable AdGuard Home service on boot

**_Type:_** boolean<br />

#### Default value

```YAML
adguardhome_service_enabled: true
```

### adguardhome_service_state

AdGuard Home service state

**_Type:_** string<br />

#### Default value

```YAML
adguardhome_service_state: started
```

### adguardhome_system_group

System group running AdGuard Home

**_Type:_** string<br />

#### Default value

```YAML
adguardhome_system_group: adguardhome
```

### adguardhome_system_user

System user running AdGuard Home

**_Type:_** string<br />

#### Default value

```YAML
adguardhome_system_user: adguardhome
```

### adguardhome_users

Web interface accounts. `password` must be a bcrypt hash
(`htpasswd -nbBC 10 "" 'secret' | cut -d: -f2`). An empty list disables
authentication: only acceptable while the web interface is bound to localhost.

**_Type:_** list<br />

#### Default value

```YAML
adguardhome_users: []
```

### adguardhome_version

AdGuard Home version to install (without the leading "v")

**_Type:_** string<br />

#### Default value

```YAML
adguardhome_version: 1.0.0
```

### adguardhome_web_address

Listen address of the web interface and API (host:port).
Bound to localhost by default: expose it through a reverse proxy.

**_Type:_** string<br />

#### Default value

```YAML
adguardhome_web_address: 127.0.0.1:3000
```

## Dependencies

None.

## License

MPL-2.0

## Author

Clément Hubert
