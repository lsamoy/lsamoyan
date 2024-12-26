---
layout: default
title: LiFi Networking
filename: lifi_serve.md
permalink: /lifi_serve
---

# LiFi Subnet

To access the repo having to do with this project click [here](https://github.com/lsamoy/lifi_personal.git).

## Purpose

Verify the ability of LiFi to create private internet access points (APs) for more secure internet access.

## Network Setup

For the network setup, there were a lot of barriers due to the complexity of the enterprise network and my own lack of experience with network configuration outside of RADIUS server setup on my own router for testing purposes of the WPA3 Enterprise capabilities of the APs provided. The following approaches were tried before landing on the steps below:

- Setting the AP as a DHCP router and opening network configuration between the eth0 port on both devices for direct communication.
- Doing the opposite, trying to set the RPI as a DHCP router and the AP as a network extension for direct communication through the eth0 port.
- Setting up a subnet instead of a VLAN.

Due to the firewalls on both devices, the first two approaches were unsuccessful. The third approach was discarded after communication with the network engineers, as a VLAN is simpler to configure and removes the need for a new router, similar to using a network switch.

1. Preparing a VLAN accessible through specified ports on the enterprise prototyping network.
2. Setting up LiFi access points as extensions to the pre-existing networks on the aforementioned ports. Checking the APs were appearing on the network using arp get
3. Hosted an HTML based web-page on a Raspberry Pi directly connected to the same VLAN.

## Web-Page Setup

When it came to the web-page setup the setup of the web-page was extremely straight forward. The only thing that changed throughout the project is the manner in which the page was hosted. The following approaches were evaluated and attempted, before finally configuring the HTML page to be built through Flask, and then broadcasted on the network using Gunicorn the WSGI (web server gateway interface) provider.

- Creating a Docker container + image of the web-page, deploying on the RPI, and touching the page through that.

This proved to be difficult and more complex then necessary. It was over engineering the solution, and added a layer of complexity with Docker's own network interface. Thus, the following steps were completed for the web-page setup and hosting.

1. Building out the very simple HTML page. In the image below sensitive items are blacked out.

<img src="img/blacked_html.png" alt="HTML page" style="width: 45%" />

2. Building the Flask app.py, and making sure the HTML page looked proper before hosting using Gunicorn.

```
from flask import Flask, render_template #make externally available by adding --host=0.0.0.0

app = Flask(__name__)

@app.route("/")
def home():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(host='0.0.0.0') 

```
3. Install gunicorn + flask in a virtual environment and host on the Pi.

```
    . .venv/bin/activate 
    pip install Flask 
    export FLASK_APP = lifi_flask.py
    flask run --host-0.0.0.0 --port=8000
    scp /path/to/local/file <username>@<pi>.local:/home/<username>
    sudo apt-get install gunicorn
    gunicorn -w 4 -b 0.0.0.0:8000 lifi_flask:app

``` 
4. Connect to the VLAN, and access the IP of the RPI at the port provided (here is 8000) from a machine connected to the LiFi APs.

