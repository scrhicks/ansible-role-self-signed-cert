Self Signed Cert
=========

This ansible role allows generating a self-signed certificates.


Role Variables
--------------

* `ssc.output_dir` - Directory where the certificates will be stored.
* `ssc.server_expiry` - Time when the server certificate will be expired.
* `ssc.client_expiry` - Time when the client certificate will be expired.
* `ssc.cn` - Is used by some CAs to determine which domain the certificate is to be generated for instead.
* `scc.hosts` - Is a list of the domain names which the certificate should be valid for.
* `ssc.key_algo` - Algorithm name which will be used to generate the certificate.
* `ssc.key_size` - Size of the key.
* `ssc.country` - The coutry (C).
* `ssc.location` - The locality or municipality (L).
* `ssc.organisation` - The organisation (O).
* `ssc.organisation_unit` - Organisational unit, such as the department responsible for owning the key; it can also be used for a "Doing Business As" (DBS) name (OU).
* `ssc.state` - The state or province (ST).


Example Playbook
----------------

```yaml
- hosts: localhost
  become: yes
  roles:
    - pogosoftware.self-signed-cert
  vars:
    cfssl:
        version: 'R1.2'
        os: linux
        os_arch: amd64
        
    ssc:
      output_dir: /vagrant/certs

      server_expiry: 8760h
      client_expiry: 8760h
      
      cn: example.com
      hosts:
        - example.com
        - www.example.com

      key_algo: rsa
      key_size: 4096

      country: PL
      location: Wroclaw
      organisation: Pogosoftware
      organisation_unit: DevOps
      state: dolnoslaskie
```