**RxFileWatcher** allows you to observe directories (recursiveley or not) for file system events with a [RxJava](https://github.com/ReactiveX/RxJava) observable. It is based on the [JDK WatchService](https://docs.oracle.com/javase/8/docs/api/java/nio/file/WatchService.html), but it is much more convenient.

Usage
-------

The following example creates an observable that watches the given directory and all its subdirectories for file system events. Each event will be emitted as a [WatchEvent](https://docs.oracle.com/javase/8/docs/api/java/nio/file/WatchEvent.html) and will be printed.

```java
DirectoryObservable
  .createRecursive(Paths.get("some/dir/"))
  .subscribe(event -> System.out.println(event));
```
        
The example above uses a scheduler 
    
To watch only the top-level directory, you call `createNonRecursive` instead of `createRecursive`:

```java
DirectoryObservable
  .createNonRecursive(Paths.get("some/dir/"))
  .subscribe(event -> System.out.println(event));
```

That's it!

See [RxJava Documentation](https://github.com/ReactiveX/RxJava/wiki) for more information, e. g. how you can filter certain types of events.