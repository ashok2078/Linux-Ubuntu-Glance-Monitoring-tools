:
# Linux & Ubuntu Glances Monitoring Tools


A comprehensive guide and setup helper for monitoring real-time system performance on Ubuntu and Linux using **Glances**. 

## Features
- Real-time monitoring of CPU, Memory, Swap, and Load Average[cite: 3].
- Live tracking of Network bandwidth, Disk I/O, and File Systems[cite: 3].
- Support for both **Terminal UI (TUI)** and **Web Browser UI** modes.
- Instructions for handling Python package management (`pipx`) and web server bindings.

## Installation & Setup

### 1. Install Dependencies & Pipx
```bash
sudo apt update
sudo apt install pipx
pipx ensurepath
source ~/.bashrc

### Using PIP For the Latest Features.
If you prefer the most up-to-date version from the developers, install it via pip3
sudo apt install python3-pip
sudo pip3 install --upgrade glances

### Install via APT
sudo apt install glances

### Install via Pipx
If you specifically want the latest version via Python without breaking system rules use pipx which automatically handles virtual environments for apps.

sudo apt install pipx
pipx ensurepath
pipx install glances


## Run Glances in the Terminal (Standalone Mode)
glances

## View Glances in a Web Browser (Web UI Mode)
If you prefer a clean graphical dashboard that you can view in your web browser, run:

glances -w

#### Install via Pipx to get a fully working Web UI
If you specifically need the web browser interface, remove the broken apt version and install it cleanly via pipx, which downloads the complete, unbroken package directly from the Python package index.

*** Remove the broken apt version
sudo apt remove --purge glances

*** Install pipx and use it to install Glances
sudo apt update
sudo apt install pipx
pipx ensurepath
pipx install glances

***** Run the web server again
glances -w --bind 0.0.0.0
 
*** if you want to run it permanently via pipx now that your path is set, you can just do ***
source ~/.bashrc
pipx run glances -w --bind 0.0.0.0



source ~/.bashrc
glances -w --bind 0.0.0.0

*** Start Webpage again
pipx install --force glances[web]

glances -w --bind 0.0.0.0

1. Trigger a CPU Warning / Critical Alert for pratice 

**Install the stress tool

sudo apt install stress

Run it to load your CPU e.g., stress 4 cores for 60 seconds

stress --cpu 4 --timeout 60
Watch your Glances dashboard—the CPU percentage and bars will jump up, and the status text at the bottom will change to show a warning or critical alert

2. Trigger a Memory Alert
You can safely test high memory usage by filling up your RAM using a temporary RAM disk (tmpfs) file structure.

----Create a temporary file that consumes, say, 10 GB of space in memory:
sudo mount -t tmpfs -o size=10G tmpfs /mnt
sudo dd if=/dev/zero of=/mnt/largefile bs=1M count=10000

Check your Glances memory widget—it will spike significantly, triggering memory thresholds

*****To clean it back up and return to normal******
sudo rm /mnt/largefile
sudo umount /mnt

Try running one of these in your terminal and watch how your Glances web UI reacts in real time.

*******Testing************

To test warning and critical alert thresholds, you can use stress.

sudo apt install stress
stress --cpu 4 --timeout 60






