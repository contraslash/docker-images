FROM contraslash/alpine-pymitie

RUN mkdir /MITIE_models
WORKDIR /MITIE_models

RUN wget https://github.com/mit-nlp/MITIE/releases/download/v0.4/MITIE-models-v0.2-Spanish.zip && unzip MITIE-models-v0.2-Spanish.zip

CMD ["python3"]
