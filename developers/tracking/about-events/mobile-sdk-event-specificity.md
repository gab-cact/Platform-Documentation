# Mobile App event specificity

1. [Event SDK mapping](mobile-sdk-event-specificity.md#event-sdk-mapping)
2. [Event specificity for mobile app](mobile-sdk-event-specificity.md#event-specificity-for-mobile-app)
3. [Fields details](mobile-sdk-event-specificity.md#fields-details)
4. [device](mobile-sdk-event-specificity.md#device)
5. [device -> os](mobile-sdk-event-specificity.md#device---os)
6. [device -> screen](mobile-sdk-event-specificity.md#device---screen)
7. [device -> network](mobile-sdk-event-specificity.md#device---network)
8. [device -> Lifecycle](mobile-sdk-event-specificity.md#device---lifecycle)
9. [app](mobile-sdk-event-specificity.md#app)

A full event is the addition of event specific information and data gathered by the SDK. For each event you'll find in the documentation "events reference" all the possible properties and the mandatory ones.

## Event SDK mapping

To create event, you will need to use classes from the SDK which represents the events. As this might be confusing, you'll find here a list of class name and their event counterparts.

All those class names are valid on both Android and iOS.

| event name          | class name             |
| ------------------- | ---------------------- |
| any custom event    | TCCustomEvent          |
| add\_payment\_info  | TCAddPaymentInfoEvent  |
| add\_shipping\_info | TCAddShippingInfoEvent |
| add\_to\_cart       | TCAddToCartEvent       |
| add\_to\_wishlist   | TCAddToWishlistEvent   |
| begin\_checkout     | TCBeginCheckoutEvent   |
| generate\_lead      | TCGenerateLeadEvent    |
| login               | TCLoginEvent           |
| page\_view          | TCPageViewEvent        |
| purchase            | TCPurchaseEvent        |
| refund              | TCRefundEvent          |
| remove\_from\_cart  | TCRemoveFromCartEvent  |
| search              | TCSearchEvent          |
| select\_content     | TCSelectContentEvent   |
| select\_item        | TCSelectItemEvent      |
| sign\_up            | TCSignUpEvent          |
| view\_cart          | TCViewCartEvent        |
| view\_item          | TCViewItem             |
| view\_item\_list    | TCViewItemListEvent    |

| COMMON SCHEMAS | class name |
| -------------- | ---------- |
| Item           | TCItem     |
| Product        | TCProduct  |
| User           | TCUser     |

| ENUMERATED VALUE | Class name        |
| ---------------- | ----------------- |
| Payment methods  | ETCPaymentMethod  |
| Purchase status  | ETCPurchaseStatus |

## Event specificity for mobile app

IOS and Android SDK add specific properties regarding the device and app. Those are in addition to event managed properties.

{% hint style="info" %}
If you track your mobile applications without using the sdk (with the [http tracking api](../../../features/sources/sources-catalog/http-tracking-api.md)), you should follow this specification to benefit from plug\&play on destinations\\
{% endhint %}

Here are an example of event playload :

```json
{
   "event_name":"add_to_cart",
   "value":22.53,
   "currency":"EUR",
   "user": {
	   "id": "12345",
	   "email": "toto@domain.fr",
	   "consent_categories": ["1", "3"]
   },
   "items":[
      {
         "id":"SKU_12345",
         "quantity":1,
         "product":{
            "id":"12345",
            "name":"Trex tshirt",
            "price":9.99
         }
      }
   ],
   "context":{
      "event_id":"8f6e05dd-6df0-476c-9c56-5d277fac7cea",
      "device":{
         "sdk_id":"a47f71c0-9561-4a26-96d6-0d8632095caa",
         "user_agent":"Mozilla\/5.0 (Linux; Android 13; sdk_gphone64_arm64 Build\/TE1A.220922.012; wv) AppleWebKit\/537.36 (KHTML, like Gecko) Version\/4.0 Chrome\/103.0.5060.71 Mobile Safari\/537.36",
         "manufacturer":"Google",
         "model":"sdk_gphone64_arm64",
         "name":"emu64a",
         "type":"android",
         "network":{
            "bluetooth":false,
            "cellular":false,
            "wifi":true
         },
         "os":{
            "name":"android",
            "version":"13"
         },
         "screen":{
            "width":1080,
            "height":1857,
            "density":2.625
         },
         "timezone":"Europe\/Paris",
         "lifecycle":{
            "session_id":"5ab5fd16-5ebd-42bb-8c9c-b12564370c83",
            "new_session":false,
            "first_execute":false,
            "is_first_visit":true,
            "session_duration":138200,
            "current_session":1673571497826,
            "current_visit":1673571497826,
            "current_version_first_visit":1673571497826,
            "first_visit":1673571497826,
            "last_visit":1673571497826,
            "last_call":1673571632270,
            "last_session_start":0,
            "last_session_last_hit":0,
            "foreground_time":137652,
            "background_time":548,
            "foreground_transitions":2,
            "session_number":1,
            "visit_number":1
         }
      },
      "app":{
         "name":"TCDemo ServerSide And Consent",
         "version":"1.0",
         "build":"1",
         "namespace":"com.tagcommander.tcdemo",
         "core_version":"5.3.1",
         "serverside_version":"5.3.1"
      },
      "event_timestamp":1673571636026
   }
}
```

## Fields details

Here are fields automatically added by the sdk.

(\*) IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**.

### context

| Field name       | Example value                        | Description                                                        | Platform |
| ---------------- | ------------------------------------ | ------------------------------------------------------------------ | -------- |
| event\_id        | 8f6e05dd-6df0-476c-9c56-5d277fac7cea | A random UUID generated at the serialization of the event instance | Both     |
| event\_timestamp | 1673571636026                        | Timestamp of the event sending time.                               | Both     |

### context -> app&#x20;

| Field name          | Example value           | Description                      | Platform |
| ------------------- | ----------------------- | -------------------------------- | -------- |
| namespace           | com.tagcommander.TCDemo | The app name-space               | Both     |
| name                | TCDemo                  | The app name                     | Both     |
| build               | 1                       | The application build ID         | Both     |
| version             | 1.1                     | The app version                  | Both     |
| serverside\_version | 5.1.0                   | The server-side module’s version | Both     |
| core\_version       | 5.1.0                   | The core module’s version        | Both     |

### context -> device

| Field name   | Example value                         | Description                                            | Platform |
| ------------ | ------------------------------------- | ------------------------------------------------------ | -------- |
| manufacturer | Apple                                 | The manufacturer of the hardware                       | Both     |
| model        | iPhone7.3                             | The device model                                       | Both     |
| name         | maguro                                | The device given name                                  | Both     |
| sdk\_id      | C32272DB0-C21E-11E4-8DFC-AA07A5B093DB | A random UUID generated at the first launch of the SDK | Both     |
| timezone     | Europe/Paris                          | The detailed timezone                                  | Both     |
| type         | android                               | The os name                                            | Both     |

The next fields require consent and are added when you call "addAdvertisingIDs" from the ServerSide class.

| Field name            | Example value                        | Description                      | Platform |
| --------------------- | ------------------------------------ | -------------------------------- | -------- |
| advertising\_id       | 705EB54D-9FC7-4730-BF1B-A5D0494E1D8C | Either IDFA or AAD               | Both     |
| idfv                  | 5E35A9BA-C945-4A79-80B6-D89139471308 | IDFV                             | iOS      |
| ad\_tracking\_enabled | true                                 | Has the user enabled ad tracking | Both     |

### context -> device -> os

| Field name | Example value | Description               | Platform |
| ---------- | ------------- | ------------------------- | -------- |
| name       | ios           | The operating system name | Both     |
| version    | 15.5          | The OS version            | Both     |

### context -> device -> screen

| Field name | Example value | Description                 | Platform |
| ---------- | ------------- | --------------------------- | -------- |
| width      | 390           | The device’s screen width   | Both     |
| height     | 844           | The device’s screen height  | Both     |
| density    | 2             | The device’s screen density | Android  |

### context -> device -> network

| Field name | Example value | Description                                      | Platform |
| ---------- | ------------- | ------------------------------------------------ | -------- |
| bluetooth  | false         | Is the bluetooth connected                       | Both     |
| cellular   | true          | Is the cellular connected                        | Both     |
| carrier    | T-Mobile US   | Carrier's name (only when cellular is connected) | Android  |
| wifi       | false         | Is the wifi connected                            | Android  |

### context -> device -> Lifecycle

| Field name                     | Example value                        | Description                                                                                                      | Platform |
| ------------------------------ | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- | -------- |
| session\_id                    | F318C0D1-1DDB-4B53-9326-F2078A97CD38 | An id specific to this session                                                                                   | Both     |
| new\_session                   | false                                | True if this hit is the first of a new session                                                                   | Both     |
| session\_duration              | 8291                                 | The time spent during this session                                                                               | Both     |
| current\_session               | 1655824764174                        | Timestamp of the start of the current session                                                                    | Both     |
| visit\_number                  | 1                                    | Number of times the application was launched                                                                     | Both     |
| current\_visit                 | 1655824764174                        | Timestamp of the start of the current visit                                                                      | Both     |
| current\_version\_first\_visit | 1655824764174                        | Timestamp of the first visit for this application version                                                        | Both     |
| session\_number                | 1                                    | The number of sessions                                                                                           | Both     |
| first\_visit                   | 1655824764174                        | Timestamp of the first app visit                                                                                 | Both     |
| last\_visit                    | 1655824764174                        | Timestamp of the last visit                                                                                      | Both     |
| last\_call                     | 1655824772416                        | Timestamp of the previous call                                                                                   | Both     |
| last\_session\_start           | 0                                    | Timestamp of the start of the previous session                                                                   | Both     |
| last\_session\_last\_hit       | 0                                    | Timestamp of the last hit sent during the previous session                                                       | Both     |
| foreground\_transitions        | 2                                    | Number of times the app when from background to foreground                                                       | Both     |
| foreground\_time               | 8278                                 | Time the application spent in foreground                                                                         | Both     |
| background\_time               | 0                                    | Time the application spent in background                                                                         | Both     |
| first\_execute                 | false                                | Is this the first hit of this cold launch                                                                        | Both     |
| is\_first\_visit               | true                                 | Is this the first launch of this application. (together with first execute you can validate a new installations) | Both     |
