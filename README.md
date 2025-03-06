# README

This template downloads and installs the Splunk Unversal Forwader agent on windows. 


## Requirements

to use localy clone this repo and run the following

```bash
ludus ansible roles add -d ./ludus_splunk_uf_windows/ --force
ludus range deploy -t user-defined-roles --limit localhost,JD-ad-win11-22h2-enterprise-x64-1  --only-roles ludus_splunk_uf_windows
ludus range logs -f
```

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

  splunk_package_url_uf: "https://download.splunk.com/products/universalforwarder/releases/{{ splunk_package_version }}/windows/splunkforwarder-{{ splunk_package_version }}-{{ build_id }}-windows-x64.msi"
  splunk_package_version: 9.1.3
  build_id: 6b4ebe426ca6
  ludus_splunk_server: ""
  ludus_splunk_server_forwarder_port: 9997

## Dependencies

None.

## Example Playbook

```yaml
tba
```

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-ad-dc-win2022-server-x64-1"
    hostname: "{{ range_id }}-DC01-2022"
    template: win2022-server-x64-template
    vlan: 10
    ip_last_octet: 11
    ram_gb: 6
    cpus: 4
    windows:
      sysprep: true
    domain:
      fqdn: ludus.domain
      role: primary-dc
    roles:
      - "as it appears in `ludus ansible roles list`"
    role_vars:
      {{ example role var usage }}
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [{{Your Github Username}}](https://github.com/{{ your github username }}), for [Ludus](https://ludus.cloud/).
