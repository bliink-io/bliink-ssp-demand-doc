# BLIINK SSP documentation for DEMAND partners

The invitation to participate in an auction is sent using the POST method in JSON format (Content-Type: application/json) encoded in GZIP (Accept-Encoding: gzip).

The request header contains the OpenRTB Protocol Version (x-openrtb-version: 2.5).

The request body contains the Bid Request object. Its parameters describe the site, endpoint device, and consumer. These characteristics help the DSP select an ad and a bid.

Bid request model for OpenRTB Protocol 2.5 is shown below.

## Bid Request Model for OpenRTB Protocol 2.5
```
{   
  /* obj:Bid Request object */
  id: (string),
  cur: [(string)],
  allimps: (int),
  tmax: (int),
  bcat: [(string)],
  at: (int),
  device: {
    /* obj:Device object */
    js: (int),
    ip: (string),
    geo: {
      /* obj:Geo object */
      type: (int),
      lat: (double),
      lon: (double),
      region: (string),
      country: (string),
      city: (string),
      zip: (int),
      utcoffset: (int),
    },
    language: (string),
    ua: (string),
    osv: (string),
    devicetype: (int),
    w: (int),
    h: (int),
    pxratio: (float),
    ipv6: (string),
  },
  user: {
    /* obj:User object */
    id: (string),
  },
  source: {
    /* obj:Source object */
    fd: 1,
  },
  ext: {
    /* obj:Ext object */
    ads_txt: {
      status: (int),
      auth_id: (string),
      pub_id: (string),
    },
    is_secure: (int),
    ssp: (string),
    media_src: (string),
  },
  imp: [{ 
    /* obj:Impression object */
    bidfloor: (float),
    bidfloorcur: 'EUR',
    instl: (int),
    exp: (int),
    displaymanager: (string),
    displaymanagerver: (string),
    id: (string),
    tagid: (int),
    banner: {
      /* obj:Banner object */
      topframe: (int),
      battr: [(int)],
      btype: [(int)],
      pos: (int),
      mimes: [(string)],
      id: (string),
      h: (int),
      w: (int),
      format: [{
        /* obj:Banner object */
        h: (int),
        w: (int),
      }],
      ext: {
        /* obj:BannerExt object */
        extra_sizes: [{
          h: (int),
          w: (int),
        }],
      },
    },
    pmp: {
      /* obj:PrivateMarket object */
      deals: [{
        /* obj:Deal object */
        bidfloorcur: (string),
        id: (string),
        bidfloor: (float),
        at: (int),
      }],
      private_auction: (int),
    },
    secure: (int),
  }],
  site: {
    /* obj:Site object */
    publisher: {
      /* obj:Publisher object */
      domain: (string),
      id: (string),
      name: (string),
    },
    domain: (string),
    ref: (string),
    page: (string),
    id: (string),
    name: (string),
  },
}
```

