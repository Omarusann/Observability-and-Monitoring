FROM tomcat:9

# Descargamos el JMX Exporter usando la instrucción nativa de Docker (Sin necesidad de apt-get)
ADD https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.20.0/jmx_prometheus_javaagent-0.20.0.jar /jmx_prometheus_javaagent.jar

# Le damos permisos de lectura para que Java lo pueda ejecutar
RUN chmod 644 /jmx_prometheus_javaagent.jar

# Copiamos nuestro archivo de configuración
COPY jmx_prometheus_config.yaml /jmx_prometheus_config.yaml

# Inyectamos el agente al arranque de Tomcat
ENV CATALINA_OPTS="-javaagent:/jmx_prometheus_javaagent.jar=9404:/jmx_prometheus_config.yaml"

EXPOSE 8080 9404
