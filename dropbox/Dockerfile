#
# docker run -it --name dropbox \
#		-v $HOME/Dropbox:/home/user/Dropbox
#		dropbox
#

FROM debian:latest

RUN apt-get update \
	&& apt-get install -y ca-certificates openssl wget \
	&& rm -rf /var/lib/apt/lists/*

ENV HOME /home/user
RUN useradd --create-home --home-dir $HOME user \
	&& mkdir -p $HOME/Dropbox \
	&& chown -R user:user $HOME

ENV LANG C.UTF-8

RUN cd $HOME \
	&& wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -

WORKDIR $HOME
VOLUME $HOME/Dropbox

USER user
CMD ["/home/user/.dropbox-dist/dropboxd"]
