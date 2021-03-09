FROM codesignal/ubuntu-base:new

# Installing Microsoft SQL Server
RUN wget -qO- https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
    && add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)" \
    && apt-get update \
    && ACCEPT_EULA=Y apt-get install -y mssql-server mssql-tools unixodbc-dev \
    && rm -rf /var/lib/apt/lists/*
