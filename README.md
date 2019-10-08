# etherpad
Etherpad with postgreSQL

# Download the postgres image
dokcer pull postgres

# Create a mount point if needed
mkdir /Users/anan2252/docker/volumes/postgres

# Run the postgres container, You can create a user, password and db.
docker run -it --name pg-docker1 -e POSTGRES_USER=etherpad -e POSTGRES_PASSWORD=password -e POSTGRES_DB=etherpad -d -p 5432:5432 -v /Users/anan2252/docker/volumes/postgres:/var/lib/postgresql/data postgres

# Build the etherpad image from the source code and modify the settings.json file if needed (It's pointing to the container ip and port)
docker build --tag edaraanand/etherpad:latest .

#Run the etherpad
docker run -it -d -p 9001:9001 edaraanand/etherpad:latest
