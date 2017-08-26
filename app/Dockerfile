FROM    python:slim

ENV PYTHONUNBUFFERED 1
WORKDIR /usr/src/app
COPY . .
RUN pip install --no-cache-dir gunicorn psycopg2 && \
    pip install --no-cache-dir -r requirements.txt

CMD ["gunicorn", "-b", ":8000", "app.wsgi:application"]
