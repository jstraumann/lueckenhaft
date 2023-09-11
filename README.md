# Lueckenhaft

[https://lueckenhaft.juergstraumann.ch/index.html](https://lueckenhaft.juergstraumann.ch/index.html)

Lueckenhaft is hosted on Amazon AWS because the files are quite large.

## Requirements

* Install Git LFS repo: `curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash`
* Install Git LFS: `sudo apt install git-lfs`
* Enable Git LFS: `git lfs install`

## Development

* Add files to track with LFS: `git lfs track "*.psd"`

## Deploy

* Install the AWS CLI: `sudo apt install awscli`
* Login (you can get the credentials from one of the developers): `aws configure`
* Upload the files:

```bash
aws s3 cp .                                    s3://lueckenhaft.juergstraumann.ch/ --recursive --exclude "*" --include "*.txt" --include "*.html"
aws s3 cp StreamingAssets/UnityServicesProjectConfiguration.json s3://lueckenhaft.juergstraumann.ch/StreamingAssets/UnityServicesProjectConfiguration.json

aws s3 cp Build/JürgspielWebgl.data.gz         s3://lueckenhaft.juergstraumann.ch/Build/JürgspielWebgl.data.gz \
  --content-type="application/octet-stream" \
  --content-encoding "gzip"
aws s3 cp Build/JürgspielWebgl.framework.js.gz s3://lueckenhaft.juergstraumann.ch/Build/JürgspielWebgl.framework.js.gz \
  --content-type="application/javascript" \
  --content-encoding "gzip"
aws s3 cp Build/JürgspielWebgl.loader.js       s3://lueckenhaft.juergstraumann.ch/Build/JürgspielWebgl.loader.js \
  --content-type="application/javascript"
aws s3 cp Build/JürgspielWebgl.wasm.gz         s3://lueckenhaft.juergstraumann.ch/Build/JürgspielWebgl.wasm.gz \
  --content-type="application/wasm" \
  --content-encoding "gzip"
```
