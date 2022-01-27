Install dependencies

```shell
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
