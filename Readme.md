## Development Requirements

* .NET CORE SDK >= 2.0
* Visual Studio 2017 Community or JetBrains Rider 2017.3

## Project & Design Architecture

**Consul:**

This project is used to services register & discover. As follow steps to start your dev:

+ cd {Consul project folder}
+ consul agent -dev
+ start or restart our services projects
+ request http://localhost:8500/ui in browser

Or run dev.bat in src/Consul instead of upper steps

**OcelotGateway**

This project is used to reroute & lb our web request. If consul service was not started, this project run successfully but can't reroute, b/c it can't find available register service. 
Mark sure configuration's GlobalConfiguration section contains correct ServiceDiscoveryProvider

  "GlobalConfiguration": {
    "ServiceDiscoveryProvider": {
      "Host": "localhost",
      "Port": 8500
    }
  }

+ set this project as startup project
+ press F5
+ request http://localhost:8000/{api} to test this service
