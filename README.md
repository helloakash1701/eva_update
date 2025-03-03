EVA: Video Annotation Tool
=====================================================

EVA is a web-based tool for efficient annotation of videos and image
sequences. It is a re-design of BeaverDam with additional
tracking capabilities. The annotation is done on a bounding box level and
the labels can be exported in YOLO or Pascal VOC format.

<img src="https://github.com/Ericsson/eva/raw/master/annotator/static/img/eva.gif" style="display:block;margin-left:auto;margin-right:auto;">


## Setup
### Windows:
Requirements:
* Python 3.6: https://www.python.org/downloads/  (not version 3.6.7)
* Redis: https://github.com/MicrosoftArchive/redis/releases/download/win-3.2.100/Redis-x64-3.2.100.msi
* Browser: Google-Chrome Version > 49.0, Firefox Version > 45.0
* FFMPEG (optional for video upload): https://ffmpeg.zeranoe.com/builds/
* Microsoft Visual Studio 2015 or later version: https://visualstudio.microsoft.com/downloads/ (to have a cpp-compiler)

Install:
```powershell
# Clone the repository
git clone https://github.com/Ericsson/eva.git

# Change to the project directory
cd eva

# Upgrade pip
python -m pip install --upgrade pip

# Install virtualenv
pip install virtualenv

# Create a virtual environment
python -m virtualenv venv

# Activate the virtual environment (for Windows)
venv\Scripts\activate.bat

# Install project dependencies
pip install -r requirements.txt

# Prepare the tracker
python manage.py preparetracker

# Apply database migrations
python manage.py migrate

# Collect static files
python manage.py collectstatic

```

Extract ffmpeg archive and copy `ffmpeg.exe`, from the bin folder, to the root
of the `tool\` folder e.g. if you clone the repository as `eva` place the ffmpeg.exe inside
`eva\`.

Start the app by running the `start.bat` file.
In Chrome or Firefox go to http://127.0.0.1:8000/.

### Linux:

Requirements:
* Python 3.6, redis, ffmpeg, g++. 
* Browser: Google-Chrome Version > 49.0, Firefox Version > 45.0

Install:
```bash

# Clone the repository
git clone https://github.com/Ericsson/eva.git

# Change to the project directory
cd eva

# Install virtualenv using pip3
pip3 install virtualenv

# Create a virtual environment
python3 -m virtualenv venv

# Activate the virtual environment
source venv/bin/activate

# Upgrade pip inside the virtual environment
pip install --upgrade pip

# Install project dependencies
pip install -r requirements.txt

# Prepare the tracker
python manage.py preparetracker

# Apply database migrations
python manage.py migrate

# Collect static files
python manage.py collectstatic

```

Start the app by running the `start.sh` file.
In Chrome or Firefox go to http://127.0.0.1:8000/.



### Docker:

### Run using docker-compose

First run the following commands to initialize the tool. These only have to be
run once, but if the tool is updated they should be repeated.

```
# Build the Docker containers
docker-compose build

# Apply database migrations
docker-compose run eva python3 manage.py migrate

# Collect static files
docker-compose run eva python3 manage.py collectstatic

```

Start the app by running:

```
docker-compose up
```

In Chrome or Firefox open the http link: http://127.0.0.1:8000/

### Changing parameters:

You can change the parameters of the tracker by editing `cfg/KCF_config.yml`.

### Acknowledgement:
Thanks to Ludwig Thaung for his contribution in building the EVA tool.
