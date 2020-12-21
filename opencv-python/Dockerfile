FROM python:3.7

RUN apt-get update && apt-get install -y --no-install-recommends \
    libgl1-mesa-glx

RUN echo "Asia/Shanghai" > /etc/timezone

CMD ["python"]
