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

>vault write auth/approle/role/demoApp secret_id_ttl=8736h token_ttl=8736h token_max_ttl=8736h policies=readonly

>vault read auth/approle/role/demoApp/role-id

>vault write -force auth/approle/role/demoApp/secret-id
