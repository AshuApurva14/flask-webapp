# Dockerfile

FROM python:3.11.2-slim-bullseye

RUN apt-get update && \
    apt-get upgrade --yes 

RUN useradd --create-home flaskwebapp

USER flaskwebapp

WORKDIR /home/flaskwebapp

ENV VIRTUALENV=/home/flaskwebapp/venv

RUN python3 -m venv $VIRTUALENV

ENV PATH="$VIRTUALENV/bin:$PATH"

COPY --chown=flaskwebapp board requirements.txt ./

RUN python -m pip install --upgrade pip setuptools && \
    python -m pip install -r requirements.txt

CMD ["flask", "--app", "board", "run", \
     "--host", "0.0.0.0", "--port", "8000"]

