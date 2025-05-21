# Stage 1: Build the Go app
FROM golang:1.20-alpine AS builder

# Set working directory inside the container
WORKDIR /app

# Copy go.mod and go.sum if ada (optional, kalau kamu pakai module)
# COPY go.mod go.sum ./
# RUN go mod download

# Copy all source code files ke container
COPY . .

# Build the Go binary statically linked
RUN go build -o hello-go-app main.go

# Stage 2: Create minimal image to run the app
FROM alpine:latest

# Copy binary dari stage builder
COPY --from=builder /app/hello-go-app /hello-go-app

# Jalankan binary
ENTRYPOINT ["/hello-go-app"]