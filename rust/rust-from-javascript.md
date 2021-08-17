# rust from javascript

## Refs

- <https://blogs.harvard.edu/kapolos/rust-from-a-javascript-perspective/>

## Content

```rust
fn main() {
  let a:String = String::from("aaa");
  {
    dbg!(a.clone()); // 避免 a 被 rust drop 掉；
  }
  dbg!(a);
}
```
