FROM alpine:latest

# WORKDIR is root
WORKDIR /

# USE APK TO INSTALL GOLANG
RUN apk add --no-cache git make musl-dev go gcc g++

# GOPY build.sh 
COPY ./build.sh /

# EXPORT 
ENV GOROOT /usr/lib/go
ENV GOPATH /go
ENV PATH /go/bin:$PATH
# Enable CGO to BUILD Sqlite3 (mattn)
ENV CGO_ENABLED 1

# MKDIR-ing Create Directory
RUN mkdir -p ${GOPATH}/src ${GOPATH}/bin
RUN mkdir -p ${GOPATH}/src/github

# RUN GoDep To Install
RUN curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh

# WORKDIR is $GOPATH
WORKDIR ${GOPATH}

# RUN Build Scripts
CMD [ "/build.sh" ]