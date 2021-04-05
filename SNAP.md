


Snapcraft
```
snapcraft pull [<part-name>] # downloads,  source-*
snapcraft build [<part-name>] # use plugins, can use staging area on "after"
snapcraft stage [<part-name>] # copies the built parts into the staging area
snapcraft prime [<part-name>] # copies to prime, cause staging area might still contain files that are required for the build but not for the snap
snapcraft snap or snapcraft
```

Snapcraft advanced grammar: https://snapcraft.io/docs/snapcraft-advanced-grammar
```
parts:
  _part_name_:
    stage-packages:
    # libnuma1 package isn't available in armhf architecture, make it optional
    - try:
      - libnuma1
```

SNAP Running ENV Sample
```SNAP_REVISION=x3
SNAP_REAL_HOME=/home/ycheng
SNAP_USER_COMMON=/home/ycheng/snap/tensorflow-1-15/common
SNAP_INSTANCE_KEY=
SNAP_CONTEXT=HaZjXF4pxlMagyP8QSrPe8rfEMN1FZiWGzQyekdxucTmoy9km6P2
SNAP_ARCH=amd64
SNAP_INSTANCE_NAME=tensorflow-1-15
SNAP_USER_DATA=/home/ycheng/snap/tensorflow-1-15/x3
SNAP_REEXEC=
SNAP=/snap/tensorflow-1-15/x3
SNAP_COMMON=/var/snap/tensorflow-1-15/common
SNAP_VERSION=0.1
SNAP_LIBRARY_PATH=/var/lib/snapd/lib/gl:/var/lib/snapd/lib/gl32:/var/lib/snapd/void
SNAP_COOKIE=HaZjXF4pxlMagyP8QSrPe8rfEMN1FZiWGzQyekdxucTmoy9km6P2
SNAP_DATA=/var/snap/tensorflow-1-15/x3
SNAP_NAME=tensorflow-1-15
```

Tips as daily use.
* snap remove --purge hello-world # so that it won't save data into snapshot.

Tips creating snap
* need to set "env LC_ALL=C.UTF-8 pwd" so that UTF-8 works in snap.
