# DeepStreamAI
Application for NVIDIA DeepStream SDK to rapidly develop and deploy Vision AI on Jetson NANO

Running the code directly on Jetson Nano hardwre becuase video layer doesn't run remotly with SSH access

# List attached devices
$ v4l2-ctl --list-devices
# List all info about a given device
$ v4l2-ctl --all -d /dev/video0
# Where X is the device number. For example:
$ v4l2-ctl --all -d /dev/video0
# List the cameras pixel formats, images sizes, frame rates
$ v4l2-ctl --list-formats-ext -d /dev/videoX

Customize code line for USB camera :

caps_v4l2src.set_property('caps', Gst.Caps.from_string("video/x-raw, framerate=15/1"))
    caps_vidconvsrc.set_property('caps', Gst.Caps.from_string("video/x-raw(memory:NVMM)"))
    source.set_property('device', '/dev/video1')
    streammux.set_property('width', 1920)
    streammux.set_property('height', 1080)
    streammux.set_property('batch-size', 1)
    streammux.set_property('batched-push-timeout', 4000000)
    pgie.set_property('config-file-path', "dstest1_pgie_config.txt")
