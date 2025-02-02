docker run -it \
  -e POSTGRES_USER="kestra" \
  -e POSTGRES_PASSWORD="k3str4" \
  -e POSTGRES_DB="postgres" \
  -v $(pwd)/postgres-data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:13


  pgcli -h localhost -p 5432 -u kestra -d postgres



  postgres:
    image: postgres
    volumes:
      - postgres-data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: kestra
      POSTGRES_USER: kestra
      POSTGRES_PASSWORD: k3str4
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -d $${POSTGRES_DB} -U $${POSTGRES_USER}"]
      interval: 30s
      timeout: 10s
      retries: 10
    ports:
      - "5432:5432"
    expose:
      - "5432"  #exposing 5432 port to be able to connect to the database from the host machine
    extra_hosts:
      - "host.docker.internal:host-gateway"