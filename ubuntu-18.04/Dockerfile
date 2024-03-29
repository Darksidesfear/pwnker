FROM ubuntu:18.04
MAINTAINER Andrew Bae <andy@pwner.kr>

ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

RUN sed -i 's/archive.ubuntu.com/mirror.kakao.com/g' /etc/apt/sources.list
RUN dpkg --add-architecture i386 && \
	apt update -y && \
	apt install -y \
	libc6:i386 \
    libc6-dbg:i386 \
    libc6-dbg \
    lib32stdc++6 \
    g++-multilib \
	curl \
    cmake \
    ipython3 \
    vim \
    net-tools \
    iputils-ping \
    libffi-dev \
    libssl-dev \
	python3\
    python3-dev \
	python\
	python-dev\
    build-essential \
    tmux \
    strace \
    ltrace \
    nasm \
    wget \
    gdb \
    gdb-multiarch \
    netcat \
    socat \
    git \
    patchelf \
    file 

RUN gpg --keyserver keyserver.ubuntu.com --recv-key 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
RUN \curl -sSL https://get.rvm.io | bash -s stable --ruby
RUN /bin/bash -l -c "rvm install ruby --latest"
RUN /bin/bash -l -c "gem install one_gadget"

RUN curl https://bootstrap.pypa.io/pip/3.5/get-pip.py > /tmp/get-pip.py && python3 /tmp/get-pip.py
RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py > /tmp/get-pip.py && python2 /tmp/get-pip.py

RUN pip2 install --upgrade pip && \
    python2 -m pip install --upgrade --no-cache-dir \
    gitdb2==2.0.6 \
    GitPython==2.1.14 \
    ropgadget \
    pwntools \
    z3-solver \
    smmap2 \
    apscheduler \
    ropper \
    unicorn \
    keystone-engine \
    capstone \
    angr \
    pebble \
    r2pipe \
	six==1.12.0

RUN pip3 install --upgrade pip && \
    python3 -m pip install --upgrade --no-cache-dir \
    ropgadget \
    pwntools \
    z3-solver \
    smmap2 \
    apscheduler \
    ropper \
    unicorn \
    keystone-engine \
    capstone \
    angr \
    pebble \
    r2pipe 
RUN python3 -m pip install six==1.12.0

RUN wget -q -O- https://github.com/hugsy/gef/raw/master/scripts/gef.sh | bash
RUN curl https://raw.githubusercontent.com/slimm609/checksec.sh/master/checksec > /usr/local/bin/checksec
# dotfiles
RUN curl https://raw.githubusercontent.com/andrewbae/dotfiles/master/.bash_profile > /root/.bash_profile
RUN curl https://raw.githubusercontent.com/andrewbae/dotfiles/master/.tmux.conf > /root/.bash_profile
RUN curl https://raw.githubusercontent.com/andrewbae/dotfiles/master/.vimrc > /root/.vimrc
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
RUN echo "source /etc/profile.d/rvm.sh" >> /root/.bashrc

VOLUME ["/pwn"]
WORKDIR /pwn

CMD ["/bin/bash"]