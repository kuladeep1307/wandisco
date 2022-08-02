
Clean Hive Notifications Table Procedure
===============================

1. Copy the zip folder scripts.zip into /opt/wandisco/hivemigrator/
2. Then UnZip the folder "unzip scripts.zip"
3. Give execute rights to sh files chmod +x to the scripts in the bin dir 
4. Stop the Hive Migrator service "service hivemigrator stop" before running the clean notify script
5. To clear all the notifications in the Hive Database you need to run /opt/wandisco/hivemigrator/bin/clean-notification.sh. 
When the script is running the following successful connections will be output to screen

/opt/wandisco/hivemigrator/bin/clean-notification.sh
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/opt/wandisco/hivemigrator/log4j-slf4j-impl-2.17.1.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/opt/wandisco/hivemigrator/hivemigrator-agent-remote-facade-1.10.3-all.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/opt/wandisco/hivemigrator/hivemigrator-hikari-1.10.3-all.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [org.apache.logging.slf4j.Log4jLoggerFactory]

6.  Once the previous command has completed then restart the Hive Migrator service again "service hivemigrator start"

7. Then check if the script has executed correctly by checking the  REST API endpoint /notifications ie "http://hostname.com:6780/notifications?excludeResolved=false" and verify that only one entry exists. Showing the successful restart of the Hivemigrator process ie:
 {
  "level" : "INFO",
  "type" : "APPLICATION_STATE",
  "message" : "Hive migrator has started localhost:6780",
  "id" : "urn:uuid:e9ff3609-cb50-4e9f-bcd5-484d7c06c77e",
  "timeStamp" : 1658406027362,
  "code" : 200300,
  "resolved" : true,
  "updatedTimeStamp" : 1658406027362,
  "payload" : {
    "host" : "localhost",
    "port" : "6780"
  },
  "dateCreated" : "2022-07-21T12:20:27.362+00:00",
  "dateUpdated" : "2022-07-21T12:20:27.362+00:00"
} ]



