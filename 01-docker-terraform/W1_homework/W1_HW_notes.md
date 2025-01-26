# 1.2 ingesting taxi data to postgres using jupyter NB

# creating pgcli client to connect to the port on the local host 
pgcli -h localhost -u root -p 5432 -d ny_taxi

# how to run postgres13 image using docker,
# e > environment variables, 
# v > volume mapping folder from our file system on host machine to the folder/volume in the docker container 
#    # running docker images loses the changes made, so that's why you MOUNT a folder from local host machine to a    folder in a docker directory. 
#    # here the 'ny_taxi_postgres' folder in the current working directory (using $PWD) is mapped to the /var/lib/postgresql/data
# p > port mapping from local host machine to the port on docker 

docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:13


python W1_HW_ingest_data.py \
    --user=root2 \
    --password=root2 \
    --host=localhost \
    --port=5433 \
    --db=homework_taxi \
    --table_name=green_tripdata_2019-10 \
    --url="https://github.com/DataTalksClub/nyc-tlc-data/releases/download/green/green_tripdata_2019-10.csv.gz"

# using PGCLI

pgcli -h localhost -u postgres -p 5433 -d ny_taxi
