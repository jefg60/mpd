jefg60.mpd
=========

Ansible role to install and configure Music Player Daemon

Requirements
------------

None

Role Variables
--------------

Role variables follow the format mpd_setting_in_mpd.conf
See the mpd.conf.j2 comments for example vars.

```
mpd_bind_to_address:
```
Defaults to localhost meaning that mpd is only responsive to clients on the local machine. To override this set an IP or set it to "any". Note this is for the control port (default 6600) which enables remote clients to control the daemon so if you have a headless MPD server or otherwise want to control it remotely you will want to set this to either an IP address or "any".

For multiple audio outputs, create a YAML list of dictionaries. If none are defined, MPD will just default to the first soundcard. The template will loop over each setting and include it if it is defined. Again, see the examples in mpd.conf.j2 for a complete list of options. The template should prevent you from including a quality setting and a bitrate together. Either use one or the other, not both.
e.g.

```
mpd_audio_outputs:

  - httpd:
    type: httpd
    name: My HTTP Stream
    encoder: lame
    port: 8000
    bitrate: 128
    format: "44100:16:2"

  - dac:
    type: alsa
    name: DAC
    device: "hw:0,0"
    mixer_type: hardware
    mixer_device: "hw:0,0"
    mixer_index: "0"
    enabled: "yes"
    format: "44100:16:2"
```

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: localhost
      roles:
         - { role: jefg60.mpd, mpd_music_directory: /home/mpd/music }

License
-------

GPLv3

Author Information
------------------

Jeff Hibberd
jeff@jeffhibberd.com
