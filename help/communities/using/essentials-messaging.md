---
title: Messaging Essentials
seo-title: Messaging Essentials
description: Messaging component overview
seo-description: Messaging component overview
uuid: 6e5a28b1-5615-4c59-b65c-0a1fb5e4d14f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 1f84c5c6-7c45-4efc-a873-99ee0867d0fa
---

# Messaging Essentials{#messaging-essentials}

This page documents the details of working with using the Messaging component to include a messaging feature on a website.

## Essentials for Client-Side {#essentials-for-client-side}

<table border="1" cellpadding="4" cellspacing="4" width="100%"> 
 <tbody> 
  <tr> 
   <th colspan="2" style="text-align: center;">Compose Message</th> 
  </tr> 
  <tr> 
   <td style="text-align: center;"> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/composemessage</p> </td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"> <a href="../../communities/using/client-customize.md#clientlibsforscf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"><strong>properties</strong></td> 
   <td>see <a href="../../communities/using/configure-messaging.md">Confiiguring Messaging</a></td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"><strong>admin configuration</strong></td> 
   <td><a href="../../communities/using/messaging.md">Configuring Messaging</a></td> 
  </tr> 
 </tbody> 
</table>

<table border="1" cellpadding="4" cellspacing="4" width="100%"> 
 <tbody> 
  <tr> 
   <th colspan="2" style="text-align: center;">Message List</th> 
  </tr> 
  <tr> 
   <td colspan="2" style="text-align: center;">(for Inbox, Sent, and Trash)</td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"> <a href="../../communities/using/client-customize.md#clientlibsforscf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"><strong>properties</strong></td> 
   <td>see <a href="../../communities/using/configure-messaging.md">Confiiguring Messaging</a></td> 
  </tr> 
  <tr> 
   <td style="text-align: center;"><strong>admin configuration</strong></td> 
   <td><a href="../../communities/using/messaging.md">Configuring Messaging</a></td> 
  </tr> 
 </tbody> 
</table>

See also [Client-side Customizations](../../communities/using/client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [Configuring Messaging](../../communities/using/configure-messaging.md)

* [Messaging client APIs](/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary) for SCF components

* [Messaging APIs](/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary) for the service

* [Messaging Endpoints](/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary)

* [Server-side Customizations](../../communities/using/server-customize.md)

>[!CAUTION]
>
>The String parameter must *not *contain a trailing slash "/" for the following MessageBuilder methods :
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>For example :
>
>```>
>valid : mb.setInboxPath( "/mail/inbox" );
> not valid : mb.setInboxPath( "/mail/inbox/" );
>```>

### Community Site {#community-site}

A community site structure, created using the wizard, will include the messaging feature when selected. See `User Management` settings of [Community Sites Console](../../communities/using/sites-console.md#usermanagement).

### Sample Code : Message Received Notification {#sample-code-message-received-notification}

The Social Messaging feature throw events for operations, for example `send`, `marking read`, `marking delete`. These events can be caught and actions taken on the data contained in the event.

The following example is of an event handler which listens for the `message sent` event and sends an email to all message recipients using the `Day CQ Mail Service`.

To try the server-side sample script, you will need a development environment and the ability to build an OSGi bundle.

1. login as an administrator to ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. create a `bundle node`in `/apps/engage/install` with arbitrary names, such as

    * Symbolic Name : com.engage.media.social.messaging.MessagingNotification
    * Name : Getting Started Tutorial Message Notificaton  
    * Description : a sample service for sending an email notification to users when they receive a message
    * Package : com.engage.media.social.messaging.notification

1. navigate to /apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification

    1. delete the Activator.java class automatically created
    1. create class MessageEventHandler.java
    1. copy/paste the code below into MessageEventHandler.java

1. click **Save All**
1. navigate to /apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd and add all the import statements as written in the MessageEventHandler.java code.
1. build the bundle
1. ensure `Day CQ Mail Service`OSGi service is configured
1. login as one demo user and send email to another
1. the recipient should receive an email regarding a new message

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
