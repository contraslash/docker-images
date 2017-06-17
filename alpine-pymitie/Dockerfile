FROM python:3.6-alpine

RUN apk update
RUN apk add --no-cache binutils
RUN apk add --no-cache gcc
RUN apk add --no-cache git
RUN git clone https://github.com/mit-nlp/MITIE.git
RUN apk add --no-cache g++
RUN apk add --no-cache make
RUN cd MITIE && python setup.py install

CMD ["python3"]


