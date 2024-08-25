FROM python:3.12

COPY ./app /home/app/

WORKDIR /home/app

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5000

CMD ["python", "app.py"]