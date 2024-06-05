FROM python:3.10.12-slim-bullseye
WORKDIR /app
COPY polybot/requirements.txt .
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python3", "app.py"]