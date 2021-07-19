# html tips

## refs

- <https://markodenic.com/html-tips/>

## content

- loading=lazy

```html
<img src="image.jpg" loading="lazy" alt="Alternative Text" />
```

- Email, call, and SMS links

```html
<a href="mailto:{email}?subject={subject}&body={content}"> Send us an email </a>

<a href="tel:{phone}"> Call us </a>

<a href="sms:{phone}?body={content}"> Send us a message </a>
```

- Favicon cache busting

```html
<link rel="icon" href="/favicon.ico?v=2" />
```

- `download` attribute

```html
<a href='path/to/file' download>
  Download
</a>           
```
