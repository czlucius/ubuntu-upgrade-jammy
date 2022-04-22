# Upgrade Ubuntu to 22.04 Jammy Jellyfish

Currently, Ubuntu's Software & Updates does not detect the upgrade for Jammy Jellyfish 22.04.  
This exposes 22.04 stable to Ubuntu so it can upgrade.

## 1. Changing the upgrade link
   
Edit `/etc/update-manager/meta-release` in your preferred editor(I'm using `gedit`)  
You should see something like this:
```
# default location for the meta-release file

[METARELEASE]
URI = https://changelogs.ubuntu.com/meta-release
URI_LTS = https://changelogs.ubuntu.com/meta-release-lts
URI_UNSTABLE_POSTFIX = -development
URI_PROPOSED_POSTFIX = -proposed

```

Change
`URI = https://changelogs.ubuntu.com/meta-release` to `URI = https://raw.githubusercontent.com/czlucius/ubuntu-upgrade-jammy/main/meta_release_jammy`.  
This link is pointing to the `meta_release_jammy` file of this repo: https://github.com/czlucius/ubuntu-upgrade-jammy/blob/main/meta_release_jammy.
(you can compare with https://changelogs.ubuntu.com/meta-release if you're concerned about it's safety)

Save the file.

## 2. Check and install the upgrade

In a terminal window, type `do-release-upgrade` to fetch the upgrades from Ubuntu(Canonical)'s servers. Accept all prompts and the upgrade should be installed.
