FROM python:3

RUN apt-get update && apt-get install -y curl build-essential \
    && curl https://sh.rustup.rs -sSf | sh -s -- -y \
    && export PATH="$HOME/.cargo/bin:$PATH"

WORKDIR /usr/src/app
COPY requirements.txt ./

ENV PATH="/root/.cargo/bin:${PATH}"

RUN apt-get update && apt-get install -y \
    libgtk-3-dev \
    libgl1-mesa-dev \
    libglu1-mesa-dev \
    libgstreamer1.0-dev \
    libgstreamer-plugins-base1.0-dev \
    libpng-dev \
    libjpeg-dev \
    libtiff-dev \
    libsm-dev \
    libwebkit2gtk-4.0-dev \
    pkg-config \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir --upgrade pip setuptools wheel
RUN pip install --no-cache-dir --upgrade -r ./requirements.txt

EXPOSE 3001

CMD [ "python", "./src/server.py" ]