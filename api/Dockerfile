# Build stage
FROM golang:alpine AS builder

RUN mkdir /build

ADD . /build/

WORKDIR /build

# Build the application
RUN go build -o main .

# Final stage
FROM alpine:latest

# Create non-root user
RUN adduser -S -D -H -h /app appuser

# Use non-root user
USER appuser

COPY . /app

# Copy binary from builder
COPY --from=builder /build/main /app/

# Create app directory
WORKDIR /app

# Expose port
EXPOSE 3000

# Run the application
CMD ["./main"]