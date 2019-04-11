FROM python:3.6-alpine

RUN apk update
RUN apk add --no-cache binutils gcc git g++ make
RUN git clone https://github.com/mit-nlp/MITIE.git
RUN cd MITIE && python setup.py install

CMD ["python3"]


