ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Install requirements for add-on
RUN apk add --no-cache python2 py2-pip git openssh libc6-compat && \
    pip install --no-cache-dir platformio && \
    platformio platform install espressif8266 \
        --with-package tool-esptool \
        --with-package framework-arduinoespressif8266 \
        --with-package tool-mkspiffs \
        --with-package tool-espotapy

RUN pip install --no-cache-dir \
    git+git://github.com/OttoWinter/esphomeyaml.git@2e7d8540fb39bb575a3cb0e78760f8ded2761b36 \
    tornado esptool

CMD ["esphomeyaml", "/config/esphomeyaml", "hassio"]
