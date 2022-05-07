# Ansible Role: macOS Dock Automation

This role automates the use of `dockutil` to manage the items in your macOS Dock. You can add, remove, and arrange Dock items.

## Requirements

  - **Homebrew**: Requires `homebrew` already installed (you can use `buluma.mac.homebrew` to install it on your Mac).

## Role Variables

Available variables are listed below, along with example values (see `defaults/main.yml`):

```yaml
dockitems_remove: []
```

Dock items to remove.

```yaml
dockitems_persist: []
```

Dock items to add. `pos` parameter is optional and will place the Dock item in a particular position in the Dock.

## Dependencies

  - (Soft dependency) `buluma.homebrew`

## Example Playbook

```yaml
    - hosts: localhost

      vars:
        dockitems_remove:
          - Launchpad
          - TV
          - Podcasts
          - 'App Store'

        dockitems_persist:
          - name: Messages
            path: "/Applications/Messages.app/"
          - name: Safari
            path: "/Applications/Safari.app/"
            pos: 2
          - name: Sublime Text
            path: "/Applications/Sublime Text.app/"
            pos: 3

      roles:
        - buluma.mac.homebrew
        - buluma.mac.dock
```

See the [Mac Development Ansible Playbook](https://github.com/buluma/mac-dev-playbook) for an example of this role's usage.

## License

Apache-2.0

## Author Information
This role was created in 2022 by [Michael Buluma](https://buluma.github.io)

The contents of this role were originally created by [Michael Buluma](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
