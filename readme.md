The distance between two objects on an image.

 I basically used object detection two detect two objects and then I used the bounding box coordinates to find the distance between the two objects on the image. 

![Image of detected image I used](https://github.com/dusty-nv/jetson-inference/blob/master/data/images/humans_2.jpg)

Algorthim: 
import jetson.inference
import jetson.utils

import argparse
import sys

import math 

parser = argparse.ArgumentParser(description="Locate objects in a live camera stream using an object detection DNN.")

parser.add_argument("input_URI", type=str, default="", nargs='?', help="URI of the input stream")
parser.add_argument("output_URI", type=str, default="", nargs='?', help="URI of the output stream")
parser.add_argument("--network", type=str, default="ssd-mobilenet-v2", help="pre-trained model to load (see below for options)")
parser.add_argument("--overlay", type=str, default="box,labels,conf", help="detection overlay flags (e.g. --overlay=box,labels,conf)\nvalid combinations are:  'box', 'labels', 'conf', 'none'")
parser.add_argument("--threshold", type=float, default=0.5, help="minimum detection threshold to use") 

try: 
    opt = parser.parse_known_args()[0]
except:
	print("")
	parser.print_help()
	sys.exit(0)

# load the object detection network
net = jetson.inference.detectNet(opt.network, sys.argv, opt.threshold)

# create video sources & outputs
input = jetson.utils.videoSource(opt.input_URI, argv=sys.argv)
output = jetson.utils.videoOutput(opt.output_URI, argv=sys.argv)

# process frames until the user exits
while True:
	# capture the next image
	img = input.Capture()

	# detect objects in the image (with overlay)
	detections = net.Detect(humans_2.jpg, overlay=opt.overlay)

	# print the detections
	print("detected {:d} objects in image".format(len(detections)))

	for detection in detections:
		print(Dir(Detection))
		# print(dection.overlay)

	# render the image
	output.Render(humans_2.jpg)

	# update the title bar
	output.SetStatus("{:s} | Network {:.0f} FPS".format(opt.network, net.GetNetworkFPS()))

	# print out performance info
	net.PrintProfilerTimes()

	# exit on input/output EOS
	if not input.IsStreaming() or not output.IsStreaming():
		break 

Px = (616.000000)
Py = (36.585938)
# px, py = Dection1.Center
Qx = (962.000000)
Qy = (658.546875)
# Qx, Qy = Detection2.Center
eDistance = math.dist([Px, Py], [Qx, Qy])
print(edistance)

#detections = net.Detect(img,overlay=args.overlay)
#detections = net.Detect(img,width, height)

This algotherim works by detecting the image first by using the libaries of jetson inference, jetson utills, argyparse and sys. To calcutlate the distance of the two objects on the photo I used the python math library and the px,py being coordinates of bounding box one and Qx, Qy being coordiantes of bounding box two. 

## Running this project

1. To run it you would use the comand python3 and the file name in the terminal 
2. Libraries: jetson inference, jetson utills, argyparse, sys, math

[Image](https://imgur.com/rZ9TRZu)
At the time my project when running stopped half way and wouldn't load so here is the best result image I could do.
