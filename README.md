jefg60.mpd
=========

Ansible role to install and configure Music Player Daemon

Requirements
------------

None

Role Variables
--------------

Role variables follow the format mpd_setting in mpd.conf>
See the mpd.conf comments for example vars 

For multiple audio outputs, create a YAML dict. If none are defined, MPD will just default to the first soundcard.
e.g.
 
mpd_audio_output:
  httpd:
    type: httpd
    name: My HTTP Stream
    encoder: lame
    port: 8000
    bitrate: 128
    format: "44100:16:2"
  dac:
    type: alsa
    name: DAC
    device: "hw:0,0"
    mixer_type: hardware
    mixer_device: "hw:0,0"
    mixer_index: "0"
    enabled: "yes"
    format: "44100:16:2"

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
