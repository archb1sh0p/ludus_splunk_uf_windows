# README

This template includes a task yml for caching downloads to the Ludus host (download_file.yml) as well as GitHub action to push the role to Ansible Galaxy when a tag is created in git. You'll need to get a [Galaxy token](https://galaxy.ansible.com/ui/token/) and set it as `GALAXY_API_KEY` in [Github Secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository) for the Ansible Galaxy deployment to work correctly.

Remove this section, and replace all `{{ variable }}` strings. Write your tasks in `./tasks/main.yml`

# Ansible Role: {{ Thing }} ([Ludus](https://ludus.cloud))

An Ansible Role that installs the Splunk Universal Forwader Agent on Windows 


## Requirements

None.

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
- hosts: {{ thing }}_hosts
  roles:
    - {{ your github username }}.{{ this repo name }}
  vars:
    {{ role vars here }}
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
      - {{ your github username }}.{{ this repo name }}
    role_vars:
      {{ example role var usage }}
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [{{Your Github Username}}](https://github.com/{{ your github username }}), for [Ludus](https://ludus.cloud/).
