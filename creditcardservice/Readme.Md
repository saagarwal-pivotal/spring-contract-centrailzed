# Spring cloud Contracts - Consumer Side
---

### Consumer Side Changes


### Step 1

Generate the stub jar from centralized maven repo and publish it to local. For details on how to generate stub jar
go  (centralizedcontracts project repo)



### Step 2

Adding the latest maven dependency of spring cloud contract stub runner

```
	<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-contract-stub-runner</artifactId>
			<version>1.2.1.RELEASE</version>
		</dependency>
```

### Step 3

Add the stub jar to integration test and wire mock will start serving the stubs

```
@AutoConfigureStubRunner(ids = "com.retailbank:creditcheckservice:+:stubs:8080", workOffline = true)
```

### Step 4

Run the test and test should pass