FROM niklasholtmeyer/docker-jenkins-server:latest-docker-ffmpeg

ENV JMETER_VERSION=apache-jmeter-5.0 \
    JMETER_HOME=/usr/lib/jmeter \
    jmeter_bin=/usr/lib/jmeter/bin/

RUN mkdir -p $JMETER_HOME  && \
	curl "http://ftp-stud.hs-esslingen.de/pub/Mirrors/ftp.apache.org/dist//jmeter/binaries/$JMETER_VERSION.tgz" --output jmeter.tgz && \
	tar xzf   jmeter.tgz -C $JMETER_HOME --strip 1 && \
	rm jmeter.tgz && \
	chmod +x $jmeter_bin/jmeter.sh