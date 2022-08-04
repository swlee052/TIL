### Definition
1) Provides a surrogate or placeholder for another object to control access to it.
2) Proxy has the same interface as the real subject.
3) The client makes requests to the proxy, then proxy sends a request to the real subject when appropriate.
4) Lots of variations: Firewall Proxy, Smart Reference Proxy, Caching Proxy (provides temporary storage),
   synchronization proxy (safe access for multi threading), complexity hiding proxy (controls access to a set of classes),
   copy-on-write proxy (copies object until it's required by client), and so on...

### Remote Proxy
1) The proxy acts as a local representative for an object that lives in a different JVM.
2) Proxy lives in the same JVM heap space as client
3) It can be used for fetching images from the server. The proxy loads the "loading" UI and creates a thread creates
   the image containing object that fetches the image. When it's fetched, the real subject updates the UI.

### Virtual Proxy
1) Acts as a surrogate for the object before and while the real subject is being created.
2) Used when the real subject is expensive to create.
