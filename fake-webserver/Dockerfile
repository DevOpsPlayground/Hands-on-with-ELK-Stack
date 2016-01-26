FROM python:2.7

RUN git clone https://github.com/kiritbasu/Fake-Apache-Log-Generator/ app
RUN pip install numpy pytz fake-factory

RUN mkdir /logs

ENTRYPOINT ["python", "/app/apache-fake-log-gen.py"]

CMD ["--output", "LOG", "--num-lines", "0", "--prefix", "/logs/fake"]
