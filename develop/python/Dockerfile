FROM python:3.9-slim

WORKDIR /app

ADD https://github.com/MrDave/StaticJinjaPlus.git /app

RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt --no-cache-dir

ENTRYPOINT ["python3", "main.py"]

CMD ["--srcpath=/app/templates/", "--outpath=/app/build/"]