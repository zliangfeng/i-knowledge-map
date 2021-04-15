# grid

## Refs

## content

`multiple colomns/rows`

```css
.grid {
  display: grid;
  grid-template-colomns: 1fr 500px 1fr;
  grid-template-rows: 100px 200px;
  place-items: center;
}
```

effect

```text
+-------+----------------+-------+
|       |                |       |
|     100px              |       |
|       |                |       |
+-1fr-------500px-----------1fr--+
|       |                |       |
|       |                |       |
|       |                |       |
|     500px              |       |
|       |                |       |
|       |                |       |
+-------+----------------+-------+

```
