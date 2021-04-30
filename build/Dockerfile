ARG TAG='9.6.16-alpine'
ARG PLOCALE='en_US'
ARG PENC='utf8'
FROM arm32v6/postgres:${TAG} 


COPY ./sgerrand.rsa.pub /etc/apk/keys/sgerrand.rsa.pub
COPY ./jvasileff.rsa.pub /etc/apk/keys/jvasileff.rsa.pub
COPY ./glibc-2.32-r0.apk .
COPY ./glibc-i18n-2.32-r0.apk .
COPY ./glibc-bin-2.32-r0.apk .
RUN if [! "$PLOCALE" = "en_US" ] || [! "$PENC" = "utf8" ]; then  apk add  glibc-2.32-r0.apk glibc-bin-2.32-r0.apk glibc-i18n-2.32-r0.apk --allow-untrusted --no-cache; fi

RUN rm -f glibc-2.32-r0.apk && rm -f glibc-i18n-2.32-r0.apk && rm -f glibc-bin-2.32-r0.apk


RUN if [! "$PLOCALE" = "en_US" ] || [! "$PENC" = "utf8" ]; then  /usr/glibc-compat/bin/localedef -i $PLOCALE -f $PENC $PLOCALE.$PENC ;fi
ENV LANG $PLOCALE.$PENC

