# docker build --build-arg USERNAME=user -t ubuntu-user-ruby .

FROM ubuntu:latest

ARG USERNAME="user"

RUN apt update && apt install -y sudo ruby-full build-essential

RUN useradd -m -g users -G sudo -s /bin/bash ${USERNAME}
RUN echo "%sudo ALL=(ALL:ALL) NOPASSWD: ALL" >> /etc/sudoers

WORKDIR /home/${USERNAME}

USER ${USERNAME}

RUN echo 'gem: --no-user-install --no-document' > ~/.gemrc
RUN echo 'export GEM_HOME="$HOME/.gem"' >> ~/.bashrc
RUN echo 'export PATH="$PATH:$GEM_HOME/bin"' >> ~/.bashrc

CMD ["bash"]
