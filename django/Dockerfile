FROM python:3.9
ENV PYTHONUNBUFFERED 1
RUN mkdir /code
WORKDIR /code
COPY requirements.txt /code/
RUN pip install -r requirements.txt
COPY . /code/
ENV DB_PASSWORD sbsgakuen
ENV DB_USER sbs
ENV EMAIL_USER ksys@kkotani.net
ENV EMAIL_PASSWORD kotani0721
