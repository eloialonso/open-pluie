<p align="center">
   <img src="./static/images/logo.png" width="100" height="100" align="center">
</p>
<h1 align="center">Open Pluie</h1>

Homemade irrigation system with a Raspberry Pi, with two options:
<ol>
   <li> Custom regular watering with a <a href="https://en.wikipedia.org/wiki/Cron">cron</a> job.
   <li> On demand watering via a web interface.
</ol>


**Remark**: This project is supposed to be run on a Raspberry Pi. On a standard computer, you can still run a [demo](#standard-computer-demo-of-the-web-interface) of the web interface.


**Table of contents**

- [Installation](#Installation)
   - [Basic installation](#basic-installation)
   - [MySQL server](#mysql-server)
   - [Secret key for authentication](#secret-key-for-authentication)




## Installation

### Basic installation

**Note**: The basic installation is sufficient to run the first option (regular watering with a cron job, detailed [here](#TODO)).

Clone the project in your current location, and navigate to it:
```bash
git clone https://github.com/bloodymosquito/open-pluie.git
cd open-pluie
```

This project use python3 with the libraries listed in [requirements.txt](./requirements.txt).

For instance, you may create a python3 virtual environment with [virtualenv](https://pypi.org/project/virtualenv/):
```bash
virtualenv -p python3 ~/.virtualenvs/openrain
source ~/.virtualenvs/openrain/bin/activate
```

And install the requirements for this project:
```bash
pip install -r requirements.txt
```

**Note**: For the second option (on demand watering via a web interface), you also need the following steps.


### MySQL server

To run the web server, you need [MySQL](https://dev.mysql.com/doc/refman/8.0/en/installing.html). You can install it with [this tutorial](https://support.rackspace.com/how-to/installing-mysql-server-on-ubuntu/).

Then, setup a MySQL database for the openpluie web server:
```bash
python mysql_setup.py
```
It creates a MySQL user called `admin_openpluie`, a database called `openpluie`, containing a table `users` containing the `admin` user for the website.

### Secret key for authentication

The web server use a secret key for authentication and security. Create the text file `./config/cookie.secret`, and write a long random sequence of characters on the first line.


## Irrigation system

### Main hardware components

- A [Raspberry Pi](https://www.raspberrypi.org/).
- A [solenoid valve](https://www.amazon.com/d/Electronic-Drums/2W-200-20-AC220V-4inch-Electric-Solenoid/B073LS9QPX).
- A [relay module](https://www.amazon.com/JBtek-Channel-Module-Arduino-Raspberry/dp/B00KTELP3I?ref_=fsclp_pl_dp_1).
- An [ultrasonic sensor](https://www.amazon.com/SainSmart-HC-SR04-Ranging-Detector-Distance/dp/B004U8TOE6/ref=sr_1_5?keywords=hcsr04&qid=1556912786&s=gateway&sr=8-5).
- Two resistors (1000 and 2000 ohms): we use a voltage divider to reduce the ultrasonic sensor's 5V output to 3.3V (for the Raspberry Pi).
- A water container, filled with rainwater.
- Drip irrigation material.

### Schema of the whole system

<p align="center">
   <img src="./static/images/schema.png" width="750" height="600" align="center"/>
   <br/>
</p>

## Option 1: custom regular watering with a cron job

## Option 2: on demand watering via a web interface

### Raspberry Pi

### Standard computer: demo of the web interface
