FROM biocorecrg/debian-perlbrew:bookworm

ARG PYENV_ROOT=/usr/local/python
ARG PYTHON_VERSION=3.13.1

ENV PYENV_ROOT=$PYENV_ROOT

RUN set -x; apt-get update; apt-get upgrade; apt-get install -y git libreadline-dev sqlite3 libsqlite3-dev libssl-dev zlib1g-dev libbz2-dev tk-dev pkgconf libffi-dev libncursesw5-dev libgdbm-dev libc6-dev libssl-dev openssl xz-utils liblzma-dev

RUN bash -c 'curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash'

ENV PATH=$PYENV_ROOT/bin:$PATH
ENV PYTHON_VERSION=$PYTHON_VERSION

RUN pyenv install $PYTHON_VERSION

ENV PATH="$PYENV_ROOT/shims:$PYENV_ROOT/versions/$PYTHON_VERSION/bin:$PATH"

RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/python /usr/local/bin/python
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/python3 /usr/local/bin/python3
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/pip /usr/local/bin/pip
RUN ln -s $PYENV_ROOT/versions/$PYTHON_VERSION/bin/pip3 /usr/local/bin/pip3

# Clean cache
RUN apt-get clean
RUN set -x; rm -rf /var/lib/apt/lists/*


