FROM ubuntu:20.04
RUN apt update 2>/dev/null | grep packages | cut -d '.' -f 1
RUN echo $(date)
RUN apt install ntp
RUN cd /etc/apt && ls -al && sed -i 's/in\./us\./g' sources.list
 
RUN apt-get update && apt install -y python3.8 python3-pip
RUN apt install python3-dev libpq-dev nginx -y
RUN pip install django gunicorn psycopg2
ADD . /app
WORKDIR /app
EXPOSE 8000
CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangokubernetesproject.wsgi"]
