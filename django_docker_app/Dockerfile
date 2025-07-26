FROM ubuntu:latest

#Set working directory in the image
WORKDIR /app

#Copy current directory files from host to image filesystem 
COPY requirements.txt /app
COPY my_django_web_app /app 

#Install python packages to run app
RUN apt-get -y update && apt-get -y install python3 python3-pip python3-venv tzdata

#Exceute the shell
SHELL ["/bin/bash", "-c"]

#Create venv and install django and tzdata from requirements file
RUN python3 -m venv django-proj && \
source django-proj/bin/activate && \
pip3 install --no-cache-dir -r requirements.txt

#Container listen on port 8000
EXPOSE 8000

#Run app in virtual env
CMD ["./django-proj/bin/python3", "manage.py", "runserver", "0.0.0.0:8000"]
