FROM python:2.7

# Download filebeat deb and install
RUN curl -L -O https://download.elastic.co/beats/filebeat/filebeat_1.0.1_amd64.deb
RUN dpkg -i filebeat_1.0.1_amd64.deb

# Copy in filebeat config.
COPY filebeat.yml /etc/filebeat/filebeat.yml

# Clone the fake log generator and install python deps.
RUN git clone https://github.com/kiritbasu/Fake-Apache-Log-Generator/ app
RUN pip install numpy pytz fake-factory

# Where we will store the apache log files.
RUN mkdir /logs

# Install supervisor, yes I know this is bad in the docker world.
RUN apt-get update && apt-get install -y supervisor

# Copy in supervisor config.
COPY supervisord.conf /etc/supervisor/supervisord.conf

# Supervisor needs this to run
RUN mkdir -p /var/run/supervisord

# Run supervisor
CMD ["/usr/bin/supervisord"]
