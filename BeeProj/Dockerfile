
FROM golang:latest as builder

WORKDIR /go/src/github.com/4u1kto/Golang-Playground/BeeProj

COPY . .

RUN go get -u github.com/golang/dep/cmd/dep
RUN dep init && dep ensure
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .

FROM alpine:latest

RUN apk --no-cache add ca-certificates

RUN mkdir /BeeProj
WORKDIR /BeeProj
COPY --from=builder /go/src/github.com/4u1kto/Golang-Playground/BeeProj .

CMD ["./BeeProj"]