# Amplify Fusion GRPC Demo

An Amplify Fusion gRPC Demo. Includes a mock back end gRPC server and a sample project export with gRPC proxy and twp gRPC over REST proxies. This was created by Deirdre MCHUGH.

## Mock gRPC Server

Folder `grpc-orders-mock-server` contains a mock grpc server jar file and two proto buf files.

Enter the following terminal command to start the server: `java -jar orders-grpc-1.0.0.jar`

You can run this on PCloud on the same machine as your PCloud Fusion Data Plane.

## Make Calls to Mock gRPC Server

### Install grpcurl

If you don't have `grpcurl` installed follow the instrctions below:

* Mac OS
  * `brew install grpcurl`
  * `grpcurl --version`
* Ubuntu Linux (Pcloud)
  * `curl -LO https://github.com/fullstorydev/grpcurl/releases/latest/download/grpcurl_1.9.3_linux_x86_64.tar.gz`
  * `tar -xzf grpcurl_1.9.3_linux_x86_64.tar.gz`
  * `chmod +x grpcurl`
  * `sudo mv grpcurl /usr/local/bin/`
  * `grpcurl --version`


### Test Server

`grpcurl -plaintext localhost:9090 list`

### Create Order
 
`grpcurl -plaintext -d '{"customerId":"cust-002","customerEmail":"x@y.com","items":[{"sku":"SKU-1","name":"Item","quantity":1,"unitPrice":{"currencyCode":"EUR","units":"1000"}}]}' localhost:9090 orders.v1.OrdersService/CreateOrder`
 
### Watch Orders
 
`grpcurl -plaintext -d '{"includeExisting":true}' localhost:9090 orders.v1.OrdersService/WatchOrders`


## Import Project

The file `gRPC-Orders-project.zip` is a sample gRPC Proxy project export with project name: `AnalystDemo_Orders`.

Import the project and edit the three connections with your host URL (PCloud IP address).

## Postman Collection

The file `gRPC-REST.postman_collection.json` is a Postman Collection export