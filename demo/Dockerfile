FROM golang AS builder 
WORKDIR /src
COPY src . 
RUN CGO_ENABLED=0 go build -o app 
FROM scratch 
ADD ./html /html
COPY --from=builder /src/app . 
ENTRYPOINT ["/app"]
EXPOSE 8080
RUN apt update && apt install -y bash coreutils
