# Tracking installation of specific snaps

This repository contains a demonstration of the usage of the snapd content
interface and interface hooks to make `program-foo` aware of installation and
removal of `program-bar`. Both programs are using classic confinement as an
additional constraint. Without that it would be somewhat easier. In practice
the notification is on connection and disconnection but this is close enough
without requiring any additional features in snapd.

Please read the source code to understand more about how they work. You can
build and install each of the snaps with `snap pack <dir>` and `snap install
--dangerous --classic ./<file>`. Please do note that because of how unasserted
programs are installed, you need to manually establish the connection with
`snap connect program-foo:peers program-bar:peer-info`. If the two snaps were
coming from the store, from the same publisher, the connection would be
established automatically.

Once connected you can check the status of the
snap.program-foo.peer-helper.service which is fired after connection.
