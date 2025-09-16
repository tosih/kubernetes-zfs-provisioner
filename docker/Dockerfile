FROM docker.io/library/alpine:3.22 as runtime

LABEL org.opencontainers.image.source=https://github.com/tosih/kubernetes-zfs-provisioner
LABEL org.opencontainers.image.description="Dynamic ZFS provisioner for Kubernetes"
LABEL org.opencontainers.image.licenses=MIT

ENTRYPOINT ["kubernetes-zfs-provisioner"]

RUN \
  apk add --no-cache curl bash openssh && \
  adduser -S zfs -G root

COPY docker/zfs.sh /usr/bin/zfs
COPY docker/update-permissions.sh /usr/bin/update-permissions
COPY kubernetes-zfs-provisioner /usr/bin/

USER zfs:root
