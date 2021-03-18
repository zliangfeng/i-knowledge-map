# IntersectionObserver

## Refs

- <https://codepen.io/bramus/pen/ExaEqMJ>
- <https://css-tricks.com/table-of-contents-with-intersectionobserver/>

## Content

```ts
interface Options {
  root: null | DOMElement,
  rootMargin: string,
  threshold: Array<number> | number,
}
let options: Options = {
  // 指定根(root)元素，用于检查目标的可见性。必须是目标元素的父级元素。如果未指定或者为null，则默认为浏览器视窗
  root: document.querySelector("#scrollArea"),
  // 根(root)元素的外边距
  rootMargin: "0px",
  // target元素和root元素相交程度达到该值的时候IntersectionObserver注册的回调函数将会被执行
  // 默认值是0(意味着只要有一个target像素出现在root元素中，回调函数将会被执行)。该值为1.0含义是当target完全出现在root元素中时候 回调才会被执行。
  threshold: 1.0,
};
let observer = new IntersectionObserver(callback, options);
// example: Table of Contents with IntersectionObserver
// NOTE: IntersectionObserver 已有很多浏览器支持了，但还在草案中
window.addEventListener("DOMContentLoaded", () => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      const id = entry.target.getAttribute("id");
      if (entry.intersectionRatio > 0) {
        document
          .querySelector(`nav li a[href="#${id}"]`)
          .parentElement.classList.add("active");
      } else {
        document
          .querySelector(`nav li a[href="#${id}"]`)
          .parentElement.classList.remove("active");
      }
    });
  });

  // Track all sections that have an `id` applied
  document.querySelectorAll("section[id]").forEach((section) => {
    observer.observe(section);
  });
});
```
