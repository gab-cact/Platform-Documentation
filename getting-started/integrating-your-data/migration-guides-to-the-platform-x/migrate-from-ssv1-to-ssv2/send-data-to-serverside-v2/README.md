# Send data to serverside v2

## 1. New concepts

On the new platform (aka Platform X), everything is Source/Event/Destination.\
\
[Sources](./#source) (your website, app or server) collect your user actions by sending [events](./#event).\
These events are sent to the platform servers and are then enriched, normalized and translated in each tool ([Destination](./#destinations)) format, so that they can be sent to your chosen destinations.\
\
You can learn more in the [Concepts ](../../../../../features/integrations/concepts.md)section.

## 2.How to send events (standard / custom)

* From a **server**, use our [HTTP tracking API](../../../../../features/integrations/sources/sources-catalog/http-tracking-api.md).\
  Your data has to be sent to a [new url](../../../../../features/integrations/sources/sources-catalog/http-tracking-api.md#track), following a [new format](./#3.-format-events).
* From a **mobile application**, you can either use one of our SDK ([Android](../../../../../features/integrations/sources/sources-catalog/android.md), [IOS](../../../../../features/integrations/sources/sources-catalog/ios.md), ...) or use our  [HTTP tracking API](https://community.commandersact.com/platform-x/features/integrations/sources/sources-catalog/http-tracking-api) if you don't want to use a SDK.

## 3. Format events

* As explain in the [event documentation](../../../../../developers/tracking/about-events/), common events have to be sent in the **standard format** (name and properties) to benefit from plug\&play features.\
  \
  For specific events, **custom events** name is possible. Nevertheless, please use **standard properties** in custom events, as far as possible, to benefit from automatic mapping, automatic QA, and plug\&play features.
* Standard event format can be found in our [event reference documentation](https://community.commandersact.com/platform-x/developers/tracking/events-reference)\
  Here is an [example ](purchase-event-example-ssv1-to-ssv2.md)based the ssv1 format :  [purchase event example](purchase-event-example-ssv1-to-ssv2.md)