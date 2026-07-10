# Go zabbix api

This Go package provides access to Zabbix API.

Tested on Zabbix 3.2, 3.4, 4.0, 4.2 and 4.4, but should work since 2.0 version.

This package aims to support multiple zabbix resources from its API like trigger, application, host group, host, item, template..

## Install

Install it: `go get github.com/makuartur/go-zabbix-api`

## Getting started

```go
package main

import (
	"fmt"

	"github.com/makuartur/go-zabbix-api"
)

func main() {
	user := "MyZabbixUsername"
	pass := "MyZabbixPassword"
	api, err := zabbix.NewAPI(zabbix.Config{Url: "http://localhost/api_jsonrpc.php"})
	if err != nil {
		panic(err)
	}
	api.Login(user, pass)

	res, err := api.Version()
	if err != nil {
		panic(err)
	}
	fmt.Printf("Connected to zabbix api v%s\n", res)
}
```

## Tests

### Considerations

You should run tests before using this package.
Zabbix API doesn't match documentation in few details, which are changing in patch releases. 

Tests are not expected to be destructive, but you are advised to run them against not-production instance or at least make a backup.
For a safer and more accurate testing we advice to run tests with following minimum versions which implements strict validation of valuemap for `get` method:

- 4.0.13rc1 [6ead4fd7865](https://git.zabbix.com/projects/ZBX/repos/zabbix/commits/6ead4fd7865f24ba1246832caa867d33ee9773ba)
- 4.2.7rc1 [a1d257bf6a3](https://git.zabbix.com/projects/ZBX/repos/zabbix/commits/a1d257bf6a3972e24a0044aa019d120eaf7a211a)
- 4.4.0alpha3 [db94d75b4bf](https://git.zabbix.com/projects/ZBX/repos/zabbix/commits/db94d75b4bf5bfc72df3e01cd5fd4a57bc3784e3)

For more information, please see issues [ZBX-3783](https://support.zabbix.com/browse/ZBX-3783) and [ZBX-3685](https://support.zabbix.com/browse/ZBX-3685)

### Run tests

```bash
export TEST_ZABBIX_URL=http://localhost:8080/zabbix/api_jsonrpc.php
export TEST_ZABBIX_USER=Admin
export TEST_ZABBIX_PASSWORD=zabbix
export TEST_ZABBIX_VERBOSE=1
go test -v
```

`TEST_ZABBIX_URL` may contain HTTP basic auth username and password: `http://username:password@host/api_jsonrpc.php`. Also, in some setups URL should be like `http://host/zabbix/api_jsonrpc.php`.

## Terraform provider

Use as a dependency in your Terraform provider:

```go
require github.com/makuartur/go-zabbix-api v0.17.0
```

License: Simplified BSD License (see [LICENSE](LICENSE)).
# go-zabbix-api
# go-zabbix-api
# go-zabbix-api
# go-zabbix-api
