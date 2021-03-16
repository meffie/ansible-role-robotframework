# Ansible Role: Robot Framework

Installs the [Robot Framework](https://robotframework.org) test automation
framework, and optionally one or more external test libraries and directories
of test sources.

This role will install Robot Framework with ``pip``.

``pip`` will be installed if not already present. The EPEL repository will be
installed on RHEL/CentOS distributions in order to install ``pip``.

## Requirements

Ansible 2.10 or later.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    robotframework_package_name

The Robot Framework pip package name. Default value is `robotframework`.

    robotframework_package_version_spec

The `pip` version specification to install a specific Robot Framework version.
The default value is empty, so `pip` will install the latest when Robot Framework
is not already present.

    robotframework_external_libraries

A list of external Robot Framework libraries to be installed via `pip`. The
default list is empty.

    robotframework_test_directory

Destination directory to copy test data. The directory will be created if it does
not exist. The directory will be created and owned by the current `ansible_user`.
The default directory is '.' (the current working directory).

    robotframework_test_data

A list of paths on the controller to directories containing Robot Framework
test data (that is *.robot files) to be copied to
`robotframework_test_directory`. The default value is an empty list.

Note: If your test data resides in `git`, consider adding a `git` task to
your playbook to checkout the files on the managed host.

## Dependencies

None

## Example Playbook

    - hosts: testers
      vars:
        robotframework_test_data:
          - /path/to/my/tests/on/the/controller
      roles:
        - robotframework

## License

MIT
