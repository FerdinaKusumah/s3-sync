# s3-sync

Sync AWS S3 storage:
* From s3 -> s3
* FROM s3 -> local storage
* FROM local storage -> s3 


![S3 Sync](https://raw.githubusercontent.com/FerdinaKusumah/s3-sync/master/s3_sync/images/example.png)

## Installation

```shell
  pip install s3_sync
```

## S3 sync s3 to s3

### Read from parameters
```shell
    s3-sync --sync-cross-account true \
        --source-bucket-name foo \
        --source-region-name ap-southeast-1 \
        --source-access-key-id bar \
        --source-secret-access foobar \
        
        --target-bucket-name foo \
        --target-region-name ap-southeast-1 \
        --target-access-key-id bar \
        --target-secret-access foobar
```

### Read from json file
* Create example json file as bellow example, you can name this file whatever

```json
{
  "source": {
    "bucket_name": "foo",
    "region_name": "ap-southeast-1",
    "aws_access_key_id": "bar",
    "aws_secret_access_key": "foobar"
  },
  "target": {
    "bucket_name": "foo",
    "region_name": "ap-southeast-1",
    "aws_access_key_id": "bar",
    "aws_secret_access_key": "foobar"
  }
}
```

* Then execute command `s3-sync --sync-cross-account true -json ./whatever.json`

### Read from yml or yaml file
* Create example json file as bellow example, you can name this file whatever

```yaml
source:
  bucket_name: foo
  region_name: ap-southeast-1
  aws_access_key_id: bar
  aws_secret_access_key: foobar
target:
  bucket_name: foo
  region_name: ap-southeast-1
  aws_access_key_id: bar
  aws_secret_access_key: foobar
```

* Then execute command `s3-sync --sync-cross-account true -yml ./whatever.yml` or `s3-sync --sync-cross-account true -yaml ./whatever.yaml`


## S3 sync s3 to local (*Give absolute path for this*)
### Read from parameters
```shell
    s3-sync --sync-server-local true \
        --source-bucket-name foo \
        --source-region-name ap-southeast-1 \
        --source-access-key-id bar \
        --source-secret-access foobar \
        --target-local-path "/Users/ferdinakusumah/foo/bar/s3-sync/sync-data"
```

### Read from json file
* Create example json file as bellow example, you can name this file whatever

```json
{
  "source": {
    "bucket_name": "foo",
    "region_name": "ap-southeast-1",
    "aws_access_key_id": "bar",
    "aws_secret_access_key": "foobar"
  },
  "target": {
    "path": "/Users/ferdinakusumah/foo/bar/s3-sync/sync-data"
  }
}
```

* Then execute command `s3-sync --sync-server-local true -json ./whatever.json`

### Read from yml or yaml file
* Create example json file as bellow example, you can name this file whatever

```yaml
source:
  bucket_name: foo
  region_name: ap-southeast-1
  aws_access_key_id: bar
  aws_secret_access_key: foobar
target:
  path: /Users/ferdinakusumah/foo/bar/s3-sync/sync-data
```

* Then execute command `s3-sync --sync-server-local true -yml ./whatever.yml` or `s3-sync --sync-server-local true -yaml ./whatever.yaml`



## S3 sync local to s3

### Read from parameters
```shell
    s3-sync --sync-local-server true \
        --source-local-path "/Users/ferdinakusumah/foo/bar/s3-sync/sync-data" \
        
        --target-bucket-name foo \
        --target-region-name ap-southeast-1 \
        --target-access-key-id bar \
        --target-secret-access foobar
```

### Read from json file
* Create example json file as bellow example, you can name this file whatever

```json
{
  "source": {
    "path": "/Users/ferdinakusumah/foo/bar/s3-sync/sync-data"
  },
  "target": {
    "bucket_name": "foo",
    "region_name": "ap-southeast-1",
    "aws_access_key_id": "bar",
    "aws_secret_access_key": "foobar"
  }
}
```

* Then execute command `s3-sync --sync-local-server true -json ./whatever.json`

### Read from yml or yaml file
* Create example json file as bellow example, you can name this file whatever

```yaml
source:
  path: /Users/ferdinakusumah/foo/bar/s3-sync/sync-data
target:
  bucket_name: foo
  region_name: ap-southeast-1
  aws_access_key_id: bar
  aws_secret_access_key: foobar
```

* Then execute command `s3-sync --sync-local-server true -yml ./whatever.yml` or `s3-sync --sync-local-server true -yaml ./whatever.yaml`

### Pull Request are welcome
