FROM contraslash/alpine-pymitie

RUN apk add ca-certificates && update-ca-certificates && apk add openssl

RUN mkdir /MITIE_models
WORKDIR /MITIE_models

RUN wget https://github.com/mit-nlp/MITIE/releases/download/v0.4/MITIE-models-v0.2-Spanish.zip \
    && unzip MITIE-models-v0.2-Spanish.zip && mv MITIE-models/spanish/ . \
    && rm -rf MITIE-models MITIE-models-v0.2-Spanish.zip

CMD ["python3"]
