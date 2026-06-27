# Please choose from the below set of Docker commands to complete your Dockerfile:

# COPY
# RUN
# ADD
# EXPOSE
# FROM
# CMD
# PUSH
# PULL
# WORKDIR


# Stage 1: Build the application
FROM golang:1.18 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy the source code into the container
COPY . .

# Build the application binary
RUN CGO_ENABLED=0 GOOS=linux go build -o guestbook .

# Stage 2: Final lightweight runtime image
FROM alpine:latest

# Set the working directory for the runtime container
WORKDIR /app

# Copy the compiled binary from the builder stage
COPY --from=builder /app/guestbook .

# Copy static assets or templates if your app requires them
COPY public/ ./public/

# Expose the application port
EXPOSE 3000

# Command to run the application
CMD ["./guestbook"]