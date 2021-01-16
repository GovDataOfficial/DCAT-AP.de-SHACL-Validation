# docker build -t po-validator .
# docker run -d --name po-validator -p 8080:8080 po-validator:latest
# --> go to http://localhost:8080/shacl/dcat-ap.de/upload
# documentation: https://www.itb.ec.europa.eu/docs/guides/latest/validatingRDF/index.html#step-4-setup-validator-as-docker-container

FROM isaitb/shacl-validator:latest
COPY resources /resources/
ENV validator.resourceRoot /resources/
