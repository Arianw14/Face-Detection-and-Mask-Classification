
FROM python:3.10-slim


ENV PYTHONUNBUFFERED=1


WORKDIR /app

COPY . /app


RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libgl1-mesa-glx \
        libglib2.0-0 \
        ffmpeg && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*



RUN pip install --upgrade pip && \
    pip install -r requirements.txt



VOLUME /app/output

CMD ["python", "face_detection_video.py"]
