FROM busybox
COPY hello.sh /
RUN adduser -D hello && chmod +x /hello.sh
USER hello
CMD ["/hello.sh"]
