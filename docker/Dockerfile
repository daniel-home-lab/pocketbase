FROM golang:1.24-alpine AS builder
WORKDIR /src
COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 \
    go build -o pocketbase examples/base/main.go

FROM alpine:3.22
WORKDIR /app
COPY --from=builder /src/pocketbase .
EXPOSE 8080
CMD ["./pocketbase"]