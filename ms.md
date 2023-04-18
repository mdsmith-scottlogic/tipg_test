# Setup

Create a .env file with the following values
```
TIPG_NAME="DMS2: OGC Features and Tiles API"
DATABASE_URL=postgresql://postgres:postgres@0.0.0.0:5432/digital_land
```

# Running
You might need to install univorn, a python web app runner.

`univorn tipg.main:app`

You might need to get it on ypath as well.

# Seeing the map

You need the collection name (aka table name so far!) in the query as shown below.

`http://127.0.0.1:8000/collections/public.entity/viewer`