FROM golang:latest

WORKDIR /app
COPY go.mod go.sum .
RUN go mod download
COPY . .
RUN go build
RUN CGO_ENABLED=0 go build -o app-go


FROM debian:bullseye
WORKDIR /app
COPY --from=0 /app/app-go /app/app-go

EXPOSE 8080

CMD ["./app-go"]