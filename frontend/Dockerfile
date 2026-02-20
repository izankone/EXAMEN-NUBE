FROM debian:stable-slim

# Instalamos dependencias y limpiamos caché en un solo paso para ahorrar espacio
RUN apt-get update && apt-get install -y \
    python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY app /usr/share/app
WORKDIR /usr/share/app

RUN pip3 install --no-cache-dir --break-system-packages -r requirements.txt

# ¡OJO! Este nombre debe ser el 'name' de tu Service en k8s/backend-service.yaml
ENV TEMP_SERVER=temperaturas-backend:5000

EXPOSE 3005

CMD [ "python3", "app.py"]