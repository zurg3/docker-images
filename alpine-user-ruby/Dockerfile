# docker build --build-arg USERNAME=user -t alpine-user-ruby .

FROM alpine:latest

ARG USERNAME="user"

RUN apk update && apk add sudo bash shadow ruby ruby-dev build-base

RUN useradd -m -g users -G wheel -s /bin/bash ${USERNAME}
RUN echo "%wheel ALL=(ALL:ALL) NOPASSWD: ALL" >> /etc/sudoers

WORKDIR /home/${USERNAME}

USER ${USERNAME}

RUN echo 'gem: --no-user-install --no-document' > ~/.gemrc
RUN echo 'export GEM_HOME="$HOME/.gem"' >> ~/.bashrc
RUN echo 'export PATH="$PATH:$GEM_HOME/bin"' >> ~/.bashrc

CMD ["bash"]
