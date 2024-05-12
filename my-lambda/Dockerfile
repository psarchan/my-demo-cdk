FROM golang:1.22 as build
WORKDIR /my-lambda
COPY go.mod go.sum ./
COPY main.go .
RUN go build -tags lambda.norpc -o bootstrap main.go
FROM golang:1.22 as run
COPY --from=build /my-lambda/bootstrap ./bootstrap
ENTRYPOINT ["./bootstrap"]