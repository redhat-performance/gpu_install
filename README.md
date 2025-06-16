GPU Install Role
=========

This Role installs GPU drivers for AMD and Nvidia Graphics cards.

Requirements
------------

None

Role Variables
--------------

- `gpu_install_vendor`
  - The vendor of the GPU
  - Valid values:
    - auto (does best effort to determine which vendor's GPUs are present)
    - amd
    - nvidia
- `gpu_install_driver_version`
  - The version of the relevant drivers to install
  - Valid values depend on `vendor`
- `gpu_install_library`
  - Toggles wheter or not to install CUDA/ROCm
  - Default is `False`
- `gpu_install_library_version`
  - Installs CUDA/ROCm with the specified version
  - Valid values depend on `vendor`
- `gpu_install_dry_run`
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
      gpu_install_vendor: nvidia
      gpu_install_driver_version: 550.127.05
      gpu_install_library_version: 12.4
```

## AMD
```yaml
---
- name: Install Drivers
  hosts: all
  become: True
  roles:
    - role: gpu_install
      gpu_install_vendor: amd
      gpu_install_library_version: 6.3.3
```

License
-------

GPL-2.0

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
