# grpc-debug

Only intended to be example code for debugging some grpc behaviors and nothing more

### Server (java)

```shell
cd java/examples/
./gradlew installDist && ./build/install/examples/bin/route-guide-server
```

The relevant code that instantiates the server and generates responses is contained in 
`java/examples/src/main/java/io/grpc/examples/routeguide/RouteGuideServer.java`.

### Client (node)

Make sure you have `yarn` installed; if you don't, one way to install is with `npm`:

```shell
npm i -g yarn
```

Use `nvm` to select your favorite version of node; `12.13.0` is suggested in the `engines` config:

```shell
nvm use 12.13.0
```

Install dependencies

```shell
cd node/
yarn install
```

Run the client. The env flags are only needed for extra debug output.

```shell
GRPC_TRACE=all GRPC_VERBOSITY=DEBUG node ./static_codegen/route_guide/route_guide_client.js --db_path=./static_codegen/route_guide/route_guide_db.json
```

The relevant code that creates requests is at the bottom of the `runGetFeature` method inside 
`static_codegen/route_guide_client.js`.

The default execution will perform a "bad" request which is expected to time out after 10 seconds.
Change these lines to see how a "good" request should work.

```javascript
  // client.getFeatureGood(point1, {deadline}, featureCallback);
  client.getFeatureBad(point1, {deadline}, featureCallback);
```
