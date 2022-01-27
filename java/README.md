```shell
cd examples/
./gradlew installDist && ./build/install/examples/bin/route-guide-server
```

The relevant code that instantiates the server and generates responses is contained in 
`java/examples/src/main/java/io/grpc/examples/routeguide/RouteGuideServer.java`.
