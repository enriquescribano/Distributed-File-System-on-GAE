# Distributed-File-System-on-GAE
Distributed File System on Google App Engine.

It is deployed on:  http://cs553ape.appspot.com 

How it works?

The distributed storage system is built on top of Google App Engine, using Google Cloud Storage Client Library. The storage system supports storing arbitrary files using a unique key, think of a key/value store, where the key is a unique filename (could have some complex path associated with it, but it’s not required), and the value would be a file of arbitrary size. The Google Cloud Storage will be a persistent storage solution, but could have particularly high latency overheads for small files. To improve the small file size performance we considered using memcache as a cache for small files (<=100KB). Since memcache is a distributed in-memory data structure, accessing small files from memory should be significantly faster than accessing such small files from persistent storage. Medium and large files should not be cached in memory, as in practice, large storage systems will generally have much more persistent storage capacity than volatile memory available.
