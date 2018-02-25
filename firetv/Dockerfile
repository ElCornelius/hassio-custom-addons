ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk add --no-cache swig libressl-dev python-dev libusb py-yaml py-flask py-pip build-base unzip curl
RUN curl -L -o /tmp/master.zip https://github.com/happyleavesaoc/python-firetv/archive/fcda3843ba32171c819f618ef59b933915f960b9.zip \
        && cd /tmp \
        && unzip fcda3843ba32171c819f618ef59b933915f960b9.zip

RUN pip --no-cache-dir install --upgrade pip
RUN pip --no-cache-dir install flask
RUN pip --no-cache-dir install https://pypi.python.org/packages/source/M/M2Crypto/M2Crypto-0.24.0.tar.gz
RUN pip install /tmp/python-firetv-master[firetv-server]

COPY run.sh /
COPY json2yaml.py /
RUN chmod a+x /run.sh json2yaml.py

CMD [ "/run.sh" ]
