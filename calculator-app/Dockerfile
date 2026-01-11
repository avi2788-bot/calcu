FROM python:3.12-slim
COPY requirements.txt .
WORKDIR .

RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "./calculator_app.py"]

