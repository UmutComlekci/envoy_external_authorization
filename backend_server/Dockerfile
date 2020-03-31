FROM golang:latest as builder

COPY . /backend_server
WORKDIR /backend_server
ENV GO111MODULE=on
RUN CGO_ENABLED=0 GOOOS=linux go build -o backend_server

FROM alpine:latest
WORKDIR /root/
COPY --from=builder /backend_server .
CMD ["./backend_server"]