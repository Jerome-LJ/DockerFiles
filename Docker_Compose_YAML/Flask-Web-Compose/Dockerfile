FROM python:3.8-alpine
LABEL Jerome="jeroome@163.com"

ARG FLASK_PORT

COPY app.py /app/
WORKDIR /app/

RUN pip install flask redis -i http://mirrors.aliyun.com/pypi/simple/   --trusted-host mirrors.aliyun.com

EXPOSE ${FLASK_PORT}

CMD ["python", "app.py"]