FROM golang:1.21-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o main ./cmd/lambda

FROM public.ecr.aws/lambda/provided:al2

COPY --from=builder /app/main ${LAMBDA_RUNTIME_DIR}

CMD ["main"]