GPU Install Role
=========

This Role installs GPU drivers for AMD and Nvidia Graphics cards.

Requirements
------------

None

Role Variables
--------------

- `vendor`
  - The vendor of the GPU
  - Valid values:
    - amd
    - nvidia
- `driver_version`
  - The version of the relevant drivers to install
  - Valid values depend on `vendor`
- `library_version`
  - Installs CUDA/ROCm with the specified version
  - Valid values depend on `vendor`
- `dry_run`
  - Perform a dry run without actually installing anything
  - Default is `False`

Dependencies
------------

None

Example Playbook
----------------

## Nvidia

```yaml
---
- name: Install Drivers
  hosts: all
  become: True
  roles:
    - role: gpu_install
      vendor: nvidia
      driver_version: 550.127.05
      library_version: 12.4
```

## AMD
```yaml
---
- name: Install Drivers
  hosts: all
  become: True
  roles:
    - role: gpu_install
      vendor: amd
      library_version: 6.3.3
```

License
-------

GPL-2.0

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
