## ![Pushmix](https://www.pushmix.co.uk/media/favicons/favicon-32x32.png) Pushmix - Web Push Notification Service

[https://www.pushmix.co.uk](https://www.pushmix.co.uk)

Pishmix is a web push notification service, aiming at effectively re-engaging website visitors with customized web notifications. Our service relies on Firebase Cloud Messaging cross-platform messaging solution. It's is free to register and use Pushmix service.

You will need Subscription ID to use it. The Subscription ID is free and can be obtained from [pushmix.co.uk](https://www.pushmix.co.uk).

Features includes:
* audience segmentation via topic subscription 
* customised opt in prompt
* real time user interactions in Google Analytics
* custom notification icon and badge
* action buttons with icons
* notification logs
* large image support
* Laravel package
* WordPress plugin

View all available [features](https://www.pushmix.co.uk/features) or see [documentation](https://www.pushmix.co.uk/docs) for more details.



## Requirements
There are a few requirements must be met in order to uset this service:

* write access to the website files
* website url must served via `HTTPS://` or run on `localhost` to display opt inn prompt


Google Tag Manager can be used to include required JavaScript. See Google search results for articles that describes this process.




## Getting Started
To use this service, you are required to create an account, the only details that are required: name and email address. It's is free to register and use Pushmix service.

By creating an account and using our service you agree to be bound with our [Terms & Conditions](https://www.pushmix.co.uk/terms), including our [Privacy Policy](https://www.pushmix.co.uk/privacy).

Fastest way to sign up is login with Google or Facebook accounts - [Login](https://dash.pushmix.co.uk/login). Alternatively [Register](https://dash.pushmix.co.uk/register) new account by simply entering name, email addresses and password of your choice.




### Creating subscription


**1. Details**

In the dashboard click New Subscription and enter your website address where you wish visitors to subscribe for web notifications. Enter title and optional line of text to provide subscribers with more details what they subscribing for.

All subscription details can be edited later in exception of website address.

To review opt in prompt click Preview button, continue entering details and see changes in real time.

All subscription details can be changed at later time in exception of website address. If you have added website address wrong simply delete subscription and start again.

User can create more than one website subscription.

![alt text](https://pushmix.github.io/web-notification/img/new_subscription_details_1.png "1.Details")

You can review opt in prompt by pressing `Preview` button, continue entering details and see changes in real time.


![alt text](https://pushmix.github.io/web-notification/img/new_subscription_details_2.png "Preview opt in prompt")

**2. Topics**

Topics are important elements of subscription and allow users to subscribe only for notifications of specific types i.e. Special Offers .

Topics allows you to segment audience and target only those users who have subscribed to a specific topic. For example send notification only to those users who have opted in for Special Offers.

However topics are optional and you can skip this step.

To review opt in prompt click Preview button, continue entering details and see changes in real time.

![alt text](https://pushmix.github.io/web-notification/img/new_subscription_topics_1.png "Topics")


**3. Extra**

Notification icon, badge and Google Analytics tracking id, all these parameters are optional.

Icon is the small image that displayed next to the title and the body if the notification. Recommended icon image dimensions is 192x192 pixels.

Badge is monochrome icon that used to provide more information to the user about where the notification sender. At the time of writing the badge is only used on Chrome for Android. Some browsers only allow icon and badge images to be served over HTTP.

Both of these fields are optional, however if the icon and badge parameters are not provided, default Pushmix icons will be used.

Track user interactions in real time with Google Analytics Event Tracking. Enter your GA Tracking Id to receive web notification views and action button click events.

Press Submit to create subscription, if all mandatory fields supplied correctly instructions on how to embed subscription code will be displayed.

![alt text](https://pushmix.github.io/web-notification/img/new_subscription_extra_1.png "Extra")




### Installation

Currently two options are available to integrate Pushmix service with your website.

|                                                                                         Laravel                                                                                         |                                                                          WordPress                                                                          |                                                                                         JavaScript                                                                                        |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| [Laravel package](https://github.com/pushmix/laravel-web-notification) allows to include opt-in prompt with just one line of code and send web notifications from Laravel applications. | Integrate with [WordPress](https://github.com/pushmix/wordpress-web-notifications) just with few clicks and push notifications from your website dashboard. | JavaScript integration is as simple as copy and paste a few lines of code to the footer of the webpage. Including subscription code in the webpage will trigger to display opt-in prompt. |
| Subscription opt-in prompt in your templates                                                                                                                                            | Send web notifications from WordPress Dashboard                                                                                                             | JavaScript integration can also be performed via Google Tag Manager.                                                                                                                      |
| Send push notification messages from Laravel application                                                                                                                                | Choose pages and posts to display opt-in prompt                                                                                                             |                                                                                                                                                                                           |


If you using Laravel Package or WordPress Plugin you can skip Installation section.


**Service Worker**

[Download](https://dash.pushmix.co.uk/js/pm_service_worker.js) service worker and upload it to the root of public directory on your web server. The service worker file must be accessible via public URL under the domain name you wish to push web notifications from. 

For example my website domain name is `pushmix.co.uk` than Service Worker must be accessible via this URL:
`https://www.pushmix.co.uk/pm_service_worker.js`

If you wish to place service worker file inside of any other folders on your server, fill free to do so. However please don't forget to update service worker URL path in the tracking code, see bellow.

See Google [search results](https://www.google.co.uk/search?safe=strict&ei=eC7GW_2iGszCgAaksp6QAQ&q=service+workers&oq=service+workes&gs_l=psy-ab.12...0.0..15074...0.0..0.0.0.......0......gws-wiz.NGcT7bDgRlo) for details and use of service workers.



**Subscription Code**

Copy subscription code from dashboard and paste it at the bottom of the web page to start building your audience. You can add subscription code to more than one page. When webpage is loaded subscription code trigger the opt in prompt to be displayed. In the event when web browser is not supported, opt in prompt will not be displayed.

The subscription code can also be added via Google Tag Manager, please see Google [search results](https://www.google.co.uk/search?q=Adding+Custom+JavaScript+to+Your+Website+Using+Google+Tag+Manager&oq=Adding+Custom+JavaScript+to+Your+Website+Using+Google+Tag+Manager) for articles that describes this process.

```javascript
<script type="text/javascript">
    var _pm = {
        "subscriber_id": "UNIQUE_SUBSCRIPTION_ID",
        "sw" : "https://YOUR_DOMAIN_NAME/pm_service_worker.js",
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

By default subscription code is set to load opt in prompt stright after the web page is loaded. This behavior can be quickly adjusted and tailored to your own needs, for example to display opt in prompt on click event.

![alt text](https://pushmix.github.io/web-notification/img/new_4.png "Preview opt in prompt")

Visit the section of your website where you have added the subscription code to ensure the opt in prompt is working as expected. Any changes to the subscription details applied on the dashboard will have immediate effect in the opt in prompt, web page reload may be required.

Opt in prompt can be used to subscribe for push notifications as well as toggle subscription states or unsubscribe from further notifications.

Notification scription is based on Web Browser token and one device can subscribe multiply times.




### Sending Notifications

Dashboard displays one or more of your subscriptions summary. Press Push Notification button at the bottom of subscription card.

There are three steps that you will need to go through to prepare notification message: Select Audience, Enter Content and Actions.



#### 1. Audience


**Audience**

From the dropdown select subscribers Audience you would like to target, by default all subscribers are selected. Number in the brackets indicating total number of subscribers for each topic.

If you have specified additional topics, they also be available for selection from dropdown box. Only one audience group can be selected at a time.

Priority dropdown consists of two choices High and Normal, High is selected by default. This feature regulate how push notification being delivered.

High priority messages attempted to be delivered immediately.

Normal priority messages won't open network connections on a sleeping device, and message delivery may be delayed to conserve battery.

Maximum notification lifespan of a message correspond to the maximum period of time for which message delivery will be attempted, 1 Hour is default choice. This feature helps to prevent from delivering messages with content that no longer relevant.

Consider subscriber device is turned off and you sending a message containing discount code that expire today at 6pm. Subscriber switch on it's device on the following day to receive push notification with discount code that can't be used.

![alt text](https://pushmix.github.io/web-notification/img/push_notification_1.png "Dashboard")
![alt text](https://pushmix.github.io/web-notification/img/push_notification_2.png "Audience")


#### 2. Content

**Notification Title, Body and URL**

Enter notification Title and Body, keep it brief. In the URL field enter valid website address, when user clicks or press on notification this URL will be loaded in the web browser.

![alt text](https://pushmix.github.io/web-notification/img/push_notification_2.png "2. Content")



#### 2. Actions

You can define up to two action buttons to be displayed with a notification. All fields are optional, however if you choose to specify Action Title than Action URL is required.

Additionally you can select an icon from dropdown list to displayed on the button. Please not action icons may not be displayed.

**Image URL**
Large image can be included in notification body, recommended width of 1350px or more would be a good bet. Simply enter valid image URL.


![alt text](https://pushmix.github.io/web-notification/img/push_notification_4.png "3. Actions")


**Testing**

It's always good to push test notification and preview results before sending message to your subscribers, simply press `Push Test` button. If you web browser supports push notifications you will see one shortly.

Once you happy with test press Push Notification button and your notifications will start being dispatched. Check your Google Analytics Real-Time Events section to see user interactions with notification you just send.

In case when your web browser is not compatible with push notifications you can still send the message by pressing Push Notification button to selected subscribers audience.

| Windows Chrome  69| 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_windows_chrome_69.png "Windows Chrome 69")|

| Windows Firefox  63| 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_windows_ff_63.png "Windows Firefox 63")|


| Linux Firefox 62  | 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_linux_firefox_62.png "Linux Firefox 62")|

| Linux Chromium 69 | 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_linux_chromium_69.png "Linux Chromium 69")|


| Linux Chrome 69 | 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_linux_chrome_69.png "Linux Chrome 69")|


| Samsung Chrome 70  | 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_samsung_chrome_70.png "Linux Chrome 70")|


| Samsung Internet 7  | 
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_samsung_internet_7.png "Linux Internet 7")|


### Logs

Eash subscription card has it's own list of actions, Logs is one of them.

Logs keep track of all notifications you have dispatched and consists of two available views: Summary and Details.

**Summary**

Summary view display all notification campaigns that have been sent out in descending order, including:

* Notification Title
* Audience
* Number of Successfully delivered notifications
* Number of Failed notifications
* Notification Dispatched date

All notification summary details can be exported in CSV.


**Details**

Detail view display information about the devices that received this notification including:

* Device Type (i.e Desktop)
* Device Operating System (i.e Windows)
* Device Web Browser (i.e Chrome)
* Device Web Browser Version (i.e 69.0)
* Geographical City of the device
* Postcode
* Country

The geographical device details are optined during interaction with opt in prompt and may not represent current device location.

There are also five graphs and map are available that visualize above information.

![alt text](https://pushmix.github.io/web-notification/img/logs_summary.png "Logs Summary")
![alt text](https://pushmix.github.io/web-notification/img/logs_details.png "Logs Details")
![alt text](https://pushmix.github.io/web-notification/img/logs_details_2.png "Logs Details")
