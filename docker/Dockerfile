FROM debian:stretch
ADD https://github.com/just-containers/s6-overlay/releases/download/v1.11.0.1/s6-overlay-amd64.tar.gz /tmp/
RUN tar xzf /tmp/s6-overlay-amd64.tar.gz -C / && \
	rm /tmp/s6-overlay-amd64.tar.gz
RUN sed -ie 's/main$/main non-free/g' /etc/apt/sources.list
RUN apt-get update && apt-get install -y \
	net-tools \
	c3270 \
	procps \
	unzip \
 && rm -rf /var/lib/apt/lists/*
RUN mkdir /tk4
ADD ./tk4-_v1.00_current.zip /tk4
RUN cd /tk4 && unzip ./tk4-_v1.00_current.zip && rm /tk4/tk4-_v1.00_current.zip
RUN echo CONSOLE >/tk4/unattended/mode && \
	sed -ie 's#>log/3033.log##g' /tk4/mvs

FROM scratch
ENTRYPOINT ["/init"]
WORKDIR /tk4
CMD ["/tk4/mvs"]
EXPOSE 3270 8038 33351 33352 33353
COPY --from=0 / /
