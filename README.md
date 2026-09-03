# In Panel Workspace Name

In Panel Workspace Name puts every workspace directly on a Cinnamon panel. Each named
button switches to its workspace with one click. The active workspace uses the
panel theme's outlined state.

## Screenshots

![In Panel Workspace Name on the panel](screenshots/cinnamon-workspace-names-applet.webp)

The settings window:

![In Panel Workspace Name settings](screenshots/workspace-name-config.webp)

## Features

- One visible button per workspace
- Name, number, or number and name labels
- Horizontal and vertical panel layouts
- Density-aware label bounds with compact vertical name prefixes
- Full-name tooltips and accessible button names
- Optional trailing add button
- Disabled, normal, or reversed scroll switching
- Expo, add, rename, and remove actions in the standard applet menu
- Live updates after workspace add, remove, reorder, rename, or switch

## Settings

Open Cinnamon Settings, then Applets, then In Panel Workspace Name.

- Workspace button labels
- Maximum workspace name width
- Scroll wheel behavior
- Workspace editing controls
- Named workspace removal confirmation

Existing installations keep the same UUID. The former scroll checkbox is
migrated once to the new three-state scroll setting.

## Manual install

No root needed. Everything installs into your home directory.

From a release package:

```bash
curl -fLO https://github.com/CurbSoftware/cinnamon-workspace-names-applet/releases/latest/download/cinnamon-workspace-names-applet.zip
unzip -o cinnamon-workspace-names-applet.zip
mkdir -p ~/.local/share/cinnamon/applets
rm -rf ~/.local/share/cinnamon/applets/cinnamon-workspace-names-applet@curbsoftware
cp -r cinnamon-workspace-names-applet@curbsoftware/files/cinnamon-workspace-names-applet@curbsoftware \
   ~/.local/share/cinnamon/applets/cinnamon-workspace-names-applet@curbsoftware
```

Or straight from git:

```bash
git clone https://github.com/CurbSoftware/cinnamon-workspace-names-applet.git || git -C cinnamon-workspace-names-applet pull
cd cinnamon-workspace-names-applet
mkdir -p ~/.local/share/cinnamon/applets
rm -rf ~/.local/share/cinnamon/applets/cinnamon-workspace-names-applet@curbsoftware
cp -r files/cinnamon-workspace-names-applet@curbsoftware \
   ~/.local/share/cinnamon/applets/cinnamon-workspace-names-applet@curbsoftware
```

The `rm -rf` before the copy is the upgrade path: old files are removed so
nothing deleted upstream lingers, then the copy brings the new tree in. Your
settings are stored separately in
`~/.config/cinnamon/spices/cinnamon-workspace-names-applet@curbsoftware/`
and survive reinstalls.

Restart Cinnamon (**Alt-F2**, type `r`, Enter) and enable the applet in
Cinnamon Settings, Applets.

## Testing

```sh
gjs dev-tools/test-workspace-actions.js
python3 dev-tools/live-test-applet.py
```

## References

Derived from
[workspace-name@willurd](https://github.com/linuxmint/cinnamon-spices-applets/tree/master/workspace-name@willurd);
`info.json` keeps `original_author: willurd`. Related reference work:
[Cassia Window List](https://github.com/linuxmint/cinnamon-spices-applets/tree/master/CassiaWindowList@klangman)
by klangman.

UUID: `cinnamon-workspace-names-applet@curbsoftware`
