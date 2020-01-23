# Web

Use either one of the following methods will do.

### 1. Embedly

Use the following URL for Embedly
```
https://button.like.co/{{LikerID}}
```

### 2.`<iframe>`

#### 2.1 Construct an embedded URL according to the following format:

```
https://button.like.co/in/embed/{{LikerID}}/button?referrer={{referrer}}&type={{type}}
```

| Parameter    | Type       | Required?  | Description                                     |
| -------------|------------|------------|-------------------------------------------------|
| `LikerID`    | `string`   | required   | The author of the content |
| `referrer`   | `string`   | required   | The source (canonical) URL of the content in `encodeURIComponent()` format (this also works as the content key) |
| `type`       | `string`   | optional   | `wp` for WordPress site, omit for the others|

> For testing purpose, you may use `button.rinkeby.like.co` instead of `button.like.co`

> In case of iframe sandbox, `allow-scripts`, `allow-same-origin`, `allow-popups` `allow-popups-to-escape-sandbox`, `allow-top-navigation-by-user-activation`, `allow-storage-access-by-user-activation` are needed for proper register/login functionality.

#### 2.2 Embed the [sample HTML](index.html) and replace `{{ src }}` with the embed URL into your HTML

#### 2.3 Include the [CSS code](style.css)
#### 2.4 (Optional) Update referrer via [postMessage](postMessage.html)
The LikeCoin button `<iframe>`'s src (especially the `referrer` param) should be updated to when the URL is changed. In case updating `<iframe>`'s src is not possible (e.g. for some SPA usecases), you may call `postMessage()` to the `<iframe>` with following payload to update the `referrer`.
```javascript
{
  action: 'SET_REFERRER',
  content: { referrer: `${ newReferrer||window.location.href }` }
}, 'https://button.like.co'
```
