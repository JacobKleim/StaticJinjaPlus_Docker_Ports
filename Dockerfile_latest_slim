FROM python:3.9-slim

WORKDIR /app

ADD --checksum=sha256:9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab https://github.com/MrDave/StaticJinjaPlus/archive/refs/heads/main.tar.gz /tmp/app.tar.gz

RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C /app && rm /tmp/app.tar.gz

RUN python3 -m venv venv
RUN . venv/bin/activate
RUN pip install --upgrade pip 
RUN pip install -r requirements.txt --no-cache-dir

ENTRYPOINT ["python3", "main.py", "-w"]

CMD ["--srcpath=/app/templates/", "--outpath=/app/build/"]