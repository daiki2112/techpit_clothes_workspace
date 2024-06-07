ARG MYSQL_VERSION
FROM mysql:${MYSQL_VERSION}

LABEL maintainer="Mahmoud Zalt <mahmoud@zalt.me>"

# Set environment variables
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=default
ENV MYSQL_USER=default
ENV MYSQL_PASSWORD=secret

# Copy custom MySQL configuration
COPY my.cnf /etc/mysql/conf.d/my.cnf

# Ensure the MySQL data directory exists and has the correct permissions
RUN mkdir -p /var/lib/mysql && chown -R mysql:mysql /var/lib/mysql

# Expose the MySQL port
EXPOSE 3306

# Add healthcheck
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD mysqladmin ping -h localhost || exit 1

CMD ["mysqld"]
