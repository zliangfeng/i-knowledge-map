如果一个字体源文件比较大，可以采用 css/unicode-range属性切分字体后异步加载
ref: <https://cdnjs.cloudflare.com/ajax/libs/lxgw-wenkai-screen-webfont/1.5.0/lxgwwenkaiscreenr.css>
```css
/* LXGW WenKai Screen R [4] */
@font-face {
  font-family: 'LXGW WenKai Screen R';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url('./files/lxgwwenkaiscreenr-subset-4.woff2') format('woff2');
  unicode-range: U+1f1e9-1f1f5, U+1f1f7-1f1ff, U+1f21a, U+1f232, U+1f234-1f237, U+1f250-1f251, U+1f300, U+1f302-1f308, U+1f30a-1f311, U+1f315, U+1f319-1f320, U+1f324, U+1f327, U+1f32a, U+1f32c-1f32d, U+1f330-1f357, U+1f359-1f37e
}
/* LXGW WenKai Screen R [5] */
@font-face {
  font-family: 'LXGW WenKai Screen R';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url('./files/lxgwwenkaiscreenr-subset-5.woff2') format('woff2');
  unicode-range: U+fee3, U+fef3, U+ff03-ff04, U+ff07, U+ff0a, U+ff17-ff19, U+ff1c-ff1d, U+ff20-ff3a, U+ff3c, U+ff3e-ff5b, U+ff5d, U+ff61-ff65, U+ff67-ff6a, U+ff6c, U+ff6f-ff78, U+ff7a-ff7d, U+ff80-ff84, U+ff86, U+ff89-ff8e, U+ff92, U+ff97-ff9b, U+ff9d-ff9f, U+ffe0-ffe4, U+ffe6, U+ffe9, U+ffeb, U+ffed, U+fffc, U+1f004, U+1f170-1f171, U+1f192-1f195, U+1f198-1f19a, U+1f1e6-1f1e8
}
```