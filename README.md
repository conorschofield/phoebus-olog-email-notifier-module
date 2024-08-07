# Phoebus Olog Email Notifier Module

This is an optional module for the Phoebus Olog electronic logbook service, see https://github.com/Olog/phoebus-olog. Its purpose is to send an email when a log is sent based on a list of emails mapped to the logbook entry's tag. 

The module uses Simple Java Mail to send emails (Email java library: https://www.simplejavamail.org/).

### Configuration

#### Add these to phoebus olog:

pom.xml
```
<dependency>
    <groupId>org.phoebus</groupId>
    <artifactId>olog-email-notifier-module</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>jakarta.activation</groupId>
    <artifactId>jakarta.activation-api</artifactId>
    <version>2.1.3</version>
</dependency>
<dependency>
    <groupId>com.sun.mail</groupId>
    <artifactId>jakarta.mail</artifactId>
    <version>2.0.1</version>
</dependency>
```

Example tagsToEmails.json
```
{
    "tagsToEmails": 
    {
      "tag1": ["email1@example.com"],
      "tag2": ["email2@example.com", "email3@example.com"]
    }
}  
```
Add the following to olog application.properties
Properties file:
```
olog.tagsToEmailsFilePath=/pathToTagsToEmails.json

simplejavamail.transportstrategy=SMTPS
simplejavamail.smtp.host=smtp.default.com
simplejavamail.smtp.port=25
simplejavamail.defaults.from.name=From Default
simplejavamail.defaults.from.address=from@default.com
```

See: https://www.simplejavamail.org/configuration.html#section-available-properties for more simplejavamail properties