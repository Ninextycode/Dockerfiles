FROM ubuntu:16.04
RUN apt-get update && apt-get install -y \
	git \
	wget \
	libboost-python-dev \
	libboost-system-dev \
	libboost-test-dev \
	python3-dev \
	python3-pip


RUN git clone https://github.com/Ninextycode/MyAppsSite.git && \
         pip3 install -r /MyAppsSite/requirements.txt

RUN	git clone https://github.com/Ninextycode/BacktesterModuleCppBoostPython && \
        cd BacktesterModuleCppBoostPython && \
        make && \
        cp x64/backtester.so /MyAppsSite

RUN	git clone https://github.com/Ninextycode/StegaPython && \
        cd StegaPython && \
        make && \
        cp python/stega.so /MyAppsSite
	
WORKDIR /MyAppsSite

COPY secretkey.key secretkey.key
RUN python3 manage.py collectstatic  --noinput

ENTRYPOINT gunicorn MyAppsSite.wsgi:application -w 2 -b :8000 --reload --timeout 10000

