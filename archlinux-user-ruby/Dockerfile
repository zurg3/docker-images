# docker build --build-arg USERNAME=user -t archlinux-user-ruby .

FROM archlinux:latest

ARG USERNAME="user"

# RUN echo 'Server = https://mirror.yandex.ru/archlinux/$repo/os/$arch' > /etc/pacman.d/mirrorlist

RUN echo "[multilib]" >> /etc/pacman.conf
RUN echo "Include = /etc/pacman.d/mirrorlist" >> /etc/pacman.conf

RUN pacman -Syy && pacman -S --noconfirm base-devel ruby ruby-stdlib

RUN useradd -m -g users -G wheel -s /bin/bash ${USERNAME}
RUN echo "%wheel ALL=(ALL:ALL) NOPASSWD: ALL" >> /etc/sudoers

WORKDIR /home/${USERNAME}

USER ${USERNAME}

RUN echo 'gem: --no-user-install --no-document' > ~/.gemrc
RUN echo 'export GEM_HOME="$HOME/.gem"' >> ~/.bashrc
RUN echo 'export PATH="$PATH:$GEM_HOME/bin"' >> ~/.bashrc

CMD ["bash"]
