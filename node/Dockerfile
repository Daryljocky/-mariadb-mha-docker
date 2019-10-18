FROM mariadb/server:10.3

COPY ./mha4mysql-node-0.58.tar.gz /tmp/

RUN build_deps='ssh sshpass perl libdbi-perl libmodule-install-perl libdbd-mysql-perl make' \
    && apt-get update \
    && apt-get -y --force-yes install $build_deps \
    && tar -zxf /tmp/mha4mysql-node-0.58.tar.gz -C /opt \
    && cd /opt/mha4mysql-node-0.58 \
    && perl Makefile.PL \
    && make \
    && make install \
    && cd /opt \
    && rm -rf /opt/mha4mysql-* \
    && apt-get clean 
