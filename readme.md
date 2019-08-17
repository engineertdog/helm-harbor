## About
This repo is used in conjunction with the [Harbor Terraform](https://github.com/engineertdog/terraform-harbor) repo. Make sure you utilize the Harbor Terraform repo first as you will need the KMS ARN and the S3 bucket name. This repo itself is used to deploy Harbor via [Helm](https://helm.sh/) into a Kubernetes cluster.

Official Harbor Helm documentation [here](https://github.com/goharbor/harbor-helm).

## Setup
1. Download the helm chart into the charts directory.
    - The current stable release from the [Harbor Helm](https://github.com/goharbor/harbor-helm) repo is the `1.1.0 branch`. Clone that branch and put the folder inside of the `charts` folder.
2. You need to set the following values in `values.yaml`. This will use a loadBalancer setup on AWS.
    - harbor.expose.tls.commonName
        - Needed to generate a certificate
    - harbor.expose.externalURL
        - Site URL
    - harbor.persistence.s3.region
        - Choose the region we want to deploy in.
    - harbor.persistence.s3.bucket
        - S3 Bucket name we set in the Harbor Terraform config.
    - harbor.persistence.s3.keyid
        - KMS Key ARN we got from the Harbor Terraform repo installation.
    - harbor.secretKey
        - Used for encryption
    - harbor.database.internal.password
        - If you want to use an external database instead, then you can set those values instead.