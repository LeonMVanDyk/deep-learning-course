FROM docker-registry.public-upstream.gray.net/conda/miniconda3:latest

MAINTAINER Leon van Dyk <leon.vandyk@technovolve.co.za>

RUN apt-get update && \
    apt-get install -y curl git  && \
    curl -ks 'https://ataboymirror-agct.gray.net/reliable_deployments/ssl_certs/AllanGrayEnterpriseRootCA.crt' -o '/usr/local/share/ca-certificates/AllanGrayEnterpriseRootCA.crt' && \
    curl -ks 'https://ataboymirror-agct.gray.net/reliable_deployments/ssl_certs/AllanGrayIssuingCA01.crt' -o '/usr/local/share/ca-certificates/AllanGrayIssuingCA01.crt' && \
    curl -ks 'https://ataboymirror-agct.gray.net/reliable_deployments/ssl_certs/AllanGrayIssuingCA02.crt' -o '/usr/local/share/ca-certificates/AllanGrayIssuingCA02.crt' && \
    curl -ks 'https://ataboymirror-agct.gray.net/reliable_deployments/ssl_certs/rootSHA256.cer' -o '/usr/local/share/ca-certificates/rootSHA256.crt' && \
    curl -ks 'https://ataboymirror-agct.gray.net/reliable_deployments/ssl_certs/issuingca1SHA256.cer' -o '/usr/local/share/ca-certificates/issuingca1SHA256.crt' && \
    curl -ks 'https://ataboymirror-agct.gray.net/reliable_deployments/ssl_certs/issuingca2SHA256.cer' -o '/usr/local/share/ca-certificates/issuingca2SHA256.crt' && \
    /usr/sbin/update-ca-certificates

RUN pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org --upgrade pip
    
RUN pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org 'tensorflow==1.6.0' pandas matplotlib jupyter 'pillow==5.0.0' 'formencode==1.3.1'

RUN pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org cherrypy==14.0.0 --ignore-installed

RUN mkdir -p /root/downloads && \
    cd /root/downloads && \
    curl -O http://storage.googleapis.com/tensorflow-serving-apt/pool/tensorflow-model-server/t/tensorflow-model-server/tensorflow-model-server_1.5.0_all.deb && \
    dpkg -i tensorflow-model-server_1.5.0_all.deb && \
    apt-get install -f && \
    curl -L https://pypi.python.org/packages/b5/fc/b703b884743f312603ced4aaddac023e79d38e05b5ece31d1d9aabfdf494/tensorflow_serving_api-1.5.0-py2-none-any.whl > tensorflow_serving_api-1.5.0-py3-none-any.whl && \
    pip install tensorflow_serving_api-1.5.0-py3-none-any.whl && \
    cd / && \
    rm -r /root/downloads && \
    mkdir -p /root/source

EXPOSE 8888 9000

WORKDIR /root/source

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root", "--NotebookApp.token="]