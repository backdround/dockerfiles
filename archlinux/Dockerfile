FROM archlinux:latest

# Configuration
WORKDIR /root/
ENTRYPOINT []
CMD ["/usr/bin/zsh"]

# Install from script.
RUN pacman --noconfirm -Syu git sudo
RUN cd ~ \
  && git clone https://github.com/backdround/configuration.git \
  && cd configuration \
  && ./auxiliary/init.sh server

# Install zsh plugins
ENV SHELL=zsh
RUN zsh -ic "sleep 0.5"

# Install neovim plugins
RUN mkdir drop \
  && nvim --headless +PlugInstall +'CocInstall -sync' +qa

# Install neovim coc extensions
RUN COC_PLUGINS=$(nvim --headless +'echo g:coc_global_extensions' +'echo "\n"' +qa 2>&1 \
  | head -1 | tr -d ",[]'" | tr ' ' '\n') \
  && echo "$COC_PLUGINS" \
  | xargs -i sh -c 'nvim --headless +"CocInstall -sync {}" +qa 2> /dev/null && echo "{} installed"'
