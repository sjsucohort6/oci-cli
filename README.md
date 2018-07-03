# Instructions

## Running oci-cli

1) Make sure you have Docker installed.

2) Make sure that your OCI configuration in ~/.oci/config does not have any absolute path references to your OCI key.  For example:
```
[DEFAULT]
key_file=~/.oci/oci_api_key.pem
user=<USER_OCID>
fingerprint=<USER_FINGERPRINT>
tenancy=<TENANCY_OCID>
region=us-phoenix-1
```

3) Add this to your .profile:
```
oci() { docker run -t --rm --mount type=bind,source=$HOME/.oci,target=/root/.oci stephenpearson/oci-cli:latest "$@"; }
```

## Building oci-cli

```
docker build .
docker tag <image-id> my_hub_user/oci-cli
docker push my_hub_user/oci-cli
```
