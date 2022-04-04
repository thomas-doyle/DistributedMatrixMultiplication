# Distributed Matrix Multiplication
This project uses the gRPC (Remote Procedure Call) framework for scaled square matrix multiplication. Through a REST API, the client sends a file with two matrices and a deadline parameter in seconds. A server middleware calculates the footprint and the number of servers needed for the matrix multiplication. It then distributes the multiplication load to a maximum of 8 servers.

# References:
https://grpc.io/

https://grpc.io/docs/languages/java/basics/

https://spring.io/guides/tutorials/rest/

# Setup:
At least 9 servers

Clone this repo into each server
run sudo apt install default-jdk maven on each server
on client server cd into grpc-client and run ./mvnw clean spring-boot:run
on the rest of the servers cd into grpc-server and run ./mvnw clean spring-boot:run -Dmaven.test.skip=true
To upload matrix file use <server_public_ip>:8082/upload. The call accepts a body form data with 2 keys:

file - txt file containing 2 matrices - check provided file (MatrixFormatFile.txt) for matrix format
deadline - in seconds

# NOTE:
This version is implemented using ServiceNameBlockingStub for better performance and scalling an asynchronous stub can be used: https://grpc.io/docs/languages/java/generated-code/#asynchronous-stub
