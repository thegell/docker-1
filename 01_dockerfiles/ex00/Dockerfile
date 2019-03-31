#docker build -t alpine-vim .
#docker run -it alpine-vim

FROM alpine

RUN apk update && \
	apk upgrade && \
	apk add vim

ENTRYPOINT ["vim"]
