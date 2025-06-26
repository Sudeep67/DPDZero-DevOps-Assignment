# Use an official Golang base image
FROM golang:1.18

# Set the working directory inside the container
WORKDIR /app

# Copy the source code into the container
COPY . .

# Build the Go app
RUN go build -o main .

# Expose the port your app uses
EXPOSE 8001

# Command to run the binary
CMD ["./main"]
