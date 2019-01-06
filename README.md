## ![Pushmix](https://www.pushmix.co.uk/media/favicons/favicon-32x32.png) Pushmix - Web Push Notification Service

[https://www.pushmix.co.uk](https://www.pushmix.co.uk)

Pushmix is effective and dependable web service helping to reconnect with your audience through customised web push notifications.

`  The service is FREE to register and use.  `

### Requirements
Following requirements must be met in order to use Pushmix service:

* Website must be served via `HTTPS://`

` Don't have SSL, check out [Cloudflare](https://dash.cloudflare.com/sign-up) `

You will need Subscription ID to use it. The Subscription ID is free and can be obtained from [pushmix.co.uk](https://dash.pushmix.co.uk/login).

### Features
* Audience segmentation via topic subscription
* Customised opt-in prompt
* Action buttons
* Open and Click Through Rate Stats
* Integration with Google Analytics
* Customised notification icon and badge
* REST API
* Laravel and WordPress integration
* Large image support
* Notification Lifespan
* Subscriber device information
* Subscriber device GEO location



### Getting Started
This documentation designed to help you to start using the Pushmix service and send notification messages just in few minutes, no specific technical skills are required.

For users wishing to have more control and send notifications directly from your own application checkout our [Laravel package](https://www.pushmix.co.uk/docs/laravel-package), [WordPress plug-in](https://www.pushmix.co.uk/docs/wordpress-plugin) or [API section](https://www.pushmix.co.uk/docs/api).

By creating an account and using our service you agree to be bound with our [Terms & Conditions](https://www.pushmix.co.uk/terms), including our [Privacy Policy](https://www.pushmix.co.uk/privacy).


### Workflow

* **01 - Sign Up**
> Create an account and login to your dashboard.


* **02 - Create Subscription**
> Enter opt-in prompt _Title_ and _Description_, add up to two optional _Topics_ to segment your audience, provide optional _Icon URL_ and _Google Analytics Tracking ID_


* **03 - Integration**
> Copy and paste a few lines of JavaScript or use our [Laravel package](https://github.com/pushmix/laravel-web-notification) or [WordPress plug-in](https://github.com/pushmix/wordpress-web-notifications). For dipper integration with your application see [API section](https://www.pushmix.co.uk/docs/api).


* **04 - Grow Audience**
> Build up and grow your audience by displaying opt-in prompt on more than one of your web pages and encourage visitors to subscribe to your push notifications.


* **05 - Engage**
> Engage your audience with time-sensitive, relevant and accurate push notification messages. Send notifications from [Pushmix Dashboard](https://dash.pushmix.co.uk/login), if you are using one of our plug-ins or prefer API you can send notifications directly from your application.

* **06 - Analyse**
> Review and analyse notification stats to improve your performance.


### Create Subscription



**1. Details**

In the dashboard click _New Subscription_ and enter your *Website URL* and the opt-in prompt *Title*. Use the optional *Description* field to motivate your visitors to subscribe to your notifications.

All subscription details can be edited later, in exception of the website address.


![alt text](https://pushmix.github.io/web-notification/img/new_subscription_details_1.png "1.Details")

Use the _Preview_ button to view the opt-in prompt, continue entering details and see changes in real time.


![alt text](https://pushmix.github.io/web-notification/img/new_subscription_details_2.png "Preview opt-in prompt")

**2. Topics**

Topics are important elements of subscription, allowing users to subscribe only for notifications of their interests i.e. Order Dispatched.

Topics allow you to segment your subscriber's audience and target only those users who have expressed interest in the specific subject. For example, send notification only to those users who have opted in for Order Dispatched topic.

However, topics are optional and you can skip this step.

![alt text](https://pushmix.github.io/web-notification/img/new_subscription_topics_1.png "Topics")


**3. Extra**

*Notification Icon URL*, *Badge Icon URL* and *Google Analytics Tracking ID* are optional parameters.

The *Icon URL* is the small image that displayed next to the title and the body of the notification. Recommended icon image dimensions are 192x192 pixels.  [Read more](https://developers.google.com/web/fundamentals/push-notifications/display-a-notification#icon).

The *Badge URL* is a monochrome icon that used to provide more information to the user about the notification sender.  [Read more](https://developers.google.com/web/fundamentals/push-notifications/display-a-notification#badge).

If *Icon URL* and *Badge URL* parameters are not provided, default Pushmix icons will be used.

Track user interactions in real time with Google Analytics Event Tracking. Enter your GA Tracking ID to receive web notification views and click events.

Press _Submit_ to create the subscription, instructions on how to embed subscription code will be displayed.

![alt text](https://pushmix.github.io/web-notification/img/new_subscription_extra_1.png "Extra")


### Subscription ID

After you have created new subscription the *Subscription ID* will be displayed on the screen. The *Subscription ID* can also be found later in the Dashboard under subscription _Code_ section.

If you choose [Laravel Package](https://github.com/pushmix/laravel-web-notification) or [WordPress Plug-in](https://github.com/pushmix/wordpress-web-notifications) you will only need *Subscription ID*.

With JavaScript integration, you require to upload *Service Worker* file to the web server and include few lines of JavaScript at the bottom of the page to display subscription opt-in prompt for your visitors to subscribe for web notifications.


### Installation

Following methods are available to integrate Pushmix service:

* JavaScript (see below)
* [Web Push Notifications for Laravel](https://github.com/pushmix/laravel-web-notification)
* [Web Push Notifications for WordPress](https://github.com/pushmix/wordpress-web-notifications)

If you using Laravel Package or WordPress Plug-in you can skip Installation section.

`  For notifications open rate and click through stats you will need to login to Pushmix Dashboard. `

**Service Worker**

[Download](https://dash.pushmix.co.uk/js/pm_service_worker.js) service worker and upload it to the root of the public directory on your web server. The service worker file must be accessible via public URL under the domain name you wish to send web notifications from.

For example, my website domain name is `pushmix.co.uk` than Service Worker must be accessible via this URL:

` https://www.pushmix.co.uk/pm_service_worker.js `


**Subscription Code**

Copy subscription code from the dashboard and paste it at the bottom of the web page to start building your audience. You can add subscription code to more than one page. When a webpage is loaded subscription code trigger the opt-in prompt to be displayed. In the event when the web browser is not supported, the opt-in prompt will not be displayed.


```javascript
<script type="text/javascript">
    var _pm = {
        // replace with your Subscription ID
        "subscriber_id": "UNIQUE_SUBSCRIPTION_ID",
        // replace with Service Worker UR under your domain
        "sw" : "https://YOUR_DOMAIN_NAME/pm_service_worker.js",

        // PLEASE DO NOT EDIT BELLOW
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

` Include Subscription Code using Google Tag Manager [Custom HTML tag](https://support.google.com/tagmanager/answer/6107167?hl=en). `


**Opt-in Prompt**
![alt text](https://pushmix.github.io/web-notification/img/new_4.png "Preview opt-in prompt")

Visit the section of your website where you have added the subscription code to ensure the opt-in prompt is working as expected. Any changes to the subscription details applied in the Pushmix Dashboard will have an immediate effect, web page reload may be required.

The opt-in prompt can be used to subscribe for push notifications as well as toggle subscription states or unsubscribe from further notifications.




### Sending Web Push Notifications

In the Dashboard you will find one or more of your subscriptions cards. Press **Push Notification** button at the bottom of subscription card.

There are three steps that you will need to go through to prepare notification message: _Select Audience_, _Enter Content_ and specify _Actions_.





#### 1. Audience


**Audience**

From the drop-down select subscriber's Audience, you would like to target, by default all subscribers are selected. The number in the brackets indicating the total number of subscribers for each topic*.

`  *Number of subscribers only available in the Pushmix Dashboard. `

If you have specified additional topics, they are available from the drop-down box. Only one audience group can be selected at a time.

Priority drop-down consists of two choices *High* and *Normal*

*High* is selected by default. This feature regulates how push notification being delivered, priority messages attempted to be delivered immediately.

*Normal* priority messages won't open network connections on a sleeping device, and message delivery may be delayed to conserve battery.

*Notification Lifespan* of a message corresponds to the maximum period of time for which message delivery will be attempted, 1 Hour is default choice. This feature helps to prevent from delivering messages with content that no longer relevant.


![alt text](https://pushmix.github.io/web-notification/img/push_notification_1.png "Dashboard")
![alt text](https://pushmix.github.io/web-notification/img/push_notification_2.png "Audience")


#### 2. Content

**Notification Title, Body and URL**

Enter notification *Title* and *Body*, keep it brief. In the *URL* field enter a valid website address, when a user clicks or press on notification this *URL* will be loaded in the web browser.

![alt text](https://pushmix.github.io/web-notification/img/push_notification_2.png "2. Content")



#### 2. Actions

You can define up to two action buttons to be displayed with a notification. All fields are optional, however, if you choose to specify *Action Title* than *Action URL* is required.

Additionally, you can select an icon from the drop-down list to display on the button. Please note: action icons may not be displayed.


**Image URL**
The large image can be included in the notification body, recommended the width of 1350px or more would be a good bet. Simply enter valid image URL.


![alt text](https://pushmix.github.io/web-notification/img/push_notification_4.png "3. Actions")


**Testing**

It's always good to test notification and preview results before sending it out. Simply press *Push Test* button. If your web browser supports push notifications you will see one shortly.

Once you happy with test press *Push Notification button* and your notifications will be dispatched. Check your Google Analytics Real-Time Events section to see user interactions with web notifications you just send.

| Windows Chrome  69|
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_windows_chrome_69@2.png "Windows Chrome 69")|

| Windows Firefox  63|
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_windows_ff_63@2.png "Windows Firefox 63")|


| Linux Firefox 62  |
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_linux_firefox_62@2.png "Linux Firefox 62")|

| Linux Chromium 69 |
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_linux_chromium_69@2.png "Linux Chromium 69")|


| Linux Chrome 69 |
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_linux_chrome_69@2.png "Linux Chrome 69")|


| Samsung Chrome 70  |
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_samsung_chrome_70@22.png "Samsung Chrome 70 ")|


| Samsung Internet 7  |
| ------------- |
| ![alt text](https://pushmix.github.io/web-notification/img/notification_example_samsung_internet_7@22.png "Samsung Internet 7")|


### Logs

Eash subscription card has its own list of actions, Logs is one of them.

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

The geographical device details are obtained during interaction with opt-in prompt and may not represent the current device location.

There are also five graphs and map are available that visualize above information.

![alt text](https://pushmix.github.io/web-notification/img/logs_summary.png "Logs Summary")
![alt text](https://pushmix.github.io/web-notification/img/logs_details.png "Logs Details")
![alt text](https://pushmix.github.io/web-notification/img/logs_details_2.png "Logs Details")


### Issues
If you come across any issues please report them [here](https://github.com/pushmix/web-notification/issues).

### Security Vulnerabilities
If you discover a security vulnerability please send an e-mail to support@pushmix.co.uk.
