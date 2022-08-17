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

```yaml
dockutil_homebrew_cask: hpedrorodrigues/tools/dockutil
```

Which Homebrew cask to install for dockutil. See [this issue](https://github.com/kcrawford/dockutil/issues/127) to read more about why this cask is the default.

```yaml
dockutil_install: true
```

Whether to install dockutil or not. If set to false you'll need to have installed dockutil prior to the execution of this role. See [this issue](https://github.com/buluma/ansible-collection-mac/issues/42) for alternate installation methods, which may be necessary depending on your version of macOS.

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

The contents of this role were originally created by [@dspolleke](https://github.com/dspolleke) as part of the [`mac-dev-playbook`](https://github.com/buluma/mac-dev-playbook).
