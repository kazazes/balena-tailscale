FROM balenalib/amd64-alpine-golang:build as BUILD

WORKDIR /build/tailscaled
RUN go mod init tailscale.com/cmd/tailscaled
RUN go install tailscale.com/cmd/tailscaled

WORKDIR /build/tailscale
RUN go mod init tailscale.com/cmd/tailscale
RUN go install tailscale.com/cmd/tailscale
ENTRYPOINT ["/bin/sh"]

################################################
FROM balenalib/amd64-alpine-golang:run

RUN apk --no-cache add tini
COPY init /init
COPY --from=BUILD /go/bin /go/bin

ENTRYPOINT ["/sbin/tini", "--", "/init"]
