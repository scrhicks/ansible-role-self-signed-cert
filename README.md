Self Signed Cert
=========

This ansible role allows for generating self-signed certificates. As a result, it will generate 3 pem certificates with keys: ca, client and server. Additionally to that, it will also generate 2 pfx certificates for client and server.


Role Variables
--------------

* `self_signed_cert.output_dir` - Directory where the certificates will be stored.
* `self_signed_cert.server_expiry` - Time when the server certificate will be expired.
* `self_signed_cert.client_expiry` - Time when the client certificate will be expired.
* `self_signed_cert.cn` - Is used by some CAs to determine which domain the certificate is to be generated for instead.
* `self_signed_cert.sans` - Is a list of the domain names which the certificate should be valid for.
* `self_signed_cert.key_algo` - Algorithm name which will be used to generate the certificate.
* `self_signed_cert.key_size` - Size of the key.
* `self_signed_cert.country` - The coutry (C).
* `self_signed_cert.location` - The locality or municipality (L).
* `self_signed_cert.organisation` - The organisation (O).
* `self_signed_cert.organisation_unit` - Organisational unit, such as the department responsible for owning the key; it can also be used for a "Doing Business As" (DBS) name (OU).
* `self_signed_cert.state` - The state or province (ST).
* `self_signed_cert.trust_ca_cert` - Determinate if run update-ca-certificates or not.

Example Playbook
----------------

```yaml
- hosts: localhost
  become: yes
  roles:
    - pogosoftware.self_signed_cert
  vars:
    self_signed_cert:
      cfssl_version: 'R1.2'
      cfssl_os: linux
      cfssl_os_arch: amd64
        
      output_dir: /vagrant/certs

      server_expiry: 8760h
      client_expiry: 8760h
      
      cn: example.com
      sans:
        - example.com
        - www.example.com
        
      key_algo: rsa
      key_size: 4096

      country: PL
      location: Wroclaw
      organisation: Pogosoftware
      organisation_unit: DevOps
      state: dolnoslaskie

      trust_ca_cert: true
```