FROM golang:latest as builder

COPY . /authz_server
WORKDIR /authz_server
ENV GO111MODULE=on
# do this in a separate layer to cache deps from build to build
RUN go get
RUN CGO_ENABLED=0 GOOOS=linux go build -o authz_server

FROM alpine:latest
WORKDIR /root/
COPY --from=builder /authz_server .
CMD ["./authz_server"]