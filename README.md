<p align="center">
  <img src="banner.svg" alt="TT1NKER" width="100%">
</p>

```text
$ whoami
tt1nker


$ cat /etc/os-release
NAME="tt1nker"
ID=human
VARIANT="linux first · low-level by training · agents by curiosity"
HOME_URL="github.com/TT1nKer"
SUPPORT_URL="hostsjimi@gmail.com"
BUILD_ID=2026.04


$ uname -a
tt1nker arch-linux-x86_64 #1 SMP PREEMPT_DYNAMIC online-since 2025-06 unsleep


$ pacman -Qe                              # explicitly installed
ai/agent-workflows                        latest
ai/mcp                                    latest
ai/claude-api                             latest
fullstack/vue                             stable
fullstack/python                          stable
fullstack/javascript                      stable
linux/arch                                rolling
linux/dotfiles                            git
linux/shell                               daily-driven
lowlevel/c                                c11
lowlevel/cpp                              c++17
lowlevel/asm                              x86_64
lowlevel/compilers                        0.0.1
lowlevel/stm32-firmware                   bare-metal
sim/life-simulation                       speculative
sim/orbital-mechanics                     numerical
sim/narrative-agents                      experimental


$ ls -lah ~/Projects
drwxr-xr-x  AICharacter      ·  ai character builder · story distiller
drwxr-xr-x  Doomsday         ·  《宇宙冷漠》life-sim · npcs · tension engine · ten-tick
drwxr-xr-x  solar            ·  c++17 solar system simulator · halo orbits · hohmann transfer
drwxr-xr-x  placecell        ·  place-cell transformer · spatial cognition
drwxr-xr-x  voice-type       ·  voice → text via sensevoice
drwxr-xr-x  aiLab            ·  experiments


$ ls -lah ~/Downloads | grep -v '^d' | head
electronics-10-02779.pdf            ·  rf / power electronics paper
energies-07-04316.pdf               ·  energy systems journal
'Mathcing Network.pdf'              ·  rf matching network design [sic]
NetLogo-7.0.3-64.tgz                ·  agent-based modeling
Persistent_State_AI_Pitch.pptx      ·  pitch · persistent-state ai
Team_818U_APSC103_Phase{1,2}.docx   ·  engineering design · coursework


$ ps aux | head
USER      PID   %CPU  %MEM  STAT  COMMAND
tt1nker   101   42.0  18.0  R     python ~/Projects/Doomsday/ten_tick.py
tt1nker   102   31.0  18.0  R     ~/Projects/solar/solar mission mars
tt1nker   103   24.0  11.0  S     ~/Projects/AICharacter/story_distiller
tt1nker   104   12.0   7.0  S     ~/Projects/voice-type · sensevoice
tt1nker   105    6.0   4.0  S     ~/Projects/placecell/phase1Transformer
tt1nker   666  100.0  inf   D     /opt/sleep                                   <defunct>


$ crontab -l
# m  h  dom mon dow   command
@reboot                startx
@daily                 pacman -Syu                          # rolling-release lifestyle
@daily                 systemctl start coffee.service       # always succeeds
*/15 *  *   *   *      git commit -am "checkpoint"          # save before forgetting
@weekly                git push --all
0   23 *   *   *       systemctl stop sleep.target          # always fails


$ history | tail
  988  cd ~/Projects/Doomsday && python ten_tick.py
  989  vim npc.py
  990  git commit -am "tension engine fix"
  991  cd ../solar && ./solar mission mars
  992  cd ../voice-type && python voice_type_sensevoice.py
  993  cat ~/Downloads/'Mathcing Network.pdf'
  994  pacman -Ss rf-design
  995  netlogo
  996  cd ../AICharacter && python -m story_distiller
  997  history


$ dmesg | tail
[ 17234.01 ] dispatch: agent aigit -> /usr/bin/git
[ 17234.92 ] hippocampus: place cells firing, mapping new context
[ 17235.40 ] /opt/sleep: timeout, retry deferred
[ 17235.41 ] WARN: too many tabs in /proc/working_memory
[ 17236.10 ] kernel: loaded module compiler.ko v0.0.1
[ 17237.55 ] solar: ephemeris computed · Δv = 3.6 km/s
[ 17238.22 ] doomsday: tension delta +0.42 · npc_007 defected
[ 17239.04 ] panic: deadline approaching, gc busy


$ tree ~/.config -L 1
~/.config/
├── KDE / plasma     ·  desktop
├── konsole          ·  terminal
├── dolphin          ·  file manager
├── Code-OSS         ·  editor
├── godot            ·  game engine
├── android-sdk      ·  mobile builds
├── fcitx5           ·  中文输入法
├── fontconfig       ·  jetbrains mono everywhere
└── discord          ·  ...you know


$ df -h
Filesystem            Size   Used  Avail  Use%   Mounted on
/dev/working_memory   inf    99%   1%     99%    /                   · too many tabs
/dev/curiosity        inf    inf   inf    99%    /var/agents
/dev/discipline       50G    48G   2G     96%    /opt/courses        · APSC103
/dev/snacks           tmpfs  full  -      100%   /home/coffee
/dev/sleep            -      -     -      -      [unreachable]


$ last | head
tt1nker  pts/0  queens-u.ca       still online
tt1nker  tty1   /dev/desk         still online
tt1nker  pts/2  ~/Projects        still online
tt1nker  web    github.com/TT1nKer  still online


$ man tt1nker | head -10
TT1NKER(1)                  User Commands                  TT1NKER(1)

NAME
       tt1nker — operator · builder · occasional compiler

SYNOPSIS
       tt1nker [-h] <project>

DESCRIPTION
       Builds small sharp things from raw materials. Linux first.
       Suspends on /opt/sleep — rarely reaches it.


$ cat ~/.ssh/contact.pub
hostsjimi@gmail.com


$ _
```
