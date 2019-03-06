# mSuperdrive

This instruction covers how to install and deploy the mSuperdrive microservice to the edgeSDK runtime. The mimik team created this microservice for mimik access to enable device clustering among edge devices. These are the main functionalities:

1. Provide Local and Global Device Discovery.

2. APIs for microservice and edgeSDK management.

3. Use with mBeam to enable mimiking

4. Data Transfer End Point Creation (BEP/SEP)

## Deploy to edgeSDK

For latest update: https://developer.mimik.com/docs/microservices/deploy

1. Install the superdrive-v1.tar image on edgeSDK mCM container using bearer token 

```curl -i -H 'Authorization: Bearer **replaceWithYourToken**' -F "image=@superdrive-v1.tar" http://localhost:8083/mcm/v1/images```


2. Initialize superdrive microservice in edgeSDK mCM contatiner using bearer token

``` curl -i -H 'Authorization: Bearer **replaceWithYourToken**' -d '{"name": "superdrive-v1", "image": "superdrive-v1", "env": {"MCM.BASE_API_PATH": "/superdrive/v1", "MFD": "https://mfd.mimik360.com/mFD/v1", "MPO": "https://mpo.mimik360.com/mPO/v1", "uMDS": "http://127.0.0.1:8083/mds/v1"} }' http://localhost:8083/mcm/v1/containers``` 

3. Verify that mSuperDrive microservice registered and works properly by calling following curl commands:

```curl -i http://localhost:8083/superdrive/v1/bep```

## Recommended guides

* [mimik serverless JavaScript programming API](https://github.com/mimikgit/edgeSDK/wiki/How-to-use-mimik-serverless-JavaScript-programming-API)
