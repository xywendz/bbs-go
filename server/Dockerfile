FROM golang:1.24 AS server_builder

ENV APP_HOME=/code/bbs-go/server
WORKDIR "$APP_HOME"

COPY ./server ./
# RUN go env -w GOPROXY=https://goproxy.cn,direct
RUN go mod download
RUN CGO_ENABLED=0 go build -v -o bbs-go main.go && chmod +x bbs-go

FROM alpine:3.21
WORKDIR /app/bbs-go
COPY --from=server_builder /code/bbs-go/server/bbs-go ./server/bbs-go
COPY --from=server_builder /code/bbs-go/server/*.yaml ./server/
COPY --from=server_builder /code/bbs-go/server/*.yml ./server/
COPY --from=server_builder /code/bbs-go/server/migrations ./server/migrations

EXPOSE 8082

ENTRYPOINT [ "./bbs-go" ]