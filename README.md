# rustup-dockerfiles

collection of internally used dockerfiles based on [liuchong/rustup](https://github.com/liuchong/docker-rustup)

available on docker hub as [1aim/rustup-plus](https://hub.docker.com/r/1aim/rustup-plus/tags/)

### Tags
* [minimal](minimal/Dockerfile): unmodified, non-musl `all3` from liuchong/rustup (stable, beta, nightly)
* [runner](runner/Dockerfile): contains additional packages usually needed in CI runners (ssh, rsync, gawk, libz-dev)
    - run `eval $(ssh-agent -s)` before adding keys with `ssh-add`
* [postgres](postgres/Dockerfile): all packages from runner + postgres and commonly used extensions (contrib, postgis)
    - example of how to start the service and create a test database:
        ```bash
        service postgresql start
        echo "CREATE DATABASE testdb ENCODING 'UTF8'; \
              CREATE USER testuser WITH PASSWORD 'testpw'; \
              GRANT ALL PRIVILEGES ON DATABASE testdb to testuser;" | su - postgres -c psql
        ```
