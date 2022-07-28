# single-line-conclusion-简单小结

## object vs map

- <https://www.zhenghao.io/posts/object-vs-map>
  - 使用 Object 记录固定/有限的 props/fields 的对象，如 config object/一次性使用的 Object
  - 使用 Map 记录有大量实例/频繁更新的场景
  - 通常数据量达到一定量之后，Map 的性能是 Object 的 2 倍；
