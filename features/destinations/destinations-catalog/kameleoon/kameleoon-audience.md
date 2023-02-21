# Kameleoon (audience)

[Kameleoon ](https://www.kameleoon.com)is an AI personalization and A/B testing SaaS platform for product managers and marketing teams who want to personalize the customer journey to maximize engagement, conversion and online revenue.

### 1- Audience configuration

Select 1 or many segment(s) you want to export.

Select what kind of data you want to export:

* Users
* Page views
* Conversions
* Products
* Views (only available for Campaign Analytics customers)
* Clicks (only available for Campaign Analytics customers)

Select properties you want to export.

You can add also a static column, meaning you can set a value, and it will be exported as you entered it.

Select the data range:

* All: all stored data corresponding to what you selected
* Pick up where last export left off: differential export, you can export only records which were not exported on the last export
* Last... / Between...: select a precise period for the data range

### 2- Settings

Select the storage connector (a storage connector can be configured on Administration / Connector credentials).

Precise the filename and extension (CSV by default).

Precise if you want to compress the file (GZIP by default).

Precise if you want to include headers at the top of the file.

Precise the main separator and separator inside a variable (ex: value1,value2;value2a;value2b,value3)

### 3- Activation

Define the running frequency for the export (every 10 minutes, day, week...)