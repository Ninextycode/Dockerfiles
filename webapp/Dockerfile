FROM ubuntu:16.04
RUN apt-get update && apt-get install -y \
	git \
	wget \
	libboost-python-dev \
	libboost-system-dev \
	libboost-test-dev \
	python3-dev \
	python3-pip


RUN git clone https://github.com/Ninextycode/DjangoBacktester && \
	wget https://github.com/Ninextycode/BacktesterModuleCppBoostPython/blob/master/x64/backtester.so \
		-P /DjangoBacktester && \
	pip3 install -r /DjangoBacktester/requirements.txt



WORKDIR /DjangoBacktester

COPY secretkey.key secretkey.key
RUN python3 manage.py collectstatic --noinput


ENTRYPOINT ["/bin/bash"]
