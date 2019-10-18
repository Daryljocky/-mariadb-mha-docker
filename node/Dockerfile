FROM genee/mairadb:latest

COPY ./mha4mysql-node-0.58.tar.gz /tmp/

RUN build_deps='ssh sshpass perl libdbi-perl libmodule-install-perl libdbd-mysql-perl make' \
    && apt-get update \
    && apt-get -y --force-yes install $build_deps \
    && tar -zxf /tmp/mha4mysql-node.tar.gz -C /opt \
    && cd /opt/mha4mysql-node \
    && perl Makefile.PL \
    && make \
    && make install \
    && cd /opt \
    && rm -rf /opt/mha4mysql-* \
    && apt-get clean \
    && echo 'export PATH="/app/bin:$PATH"' > /etc/profile.d/docker

ENV PATH=/app/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
