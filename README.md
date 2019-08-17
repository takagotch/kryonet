### kryonet
---
https://github.com/EsotericSoftware/kryonet

```java
Server server = new Server();
server.start();
server.bind(54555, 54777);


server.addListener(new Listener() {
  public void received (Connection connection, Object object) {
    if (object instanceof SomeRequest) {
      SomeRequest request = (SomeRequest)object;
      System.out.println(request.text);
      
      SomeResponse response = new SomeResponse();
      response.text = "Thanks";
      connection.sendTCP(response);
    }
  }
});

public class SomeRequest {
  public String text;
}
public class SomeResponse {
  public String text;
}


Client client = new Client();
client.start();
client.connect(5000, "192.168.0.4", 54555, 54777);

SomeRequest request = new SomeRequest();
request.text = "Here is the request";
client.sentTCP(request);

client.addListener(new Listener() {
  public void received (Connection connection, Object object) {
    if (object instanceof SomeResponse) {
      SomeResponse response = (SomeResponse)object;
      System.out.println(response.text);
    }
  }
});


Kryo.kryo = server.getKryo();
kryo.register(SomeRequest.class);
kryo.register(SomeResponse.class);
kryo.kryo = client.getKryo;
kryo.register(SomeRequest.class);
kryo.register(SomeResponse.class);


InetAddress address = client.discoverHost(54777, 5000);
System.out.println(address);

Log.set(LEVEL_TRACE);

ObjectSpace.registerClasses(endPoint.getKryo());
ObjectSpace. objectSpace = new ObjectSpace();
objectSpace.register(42, someObject);
objectSpace.addConnection(connection);

SomeObject someObject = ObjectSpace.getRemoteObject(connection, 42, SomeObject.class);
SomeResult result = someObject.doSomething();

SomeObject someObject = ObjectSpace.getRemoteObject(connection, 42, SomeObject.class);
((RemoteObject)).setNonBlockint(true, true);
someObject.doSomething();

RemoteObject remoteObject = (RemoteObject)someObject;
remoteObject.setNonBlockint(true, false);
SomeResult result = remoteObject.waitForLastResponse();

RemoteObject remoteObject = (RemoteObject)someObject;
remoteObject.setNonBlockint(true, false);
byte responseID = remoteObject.getLastResponseID();
SomeResult result = remoteObject.waitForResponse(responseID);

```


```
```

```
```
