FROM cn007b/ubuntu:17.10

MAINTAINER V. Kovpak <cn007b@gmail.com>

ENV GOROOT /usr/local/go/
ENV GOPATH /opt/cn007b/go/
RUN mkdir -p $GOPATH

# go
RUN curl -O https://storage.googleapis.com/golang/go1.10.linux-amd64.tar.gz \
    && tar zxf go1.10.linux-amd64.tar.gz \
    && rm go1.10.linux-amd64.tar.gz \
    && mv go /usr/local \
    && ln -s /usr/local/go/bin/go /usr/bin/

# tools
RUN go get -u golang.org/x/lint/golint && ln -s $GOPATH/bin/golint /usr/bin/
RUN go get -u gopkg.in/alecthomas/gometalinter.v2 && ln -s $GOPATH/bin/gometalinter.v2 /usr/bin/gometalinter \
    && gometalinter --install
RUN go get -u golang.org/x/tools/cmd/cover
RUN go get -u github.com/mattn/goveralls && ln -s $GOPATH/bin/goveralls /usr/bin/
RUN go get -u github.com/derekparker/delve/cmd/dlv && ln -s $GOPATH/bin/dlv /usr/bin/
RUN go get -u github.com/codegangsta/gin && ln -s $GOPATH/bin/gin /usr/bin/
RUN go get -u github.com/google/pprof && ln -s $GOPATH/bin/pprof /usr/bin/
# required for pprof
RUN apt install -y python-pydot python-pydot-ng graphviz

CMD ["/usr/bin/go"]
