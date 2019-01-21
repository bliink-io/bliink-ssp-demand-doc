# BLIINK SSP documentation for DEMAND partners

## Request
The invitation to participate in an auction is sent using the POST method in JSON format (Content-Type: application/json) encoded in GZIP (Accept-Encoding: gzip).

### Request Headers
The request header contains the OpenRTB Protocol Version (x-openrtb-version: 2.5).

### Request Body
The request body contains the Bid Request object. Its parameters describe the site, endpoint device, and consumer. These characteristics help the DSP select an ad and a bid.

## Bid Request Model
Bid request model for OpenRTB Protocol 2.5 is shown below.

### Bid Object
```
{
  id: (string),
  cur: [(string)],
  allimps: (int),
  tmax: (int),
  bcat: [(string)],
  at: (int),
  device: {Device Object}
  user: {User Object}
  source: {Source Object}
  ext: {Ext Object},
  imp: [
    {Impression Object}
  ],
  site: {Site Object}
}
```

#### Device Object
```
{
  js: (int),
  ip: (string),
  geo: {Geo Object},
  language: (string),
  ua: (string),
  osv: (string),
  devicetype: (int),
  w: (int),
  h: (int),
  pxratio: (float),
  ipv6: (string)
}
```

##### Geo Object
```
{
  type: (int),
  lat: (double),
  lon: (double),
  region: (string),
  country: (string),
  city: (string),
  zip: (int),
  utcoffset: (int),
}
```

#### User Object
```
{
  id: (string),
  ext: {
    consent: (string)
  }
}
```

#### Source Object
```
{
  fd: 1
}
```

#### Ext Object
```
{
  ads_txt: {
    status: (int),
    auth_id: (string),
    pub_id: (string),
  },
  is_secure: (int),
  ssp: (string),
  media_src: (string)
}
```

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
