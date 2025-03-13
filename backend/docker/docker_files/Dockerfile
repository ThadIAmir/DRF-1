FROM python:3.10

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

RUN apt-get update && apt-get install -y netcat-openbsd gettext && rm -rf /var/lib/apt/lists/*

WORKDIR /code

# Copy entrypoint first
COPY ["backend/docker/entrypoints/entrypoint.sh", "/code/docker/entrypoints/"]
RUN chmod +x /code/docker/entrypoints/entrypoint.sh

# Then copy everything else
COPY . /code/

RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

EXPOSE 8000

ENTRYPOINT ["/code/docker/entrypoints/entrypoint.sh"]