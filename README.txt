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

spring: 

  cloud: 

    vault: 

      kv: 

        application-name: alcon 

        default-context: '' 

        backend: test 

        enabled: true 

      authentication: APPROLE 

      app-role: 

        role-id: b03a70df-e527-4344-ba22-a606ea6e528b 

        secret-id: d4950511-c4a7-75f4-486d-b8376873a829 

        app-auth-path: approle 

      scheme: https 

      uri: https://isvaulttst.ad.infosys.com 

      generic: 

        enabled: false 
        
        <dependencyManagement> 

        <dependencies> 

            <dependency> 

                <groupId>org.springframework.cloud</groupId> 

                <artifactId>spring-cloud-dependencies</artifactId> 

                <version>Greenwich.M2</version> 

                <type>pom</type> 

                <scope>import</scope> 

            </dependency> 

        </dependencies> 

    </dependencyManagement> 
