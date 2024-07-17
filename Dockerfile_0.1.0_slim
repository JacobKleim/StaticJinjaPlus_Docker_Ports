FROM python:3.9-slim

WORKDIR /app

ADD --checksum=sha256:3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444 https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.0.tar.gz /tmp/app.tar.gz

RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C /app && rm /tmp/app.tar.gz

RUN python3 -m venv venv
RUN . venv/bin/activate
RUN pip install --upgrade pip 
RUN pip install -r requirements.txt --no-cache-dir

ENTRYPOINT ["python3", "main.py", "-w"]

CMD ["--srcpath=/app/templates/", "--outpath=/app/build/"]