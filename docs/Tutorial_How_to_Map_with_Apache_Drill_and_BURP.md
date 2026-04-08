# Knowledge Graph Mapping with Apache Drill and BURP

## 1. Requirements

- Java 17.0.12
- Maven 3.9.9
- Docker

---

## 2. Setting Up Apache Drill with Docker

### 2.1 Download the Drill Docker Image

```bash
docker pull apache/drill:master-openjdk-17
````

### 2.2 Launch the Drill Container

```bash
docker run -it -p 8047:8047 -p 31010:31010 \
  -v /path/to/your/json/folder:/data \
  --name drill apache/drill:master-openjdk-17 \
  /bin/bash
```

Replace `/path/to/your/json/folder` with the path to your local folder containing JSON files.

### 2.3 Start Drill

Make sure the Drill Docker container is running. You can now access the Drill Web UI at [http://localhost:8047](http://localhost:8047).


### 2.4 Configure a Drill Workspace

1. Open the Drill Web UI.
2. Click **Storage**.
3. Click **Update** next to `dfs`.
4. Add a workspace (e.g., `statements`) in the JSON section:

```json
"statements": {
  "location": "/data",
  "writable": false,
  "defaultInputFormat": null,
  "allowAccessOutsideWorkspace": false
}
```

### 2.5 Running SQL Queries on JSON Files

Example query:

```sql
SELECT FLATTEN(statements) AS flatdata
FROM dfs.statements.`*.json`;
```

This will read all `.json` files in `/data` and flatten the `statements` arrays.

---

## 3. Building BURP with Required Dependencies

Clone BURP and update the `pom.xml` to include the following dependencies:

```xml
<dependency>
  <groupId>org.apache.drill.exec</groupId>
  <artifactId>drill-jdbc</artifactId>
  <version>1.22.0</version>
</dependency>
<dependency>
  <groupId>com.google.guava</groupId>
  <artifactId>guava</artifactId>
  <version>33.4.8-jre</version>
</dependency>
```

Then compile BURP:

```bash
mvn package -DskipTests
mvn dependency:copy-dependencies
```

This will generate:

* `BURP-0.1.2-SNAPSHOT.jar`
* a `dependencies/` folder

Copy both into the same folder as your mapping files.

---

## 4. Running Mappings with BURP

**Important:** Make sure the Drill Docker container is started and running before executing mappings.

### 4.1 Running a Single Mapping

From the folder containing the JAR, `dependencies/`, and your mapping file (`.ttl`):

```bash
java -jar BURP-0.1.2-SNAPSHOT.jar -m=MappingFile.ttl -o=OutputFile.nq
```

Example:

```bash
java -jar BURP-0.1.2-SNAPSHOT.jar -m=AccessQuestion.ttl -o=AccessQuestion.nq
```

### 4.2 Running All Mappings in Batch

If all mappings (`.ttl`) are stored in the same folder, you can run:

```bash
java -jar BURP-0.1.2-SNAPSHOT.jar -m=ReceiveFbComplete.ttl -o=ReceiveFbComplete.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=ReceiveFbNoExt.ttl -o=ReceiveFbNoExt.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=AccessQuestion.ttl -o=AccessQuestion.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=Update.ttl -o=Update.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=App.ttl -o=App.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=Answer.ttl -o=Answer.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=Version.ttl -o=Version.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=ReceiveFbNoSB.ttl -o=ReceiveFbNoSB.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=AAC.ttl -o=AAC.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=ReceiveSurvey.ttl -o=ReceiveSurvey.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=AccessFbParts.ttl -o=AccessFbParts.nq
java -jar BURP-0.1.2-SNAPSHOT.jar -m=ReceiveMessage.ttl -o=ReceiveMessage.nq
```








