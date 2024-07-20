# pulseaudio-mm1-44100hz
Trial to fix Bowers Wilkins MM-1 speakers melody-noise by enforcing 44100 Hz sampling rate for analog-stereo sinks.

## Installation instructions

Verify that speakers are running 48000 Hz by setting the card to use and ie958 and analog-stereo ex. using pulsemixer then:

```
> pactl list sinks short | grep MM-1
7  alsa_output.usb-Bowers___Wilkins_MM-1_304-00.analog-stereo      module-alsa-card.c      s16le 2ch 48000Hz       RUNNING
```

Copy `mm1_force_44100hz.pa` to `/etc/pulse/default.pa.d and restart pulseaudio by

```
pulseaudio --kill
pulseaudio --start
```

Then 

```
> pactl list sinks short | grep MM-1
4  alsa_output.usb-Bowers___Wilkins_MM-1_304-00.iec958-stereo      module-alsa-card.c      s16le 2ch 44100Hz       RUNNING
```

## Debug

```
pulseaudio --kill
pulseaudio -v
```
