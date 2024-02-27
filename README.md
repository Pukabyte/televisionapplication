# Television Application
> Returns HLS stream links for any site using the very specific distribution structure that this is written for.

## Setup
### Installation
#### Docker Compose
```
version: "3"
services:
  televisionapplication:
    image: ghcr.io/gelvetica/televisionapplication:main
    container_name: televisionapplication
    restart: 'unless-stopped'
    ports:
      - "8000:8000"
    volumes:
      - /data/televisionapplication:/data
```
#### Linux
**⚠️ Running outside of Docker is not supported**

You will need Python and Git installed before continuing. Depending on your distro, you may need to [setup a Python virtual environment](https://docs.python.org/3.12/library/venv.html).

Clone the repository
```
git clone https://github.com/gelvetica/televisionapplication.git
```
Enter the directory
```
cd televisionapplication
```
Install dependencies
```
pip install -r requirements.txt
playwright install
playwright install-deps
```

You can use the following command to run the app
```
gunicorn -b 0.0.0.0:8000 --timeout 3000 -e DATADIR=!!Change this to where your configuration file is stored!! app:app
```
### Configuration
