# pks-config-v3

Use this repo to build a platform-automation configuration repo for PKS deployment. 

Open labverify/products.yml and set pks.product-version to the version of PKS you want to deploy

Open labverify/credentials.yml and replace the contents with your values. You should decide on a "credhub prefix" to use before you start. This can be anything but commonly it would be "/concourse/TEAM-NAME/PIPELINE-NAME/". Create all keys with that prefix. In my example, we use "/concourse/main/install-pks-lab"

```
- name: /concourse/main/install-pks-lab/opsman_admin
  type: user
  value:
    username: craig
    password: xxxxxxx
```

```
- name: /concourse/main/install-pks-lab/decryption_passphrase
  type: value
  value: xxxxxxx
```

```
- name: /concourse/main/install-pks-lab/pivnet_token
  type: value
  value: xxxxxxx

```

```
- name: /concourse/main/install-pks-lab/opsman_target
  type: value
  value: opsman-verify.21dr.gridbug.io
```

```
- name: /concourse/main/install-pks-lab/pks_tls
  type: certificate
  value: 
    ca: |
      -----BEGIN CERTIFICATE-----
      xxxxxxx
      -----END CERTIFICATE-----
    certificate: |
      -----BEGIN CERTIFICATE-----
      xxxxxxx
      -----END CERTIFICATE-----
    private_key: |
      -----BEGIN RSA PRIVATE KEY-----
      xxxxxxx
      -----END RSA PRIVATE KEY-----

```

```
- name: /concourse/main/install-pks-lab/vcenter_user
  type: user
  value:
    username: administrator@gridbug.ai
    password: xxxxxxxx

```

Import these credentials into your credhub (i.e. "credhub import -f labverify/credentials.yml")

Open labverify/vars/pivotal-container-service-vars.yml and replace values to match your environment

Commit and push your repo. Note the repo url and the credhub prefix you chose as we'll need them to deploy the pipeline. The pipeline repo is here - https://github.com/colrich/pks-pipelines-v3
