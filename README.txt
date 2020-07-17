ui = true
storage "file" {
  path = "data"
}
listener "tcp" {
  address     = "0.0.0.0:8200"
  tls_disable = 1
}
max_lease_ttl = "720h"
default_lease_ttl = "168h"
api_addr = "http://0.0.0.0:8200"




vault server –config=config.hcl
