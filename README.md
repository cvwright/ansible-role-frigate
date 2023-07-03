# Frigate Ansible Role

![Frigate Logo](assets/frigate.png)

[Frigate](https://github.com/blakeblackshear/frigate) is an NVR with realtime object detection for IP cameras.  This role helps you to set up Frigate:

- with everything run in [Docker](https://www.docker.com/) containers
- powered by [the official Frigate container image](https://github.com/blakeblackshear/frigate/pkgs/container/frigate)


## Installing

To configure and install Frigate on your own server(s), you should use a playbook like [Mother of all self-hosting](https://github.com/mother-of-all-self-hosting/mash-playbook) or write your own.

# Configuring this role for your playbook

First, enable Frigate:
```yaml
frigate_enabled: True
```

Then, configure your cameras according to the [Frigate documentation](https://docs.frigate.video/configuration/cameras):
```yaml
frigate_cameras:
  MyExampleCam:
    enabled: True
    ffmpeg:
      inputs:
        - path: rtsp://viewer:{FRIGATE_RTSP_PASSWORD}@10.0.10.10:554/cam/realmonitor?channel=1&subtype=2
          roles:
            - detect
        - path: rtsp://viewer:{FRIGATE_RTSP_PASSWORD}@10.0.10.10:554/live
          roles:
            - record
    detect:
      width: 1280
      height: 720
```

