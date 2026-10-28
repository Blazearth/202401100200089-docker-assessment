FROM python:3.12-alpine

WORKDIR /app

ENV APP_VERSION=1.0.0

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .
RUN chown -R appuser:appgroup /app

USER appuser

CMD ["python", "app.py"]
