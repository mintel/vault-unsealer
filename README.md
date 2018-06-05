# vault-unsealer
Image with Vault Unsealer to unseal vaults using GCP KMS and Google Bucket

# Pre-Requisite

* Access to google bucket as StorageObjectAdmin
* Access to kms key as EncryptorDecryptor

# Sample Run
Runnig on a CoreOS Instance on Google Cloud Platform as user core

* Mount gcloud config as volume 
* Mount Vault CA as volume
* Export VAULT_CACERT

```
docker run -v /home/core/.config:/.config -v /etc/ssl/vault-ca.crt:/vault-ca.crt -e VAULT_CACERT=/vault-ca.crt --net=host mintel/vault-unsealer:0.2.1-1 unseal --google-cloud-kms-crypto-key vault-init --google-cloud-kms-key-ring vault --google-cloud-kms-location europe-west1 --google-cloud-storage-bucket aa8aa8ae-vault --google-cloud-kms-project aa8aa8ae
```
