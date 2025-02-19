# seqcolapi

Alpha version of a sequence collections server

## Instructions

### Running natively

Install natively with `pip install .`

Run natively:
```
export POSTGRES_PASSWORD=`pass aws/rds_postgres`
seqcolapi serve -c /home/nsheff/code/seqcolapi.databio.org/config/seqcolapi.yaml -p 8100
```

Use at: http://localhost:8100

http://0.0.0.0:8100/compareget/a6748aa0f6a1e165f871dbed5e54ba62/2786eb8a921aa97018c214f64b9960a0


### Running with docker

To build the docker file:

```
docker build --no-cache -t scim .
```

To run in a container:

```
export POSTGRES_PASSWORD=`pass aws/rds_postgres` 
docker run --rm -p 8000:8000 --name sccon \
  --env "POSTGRES_PASSWORD" \
  --volume $CODE/seqcolapi.databio.org/config/seqcolapi.yaml:/config.yaml \
  scim seqcolapi serve -c /config.yaml -p 8000
```

To deploy container to dockerhub:

Use github action in this repo which deploys on release, or through manual dispatch.


Left to do:
- [x] it already retrieves from a refget server.
- [x] let me insert stuff using only checksums.
- [ ] make it take 2 refget servers correctly.
