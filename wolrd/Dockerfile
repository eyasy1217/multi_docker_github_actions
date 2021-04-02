FROM busybox
COPY world.sh /
RUN adduser -D world && chmod +x /world.sh
USER world
CMD ["/world.sh"]
