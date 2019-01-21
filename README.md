# BLIINK SSP documentation for DEMAND partners

This guide covers the latest version of the BLIINK Real-time Bidding Protocol. The BLIINK bidding protocol is based on the latest OpenRTB Protocol Specification V2.5.

If you system is not compatible with OpenRTB Protocol Specification V2.5, our system is able downgrader the request version to you version. Please contact our support if you are in this case.

## Request
The invitation to participate in an auction is sent using the POST method in JSON format (Content-Type: application/json) encoded in GZIP (Accept-Encoding: gzip).

### Request Headers
The request header contains the OpenRTB Protocol Version (x-openrtb-version: 2.5).

### Request Body
The request body contains the Bid Request object. Its parameters describe the site, endpoint device, and consumer. These characteristics help the DSP select an ad and a bid.

## Bid Request Model (V2.5)
Bid request model for OpenRTB Protocol 2.5 is shown below.

### Bid Object

This is the top level object that is sent to the Buyer. Each bid request sent from BLIINK to a Buyer will contain the following fields.

| Key | Type | Description |
| --- | ---- | ----------- |
| id | string | Unique ID of the bid request. |
| cur | array of strings | Array of allowed currencies for bids on this bid request using ISO-4217 alpha codes. |
| allimps | integer  | A flag to indicate if the Supplier can verify that the impressions offered represent all of the impressions available in context to support road-blocking. |
| tmax | integer | Maximum time in milliseconds the exchange allows for bids to be received to avoid timeout, including internet latency |
| bcat | array of strings | Blocked Advertiser Categories, using the IAB taxonomy. |
| at | integer | Auction type. |
| device | object | 	Device object with details about the device to which the impression will be delivered, for more information, see the [Device Object](#device-object) section. |
| user | object | User Object which describes the user, for more information, see the [User Object](#user-object) section. |
| source | object | Indicates the entity responsible for the final impression sale decision, for more information, see the [Source Object](#source-object). |
| ext | object | Ext Object used for Supplier specific properties, for more information, see the [Ext Object](#ext-object) section. |
| imp | array of objects | Array of objects representing the impressions offered, for more information, see the [Impression Object](#impression-object) section. |
| site | object | The Site Object describing the site, for more information, see the [Site Object](#site-object) section.  |

#### Device Object

| Key | Type | Description |
| --- | ---- | ----------- |
| js | integer | 1 if the device supports JavaScript; otherwise 0. |
| ip | string | Specifies the IPv4 address closest to the device. |
| geo | object | Geo Object as derived from the device’s location services, or supplied by the Supplier if the device IP is missing. For more information, see the [Geo Object](#geo-object) section. |
| language | string | Alpha-2/ISO 639-1 code of browser language. |
| ua | string | Browser or application user agent string. |
| osv | string | Device operating system version |
| devicetype | integer | Device type as defined by OpenRTB. |
| w | integer | Physical height of the screen in pixels. |
| h | integer | Physical width of the screen in pixels. |
| pxratio | float | The ratio of physical pixels to device independent pixels. |
| ipv6 | string | IP address in IPv6. |

##### Geo Object

| Key | Type | Description |
| --- | ---- | ----------- |
| type | integer | Source of location data as defined by OpenRTB. |
| lat | double | Latitude from -90 to 90. South is negative. |
| lon | double | Longitude from -180 to 180. West is negative. |
| region | string | Region using ISO-3166-2 or FIPS region codes. |
| country | string | Country using ISO-3166-1 Alpha-2. |
| city | string | City name as provided by GeoIP. |
| zip | integer | Zip/postal code. |
| utcoffset | integer | Local time as the number +/- of minutes from UTC. |

#### User Object

| Key | Type | Description |
| --- | ---- | ----------- |
| id | string | Unique BLIINK ID of this user |
| consent | string | The binary encoding scheme that is passed in base64 URL/web safe format known as daisybit. |

#### Source Object

| Key | Type | Description |
| --- | ---- | ----------- |
| fd | integer | Indicates the entity responsible for the final impression sale decision |

#### Ext Object

| Key | Type | Description |
| --- | ---- | ----------- |
| ads_txt.status | integer | Indicates what information the ads.txt file contained regarding this Suppliers selling relationship with the publisher |
| ads_txt.auth_id | string | Passes the TAG ID if present in the ads.txt file |
| ads_txt.pub_id | string | Publisher ID |
| is_secure | integer | 0 for non-secure pages; 1 for secure pages. |
| ssp | string | The Supplier identification string |
| media_src | string | The Supplier identification string |

#### Impression object
```
{ 
  bidfloor: (float),
  bidfloorcur: 'EUR',
  instl: (int),
  exp: (int),
  displaymanager: (string),
  displaymanagerver: (string),
  id: (string),
  tagid: (int),
  banner: {Banner Object},
  pmp: {PrivateMarket Object},
  secure: (int),
}
```

##### Banner Object
```
{
  topframe: (int),
  battr: [(int)],
  btype: [(int)],
  pos: (int),
  mimes: [(string)],
  id: (string),
  h: (int),
  w: (int),
  format: [
    {BannerFormat Object}
  }],
  ext:
    extra_sizes: [{
      h: (int),
      w: (int),
    }],
  }
}
```

###### BannerFormat Object
```
{
  h: (int),
  w: (int)
}
```

##### PrivateMarket Object
```
{
  deals: [
   {Deal Object}
  ],
  private_auction: (int)
}
```

###### Deal Object
```
{
  bidfloorcur: (string),
  id: (string),
  bidfloor: (float),
  at: (int)
}
```

#### Site Object
```
{
  publisher: {Publisher Object},
  domain: (string),
  ref: (string),
  page: (string),
  id: (string),
  name: (string)
}
```

##### Publisher Object

```
{
  domain: (string),
  id: (string),
  name: (string)
}
```
