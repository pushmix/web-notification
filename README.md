# [Pushmix](https://www.pushmix.co.uk) - web push notification service
Service allows to create and push customised web notification including 
* audience segmentation via topic subscription 
* customised opt in prompt
* real time user interaction in Google Analytics
* custom notification icon and badge
* action buttons with icons
* notification logs
* large image support


## Requirements
* write access to the website files
* website url must starts with `https://`

## Getting Started
This instructions will describe how to creating your first subscription opt in prompt, 
start build up your subscribers audience and push notifications.

First step is to create new account,simply login using Google or Facebook accounts [Pushmix - login](https://dash.pushmix.co.uk/login).
Alternatively create new account here - [Pushmix - register](https://dash.pushmix.co.uk/register). Only details that requiried is a name of your choice and email address.

### New Subscription

#### Creating subscription

In the dashboard you will be asked to create your first subscription, go for it.
Enter your website full URL, starting with `https://` where you wish to display your notification opt in.
Enter opt in title and optional line of text to provide subscribers with more details about this subscription.

You can edit subscription details and change all fields in exception of website address. If you have added website address wrong simply delete subscription and start again.

User can create more than one website subscription.

![alt text](img/new_1.png "1.Details")

You can review opt in prompt by pressing `Preview` button, continue entering details and see changes in real time.


![alt text](img/new_2.png "Preview opt in prompt")

In the Topics tab you can specify up to two optional topics allowing users to receive targeted notifications.

![alt text](img/new_3.png "Topics")

![alt text](img/new_4.png "Topics")

On the third step you can specify notification icon, badge and Google Analytics tracking id, all these field are optional. Icon is the small image that displayed next to the tile and the body if the notification. Recommended icon image dimensions is 192x192 pixels. Badge is monochrome icon that used to provide more information to the user about where the notification sender. At the time of writing the badge is only used on Chrome for Android.

Some browsers the icon and badge images to be served over HTTPS.

Both of these fields are optional, however if the icon and badge values are not provided, default Pushmix icons will be used.

Track user interactions in real time with Google Analytics Event Tracking. Enter your GA Tracking Id to receive web notification views and action button click events.

 ![alt text](img/new_5.png "Extra")


#### Adding Subscription Code

**Service Worker**
After you have created subscription, first thing to do is to download `service worker` and upload it to the root of public directory on your web server.The `service worker` file must be accessible via public URL under the domain name you wish to push web notifications from.

For example `https://www.pushmix.co.uk/pm_service_worker.js`

If you wish to place service worker file inside of any other folders on your server, fill free to do so. However please don't forget to update service worker URL path in the tracking code, see bellow.

* What is the Service Worker ?

A Service Worker is a script that allows access to push notifications. Web Browser executes this script in the background, separate from the web page. Service workers only run over HTTPS, for security reasons.

See Google [search results](https://www.google.co.uk/search?safe=strict&ei=eC7GW_2iGszCgAaksp6QAQ&q=service+workers&oq=service+workes&gs_l=psy-ab.12...0.0..15074...0.0..0.0.0.......0......gws-wiz.NGcT7bDgRlo) for details and use of `service workers`.

* Do I have to use Service Worker?

Yes, Push Notifications are built on top of Service Worker API, which responds to push message events in the background and relays them to your application


**Subscription Code**

*Please do not use the subscription code bellow, this is only for illustration purposes.*
Copy and paste subscription code (subscriber id is unique for each subscription) at the bottom of the web page and start building your audience. You can add subscription code to more than one page. When webpage is loaded subscription code trigger the opt in prompt to be displayed. In the event when web browser is not supported opt in prompt will not be shown.

You can easily change the behaviour and trigger opt in prompt to be displayed on the button click instead o the page load. 

```javascript
<script type="text/javascript">
    var _pm = {
        "subscriber_id": "UNIQUE_SUBSCRIPTION_ID",
        "sw" : "https://www.pushmix.co.uk/pm_service_worker.js",
        "api": "https://www.pushmix.co.uk/api/"
    };
    (function(){
        var block = document.createElement('script');
        block.type = 'text/javascript';
        block.async = false;
        block.defer = true;
        block.src = 'https://www.pushmix.co.uk/js/pm.js';
        var el = document.getElementsByTagName('script')[0];
        el.parentNode.insertBefore(block, el);
    })();  
</script> 
```

![alt text](img/new_4.png "Preview opt in prompt")