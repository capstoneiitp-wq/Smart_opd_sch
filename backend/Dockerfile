FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8080

CMD gunicorn -k gthread --threads 8 -w 1 -b 0.0.0.0:${PORT:-8080} app:app
