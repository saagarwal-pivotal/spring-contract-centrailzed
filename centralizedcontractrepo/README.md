# spring-cloud-contract-centralized-contract-repo
---

Idea is to isolate contracts into a separate repository so both teams 
can have access to common repo. This is ideal when two independent teams
are working on implementing providers and consumers.

Folder structure is 

```
Maven group Id
    providerNameA
        -- ConsumerX
            -- ContractA
            -- ContractB
        -- ConsumerY
        
     providerNameB
         -- ConsumerX
            -- ContractA
            -- ContractB
        -- ConsumerY
        
        
```

Contract.xml is used for assembly of artifacts


### How to generate stubs for consumer

Every provider project has a pom file that has the spring contract verifier maven plugin

Running below command will generate the stubs for consumer and contracts jar

```
mvn clean install -DskipTests

```