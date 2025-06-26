# About This Parser

This parser is designed to help FortiSIEM interpret and extract meaningful fields from OCPP (Open Charge Point Protocol) log messages observed on FortiGate firewalls in EVCS (Electric Vehicle Charging Station) environments.

The parser logic specifically targets OCPP messages that pass through the FortiGate and are logged via UTM application control logs. By extracting key elements like idTag, connectorId, status, or errorCode from the payload, this parser enables better visibility and use-case mapping inside FortiSIEM.

You can find the relevant parser logic between the tags:

```<!--EVCS System Parser-->```

...


```<!--EVCS System Parser-->```


This section includes condition-based regex extraction rules applied to the $fileName field, which typically contains the OCPP payload. It is modular and can be extended further based on your specific needs or to support additional OCPP operations.



**Test Events for FortiSIEM - FortiOS-EVCS Parser**

Adding a Test Event is a mandatory step when uploading a new parser to FortiSIEM. You can use the following sample events to test and validate the FortiOS-EVCS parser.

These logs reflect typical OCPP operations observed in EVCS environments and are compatible with the current parser setup. We recommend including them in the test section of your parser definition. 



**Test Event 1: OCPP Authorize Request**

<190>date=2025-06-26 time=17:00:09 devname="EVCS-FGT" devid="FGXXXXXXXXXXXXX" eventtime=1750946409105229609 tz="+0300" logid="1059028704" type="utm" subtype="app-ctrl" eventtype="signature" level="information" vd="root" appid=52334 srcip=10.0.10.12 srccountry="Reserved" dstip=10.0.20.10 dstcountry="Reserved" srcport=53532 dstport=8180 srcintf="vlan10" srcintfrole="lan" dstintf="IPSEC1" dstintfrole="undefined" proto=6 service="tcp/8180" direction="outgoing" policyid=1 poluuid="79a91dc8-285a-51f0-4cb4-6fad2ac8b80a" policytype="policy" sessionid=76503 applist="AC-all" action="pass" appcat="Operational.Technology" app="OCPP_Authorize" hostname="10.0.20.10" incidentserialno=203593557 msg="Operational.Technology: OCPP_Authorize" clouduser="10.0.10.12" filename="[2,\"1142054\",\"Authorize\",{\"idTag\":\"tagid002\"}]" apprisk="elevated"

**Test Event 2: OCPP StartTransaction Request**

<190>date=2025-06-26 time=17:00:58 devname="EVCS-FGT" devid="FGXXXXXXXXXXXXX" eventtime=1750946457648432203 tz="+0300" logid="1059028704" type="utm" subtype="app-ctrl" eventtype="signature" level="information" vd="root" appid=52398 srcip=10.0.10.12 srccountry="Reserved" dstip=10.0.20.10 dstcountry="Reserved" srcport=53532 dstport=8180 srcintf="vlan10" srcintfrole="lan" dstintf="IPSEC1" dstintfrole="undefined" proto=6 service="tcp/8180" direction="outgoing" policyid=1 poluuid="79a91dc8-285a-51f0-4cb4-6fad2ac8b80a" policytype="policy" sessionid=76503 applist="AC-all" action="pass" appcat="Operational.Technology" app="OCPP_Start.Transaction" hostname="10.0.20.10" incidentserialno=203593590 msg="Operational.Technology: OCPP_Start.Transaction" clouduser="10.0.10.12" filename="[2,\"1142075\",\"StartTransaction\",{\"connectorId\":1,\"idTag\":\"tagid004\",\"meterStart\":328034,\"timestamp\":\"2025-06-26T14:00:57.483Z\"}]" apprisk="elevated"

**Test Event 3: OCPP StopTransaction Request**

<190>date=2025-06-26 time=17:01:56 devname="EVCS-FGT" devid="FGXXXXXXXXXXXXX" eventtime=1750946515730257781 tz="+0300" logid="1059028704" type="utm" subtype="app-ctrl" eventtype="signature" level="information" vd="root" appid=52400 srcip=10.0.10.11 srccountry="Reserved" dstip=10.0.20.10 dstcountry="Reserved" srcport=53530 dstport=8180 srcintf="vlan10" srcintfrole="lan" dstintf="IPSEC1" dstintfrole="undefined" proto=6 service="tcp/8180" direction="outgoing" policyid=1 poluuid="79a91dc8-285a-51f0-4cb4-6fad2ac8b80a" policytype="policy" sessionid=76502 applist="AC-all" action="pass" appcat="Operational.Technology" app="OCPP_Stop.Transaction" hostname="10.0.20.10" incidentserialno=203593627 msg="Operational.Technology: OCPP_Stop.Transaction" clouduser="10.0.10.11" filename="[2,\"1085790\",\"StopTransaction\",{\"meterStop\":314394,\"timestamp\":\"2025-06-26T14:01:55.661Z\",\"transactionId\":52533,\"reason\":\"EVDisconnected\"}]" apprisk="elevated"
