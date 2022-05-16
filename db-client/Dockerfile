FROM quay.io/debezium/tooling:latest

RUN yum install -y community-mysql
RUN yum install -y postgresql

RUN curl https://packages.microsoft.com/config/rhel/8/prod.repo > /etc/yum.repos.d/msprod.repo
RUN ACCEPT_EULA=Y yum install -y mssql-tools unixODBC-devel
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc

#install mongo
ADD mongodb-org-5.0.repo /etc/yum.repos.d/
RUN yum install -y mongodb-org-shell