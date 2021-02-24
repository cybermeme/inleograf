FROM alpine:latest

LABEL Maintainer="cybermeme@arch-libertas.net" \
      Description="Postix - mysql" \
      Version="1"

RUN apk update; apk add --no-cache postfix-mysql postfix --upgrade cyrus-sasl cyrus-sasl-static cyrus-sasl-digestmd5 cyrus-sasl-crammd5 cyrus-sasl-login cyrus-sasl-ntlm

VOLUME     [ "/var/spool/postfix", "/etc/postfix" ]

EXPOSE 25/tcp 587/tcp

CMD ['/usr/sbin/postfix -c /etc/postfix start >/dev/null 2>&1']
