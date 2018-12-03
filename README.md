# rxjava-slf4j-mdc-hook

[![Build Status](https://travis-ci.org/puzpuzpuz/rxjava-slf4j-mdc-hook.svg?branch=master)](https://travis-ci.org/puzpuzpuz/rxjava-slf4j-mdc-hook)

[RxJava](https://github.com/ReactiveX/RxJava) v1 and v2 [hooks](https://github.com/ReactiveX/RxJava/pull/4007) which enable [SLF4J](https://github.com/qos-ch/slf4j)'s [`MDC`](http://www.slf4j.org/api/org/apache/log4j/MDC.html) propagation.

A fork of [bmcstdio/rxjava-slf4j-mdc-hook](https://github.com/bmcstdio/rxjava-slf4j-mdc-hook).

## Usage

If you're using RxJava 2:

```java
RxJavaPlugins.setScheduleHandler(new MdcPropagatingOnScheduleFunction());
```

If you're using RxJava ≥ 1.1.7:

```java
RxJavaHooks.setOnScheduleAction(new MdcPropagatingOnScheduleAction());
```

If you're using RxJava ≤ 1.1.6:

```java
RxJavaPlugins.getInstance().registerSchedulersHook(new RxJavaSchedulersHook() {
    @Override
    public Action0 onSchedule(final Action0 action) {
        return new MdcPropagatingAction(action);
    }
});
```

**Note:**
Both `RxJavaPlugins#getInstance()` and `RxJavaSchedulersHook#onSchedule(Action0)` are deprecated since 1.1.7.

## Binaries

`rxjava-slf4j-mdc-hook` is available from both JCenter and Maven Central:

**Gradle:**

```
compile 'io.github.puzpuzpuz:rxjava-slf4j-mdc-hook:1.0.0'
```

**Maven:**

```
<dependency>
  <groupId>io.github.puzpuzpuz</groupId>
  <artifactId>rxjava-slf4j-mdc-hook</artifactId>
  <version>1.0.0</version>
</dependency>
```

## Building

```
$ git clone https://github.com/puzpuzpuz/rxjava-slf4j-mdc-hook.git
$ cd rxjava-slf4j-mdc-hook
$ ./gradlew build
```

## License

Copyright 2016-2018 brunomcustodio, puzpuzpuz

Licensed under the Apache License, Version 2.0 (the "License").
