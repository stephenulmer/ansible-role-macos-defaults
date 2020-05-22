# Ansible Role to Configure macOS Defaults

![molecule tests](https://github.com/stephenulmer/ansible-role-macos-defaults/workflows/molecule%20tests/badge.svg)

This is an Ansible role targeted at setting up macOS preferences in a repeatable, non-interactive way.

## Usage

Example playbook usage:

```
- name: Apply macOS Defaults
  hosts: all
  vars:
    dock_orientation: "left"
    dock_autohide: "true"
    dock_autohide_delay: 0
    menu_clock_format: "EEE d MMM HH:mm"
    trackpad_zoom: true
    trackpad_3finger_drag: true
  roles:
    - ansible-role-macos-defaults
```

## Role Configuration Variables

### Dock

**dock_mru_spaces** - Re-arrange spaces (multiple desktops and full-screen applications) based on usage.

**dock_orientation** - The edge of the screen on which the dock will appear. Can take values *left*, *bottom*, or *right*.

**dock_autohide** - The dock will hide until the mouse curser is positioned near the edge specified in **dock_orientation**.

**dock_autohide_delay** - How fast the dock will hide and show itself.

**dock_active_only** - Only show *running* applications in the Dock.

**dock_single_app** - Enable single application mode.

**dock_mineffect** - The type of animation used when programs are minimized to the Dock. Can take values *genie*, *suck*, or *scale*.

**dock_magnify** - Make Dock items larger as the pointer passes over them.


### Menu Bar Clock

**menu_clock_format** - String that controls the format of the time and date display. Can include these components:

    *EEE* - Day of the week abbreviation
    *MMM* - Month abbreviation
    *d* - Day of the month
    *HH* - Hours (0-23)
    *hh* - Hours (1-12)
    *mm* - Minutes
    *ss* - Seconds
    *a* - AM/PM indicator

Some formats appear to be broken by macOS Catalina. The SystemUIServer silently rewrites a perfectly valid string to a different one, so the playbook fails idempotency checks if you happen to pick that string. Also, the clock won't ever change to your custom format. Some of them work, however, so good luck!

**menu_clock_analog** - Display a tiny analog clock that is impossible to read.

**menu_clock_flash** - Makes the separators between time components flash in a distracting an annoying way.


### Finder

**ds_ignore_network_shares** - Don't write .DS_store on network volumes.

**ds_ignore_media** - Don't write .DS_store on removeable media.


### Safari

**safari_develop_menu** - Turn on the develop(er's) menu. Allows showing page source, etc.

**safari_show_favorites_bar** - Show favorite bookmarks just above the tabs.

**safari_tabs_cmdnum_swiches** - Use Command+1 through Command+9 to switch tabs; Otherwise they activate favorites.

**safari_tabs_new_in_front** - Immediately switch to a new tab when it opens.

**safari_homepage** - Set the page to open in a new browser window.


### Trackpad

**trackpad_zoom** - Zoom the entire screen by holding control (^) and using a scroll gesture.

**trackpad_3finger_drag** - Drag items using 3 fingers.

**trackpad_tap_to_click** - Tapping on the trackpad will activate a click, in addition to actually depressing it.


### Mail

**mail_shortcuts** - List of keyboard shortcuts to add for the built-in email program.


### Global

**gloabl_shortcuts** - List of keyboard shortcuts to add for the entire system.


## License

MIT, see LICENSE file.


## Author

Created in 2020 by Stephen Ulmer.

