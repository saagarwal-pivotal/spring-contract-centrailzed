# Spring cloud Contracts - Provider Side
---

### Provider Side Changes using centralized contracts repo


### Step 1

 1. Add contract verifier dependency 
 2. Add dependency management to pull in all additional cloud depenedencies
 3. Add maven plugin for generating stubs and running contract test

```

		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-contract-verifier</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-dependencies</artifactId>
				<version>Edgware.RELEASE</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
			<plugin>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-contract-maven-plugin</artifactId>
				<version>1.2.1.RELEASE</version>
				<extensions>true</extensions>
				<configuration>
					<baseClassForTests>com.retailbank.creditcheckservice.BaseContractTest</baseClassForTests>
					<contractsWorkOffline>true</contractsWorkOffline>
					<contractDependency>
						<groupId>com.retailbank</groupId>
						<artifactId>contracts</artifactId>
					</contractDependency>
				</configuration>
			</plugin>
		</plugins>
	</build>
```

Note contracts jar is referred in plugins section that has all the contracts

workoffline means check into local repository 


### Step 2

Add the base contract test class that will stub the service and set up the controller
