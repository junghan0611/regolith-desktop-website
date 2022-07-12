---
title: 소개
type: docs
bookToc: false
---

# 레골리스(Regolith) 데스크톱 환경 2.0

![](/regolith-empty.png)

{{< columns >}}

### 생산성 우선

레골리스는 키보드 기반의 작업 흐름 관리에 적합한, 인기 있고 빠르며 설정 변경이 가능한 타일링 창 관리자인 [i3](https://i3wm.org/) 기반으로 동작 합니다. 또한 레골리스는 i3를 `i3bar`, `rofication`, `gnome-flashback`, [`ilia`](https://github.com/regolith-linux/ilia#readme) 등의 다른 데스크톱 컴포넌트들과 통합하여 완벽한 데스크톱 인터페이스를 제공합니다. 

<--->

### 그놈(GNOME) 시스템 관리

레골리스는 [`gnome-flashback`](https://wiki.gnome.org/Projects/GnomeFlashback) 기반으로 그놈 세션을 제공함으로써 전형적인 `gnome-shell` 데스크톱 환경이 가지는 복잡성을 대부분 회피하며 이와 동시에 간결하고 일관적인 시스템 관리 기능을 제공합니다. 

{{< /columns >}}

***

# 레골리스 2.0 설치

{{< tabs "uniqueid" >}}
{{< tab "Ubuntu 22.04" >}}

레골리스는 시스템 패키지로 설치할 수 있습니다. 이를 통해 업데이트 및 제거 작업을 쉽고 일관되게 수행할 수 있습니다. 다음 단계에서는 레골리스 패키지 저장소에서 패키지를 가져오기 위해 시스템을 설정하는 방법과 데스크톱 패키지를 설치하는 방법을 설명합니다.

1. 먼저, 로컬 상의 `apt`에 레골리스 공개키를 등록합니다. 

   ```console
   wget -qO - https://regolith-desktop.io/regolith.key | \
   gpg --dearmor | sudo tee /usr/share/keyrings/regolith-archive-keyring.gpg > /dev/null
   ```

2. 로컬 `apt`에 저장소의 URL을 추가합니다. 

   ```console
   echo deb "[arch=amd64 signed-by=/usr/share/keyrings/regolith-archive-keyring.gpg] \
   https://regolith-desktop.io/release-ubuntu-jammy-amd64 jammy main" | \
   sudo tee /etc/apt/sources.list.d/regolith.list
   ```

{{< hint info >}}
ARM 기반의 시스템에 설치하고자 한다면 위의 라인에서 `amd64` 두 곳을 `arm64`로 각각 변경합니다.
{{< /hint >}}

1. `apt`를 갱신하고 레골리스를 설치합니다.

   ```console
   sudo apt update
   sudo apt install regolith-desktop
   sudo apt upgrade
   ```

1. 시스템 재시작

The login manager will need to be restarted for the new desktop session to be recognized. The easiest way of restarting it is to reboot your system.

{{< hint warning >}}
The Regolith Desktop is very different from common desktop environments. By default does not use docks, icon folders, or global drop-down menus.  See the [Getting Started guide]({{< ref "/docs/using-regolith/first-launch" >}}) for important details.
{{< /hint >}}

{{< /tab >}}

{{< tab "Ubuntu 20.04" >}}

Regolith can be installed as system packages.  This makes updating and removing easy and consistent.  The following steps describe how
to configure your system to read packages from the Regolith package repository and install the desktop package.

1. Register the Regolith public key to your local `apt`:

   ```console
   wget -qO - https://regolith-desktop.io/regolith.key | sudo apt-key add -
   ```

1. Add the repository URL to your local `apt`:

   ```console
   echo deb "[arch=amd64] https://regolith-desktop.io/release-ubuntu-focal-amd64 focal main" | \
   sudo tee /etc/apt/sources.list.d/regolith.list
   ```

{{< hint info >}}
Substitue `arm64` for `amd64` in the two places in the above line to install on ARM-based systems.
{{< /hint >}}

1. Update `apt` and install Regolith

   ```console
   sudo apt update
   sudo apt install regolith-desktop
   sudo apt upgrade
   ```

1. System Restart

The login manager will need to be restarted for the new desktop session to be recognized. The easiest way of restarting it is to reboot your system.

{{< /tab >}}

{{< tab "Debian Bullseye" >}}

Regolith can be installed as system packages.  This makes updating and removing easy and consistent.  The following steps describe how
to configure your system to read packages from the Regolith package repository and install the desktop package.

1. Register the Regolith public key to your local `apt`:

   ```console
   wget -qO - https://regolith-desktop.io/regolith.key | \
   gpg --dearmor | sudo tee /usr/share/keyrings/regolith-archive-keyring.gpg > /dev/null
   ```

1. Add the repository URL to your local `apt`:

   ```console
   echo deb "[arch=amd64 signed-by=/usr/share/keyrings/regolith-archive-keyring.gpg] \
   https://regolith-desktop.io/release-debian-bullseye-amd64 bullseye main" | \
   sudo tee /etc/apt/sources.list.d/regolith.list
   ```
{{< hint info >}}
Substitue `arm64` for `amd64` in the two places in the above line to install on ARM-based systems.
{{< /hint >}}

1. Update `apt` and install Regolith

   ```console
   sudo apt update
   sudo apt install regolith-desktop
   sudo apt upgrade
   ```

1. System Restart

The login manager will need to be restarted for the new desktop session to be recognized. The easiest way of restarting it is to reboot your system.

{{< /tab >}}
{{< tab "Upgrade from Regolith 1.6" >}}

To install Regolith 2 into an existing Ubuntu system that is upgrading to 22.04, follow these steps:

1. Upgrade the system to all the latest packages on current release (either Ubuntu 20.04 or 21.10)
1. Perform the [Ubuntu system upgrade to 22.04](https://www.omgubuntu.co.uk/2022/04/how-to-upgrade-to-ubuntu-22-04-lts), however **DO NOT** reboot as prompted **until the following steps are completed**
1. After the 22.04 upgrade completes, add the Regolith 2 package repository:

   ```console
   wget -qO - https://regolith-desktop.io/regolith.key | gpg --dearmor | sudo tee /usr/share/keyrings/regolith-archive-keyring.gpg > /dev/null
   echo deb "[arch=amd64 signed-by=/usr/share/keyrings/regolith-archive-keyring.gpg] https://regolith-desktop.io/release-ubuntu-jammy-amd64 jammy main" | \
   sudo tee /etc/apt/sources.list.d/regolith.list
   sudo apt update
   ```

1. Next install the Regolith 2 desktop package:

   ```console
   sudo apt install regolith-desktop # See configuration page for additional packages 
   sudo apt dist-upgrade
   ```

1. Now reboot the system and select the regolith session at the login screen

Custom configurations from Regolith 1.6 will need to be manually ported to Regolith 2.  In order to make this upgrade simpler, Regolith 2 uses the user config directory of `~/.config/regolith2`.  It will not read files from the Regolith 1.x user config directory `~/.config/regolith`.  Please refer to [the configuration page](docs/using-regolith/configuration) for more details.

{{< /tab >}}
{{< tab "Regolith Linux - Beta 1" >}} 

Regolith Linux is the Regolith Desktop environment installed into a customized Ubuntu 22.04 installer image.  It allows one to boot from a USB drive to run Regolith without having to install it.  It also allows to install the system onto a computer's drive.  Regolith Linux has the following features in addition to the Regolith Desktop:

* Branded boot up screen
* Branded login screen
* Use `lightdm` over `gdm3`.
* The following packages are not installed: `gdm3`, `gnome-shell`, `ubuntu-session`, `evolution-data-server`, `snapd`.  These packages may be installed as needed by the user.

The ISO comes in two forms, a "mini" ISO which includes a paired down experience and only includes the default look.  Also a "regular" ISO is somewhat bigger but includes built-in support for all official Looks and comes installed with many more status icons.

* [Regolith Linux 2.1](https://regolith-linux.io/dist/regolith-2.0.0.iso) / [md5sum](https://regolith-linux.io/dist/regolith-2.0.0.md5sum)
* [Regolith Linux 2.1 Mini](https://regolith-linux.io/dist/regolith-mini-2.0.0.iso) / [md5sum](https://regolith-linux.io/dist/regolith-mini-2.0.0.md5sum)

See the [Regolith 2.1 release notes](docs/reference/Releases/regolith-2.1-release-notes) for more information.

{{< /tab >}}
{{< tab "Other..." >}} 

Other options are available and documented in the [package repository for Regolith](https://github.com/regolith-linux/voulage), including support for `arm64`-based systems.

{{< /tab >}}
{{< /tabs >}}


## Visual Tour
***

{{< columns >}}

![](/regolith-ilia-keybindings.png)
Upon first login, an overlay (toggled anytime via <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">?</span></span>) presents the most important keybindings used with i3-wm.

<--->

![](/regolith-floating-terminal.png)
For those that work in the terminal, pressing <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">enter</span></span> is all it takes to get to business.

{{< /columns >}}

{{< columns >}}

![](/regolith-ilia-apps.png)
A single global app launcher is instantly available from anywhere to run your programs via <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">space</span></span>.</p>

<--->

![](/regolith-desktop-terminals.png)
Need more terminals?  Create layouts on the fly by toggling between horizontal and vertical modes with <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">backspace</span></span> followed by <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">enter</span></span>.  Navigate to windows positionally with <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">h</span> <span class="badge badge-warning">j</span> <span class="badge badge-warning">k</span> <span class="badge badge-warning">l</span></span>.

{{< /columns >}}

{{< columns >}}

![](/regolith-floating-windows.png)
Toggle floating window mode with <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">F</span></span>.  Resize windows with <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">r</span></span> and move them around with the mouse by pressing <span class="badge badge-warning">super</span>.

<--->

![](/regolith-gnome-flashback.png)
Gnome Flashback provides consistent and simple system management. Tweak your UI, auto mount your USB drives, connect to wireless networks. Launch the control panel with <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">c</span></span>.

{{< /columns >}}

{{< columns >}}

![](/regolith-screenshot-look-selector.png)
Easily switch to <a href="https://ethanschoonover.com/solarized">Solarized</a> or other looks with the <code>regolith-look</code> command. Because <b>looks</b> utilize the package manager, you only store theme resources that you're using.

<--->

![](/regolith-ilia-windows.png)
Got a lot going on?  Quickly find the window you're looking for via <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">ctrl</span> <span class="badge badge-warning">space</span></span> or navigate over workspaces with <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">[0 - 19]</span></span>.

{{< /columns >}}

{{< columns >}}

![](/regolith-many-windows.png)
Waste no space on frivolous UI and take advantage of every pixel without micro-managing your window layouts.

<--->

![](/regolith-ilia-notifications.png)
Desktop notifications do not compete for your attention, but rather can be managed via an on-screen dialog by pressing <span class="text-nowrap"><span class="badge badge-warning">super</span> <span class="badge badge-warning">n</span></span>.

{{< /columns >}}

# Interaction

{{< columns >}}

### Announcements

* [Follow us on Twitter to get the latest news](https://twitter.com/RegolithL)
* [Follow us on Mastodon to get the latest news](https://fosstodon.org/@regolith)
* [Subscribe to the mailing list for release annoucements](https://www.freelists.org/list/regolith-linux)

<--->

### Discussion and Help

* Join us on [Slack](https://regolith-linux.herokuapp.com/) for help and discussion
* Search from [existing issues or create a new issue](https://github.com/regolith-linux/regolith-desktop/issues) for bugs and feature requests
<--->

### Development

* The [Regolith GitHub org](https://github.com/regolith-linux) is where development happens.

{{< /columns >}}
