# Start from the latest golang base image
FROM golang:latest

# Set the Current Working Directory inside the container
WORKDIR /app

# Copy Go Modules dependency requirements file
COPY go.mod .

# Copy Go Modules expected hashes file
COPY go.sum .

# Download dependencies
RUN go mod download

# Copy all the app sources (recursively copies files and directories from the host into the image)
COPY . .

# Set http port
ENV HTTP_SERVER_PORT 8080
ENV HTTP_SERVER_TIMEOUT 10000
ENV CGO_ENABLED 0

# Build the app
RUN go build cmd/http-server/main.go

# Run the app
CMD ["./golang-mux-api"]
