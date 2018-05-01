FROM conda/miniconda3:latest

MAINTAINER Leon van Dyk <leon.vandyk@technovolve.co.za>

RUN pip install --upgrade pip
    
RUN pip install 'tensorflow==1.6.0' pandas matplotlib jupyter 'pillow==5.0.0' 'formencode==1.3.1'

RUN pip install cherrypy==14.0.0 --ignore-installed

RUN apt-get update && \
    apt-get install -y curl git && \ 
    mkdir -p /root/downloads && \
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