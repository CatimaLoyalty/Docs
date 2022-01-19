# Card sharing URL format

In the interest of interoperability, this page documents the URLs generated when sharing a card.

URLs have the following parts:
## hostname and path

Hostname and path must be any of the following combinations:

| Hostname                 | Path                       | Description                                                            |
| ------------------------ | -------------------------- | ---------------------------------------------------------------------- |
| catima.app               | /share                     | Default since 2021-07-11                                               |
| thelastproject.github.io | /Catima/share              | Created when forking away from Loyalty Card Keychain                   |
| brarcher.github.io       | /loyalty-card-locker/share | For compatibility with https://github.com/brarcher/loyalty-card-locker |

## parameters
The following parameters are supported:

| Key  | Required | Valid values | Explanation |
| ---- | -------- | ------------ | ----------- |
| store | Yes | Any string | Name of the store this card belongs to |
| note | Yes | Any string | An optional note for the end-user |
| cardid | Yes | Any string | The loyalty card ID |
| barcodeid | No | Any string | The value of the loyalty card barcode, if different from the loyalty card ID |
| barcodetype | No | AZTEC, CODABAR, CODE_39, CODE_93, CODE_128, DATA_MATRIX, EAN_8, EAN_13, ITF, MAXICODE, PDF_417, QR_CODE, RSS_14, RSS_EXPANDED, UPC_A, UPC_E | The type of loyalty card barcode used |
| balance | No | Any string value accepted by Java's BigDecimal constructor | The balance available in the loyalty card |
| balancetype | No | Any valid ISO 4217 value or unset for "Points" | The balance currency (USD, EUR, etc.) or "points" |
| expiry | No | Any UNIX timestamp | When the loyalty card expires |
| headercolor | No | A valid Android color value (https://developer.android.com/reference/android/graphics/Color) | The color to use in the header and card background |

## Catima 2.0

As of Catima 2.0, Share URLs are in the following format for increased privacy (no leaking card info to the server):

```
https://[hostname]/[path]#[parameters]
```

Parameters are written as such before being url-encoded (so yes, the values are url-encoded twice)
```
key=urlencoded_value&key2=urlencoded_value2
```

An example share URL is as follows:
```
https://catima.app/share#store%3DGrocery%2BStore%26note%3DQuite%2Bnecessary%26balance%3D150%26cardid%3Ddhd%26barcodetype%3DAZTEC%26headercolor%3D-9977996
```

## Before 2.0

Share URLs are in the following format:
```
https://[hostname]/[path]?[parameters]
```

An example share URL is as follows:
```
https://catima.app/share?store=Grocery%20Store&note=Quite%20necessary&balance=150&cardid=dhd&barcodetype=AZTEC&headercolor=-9977996
```

These are still imported for backwards compatibility, but no longer generated.
