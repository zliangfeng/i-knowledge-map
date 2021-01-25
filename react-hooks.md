# react-hooks

## useRef
```js
// be used as instance variable to track some kind of state
const isFirstRender = React.useRef(true); // => { current: true }

// dom ref
function ComponentWithDomApi({ label, value, isFocus }) {
  const ref = React.useRef(); // (1)
 
  React.useEffect(() => {
    if (isFocus) {
      ref.current.focus(); // (3) DOM Object.
      // const { width } = ref.current.getBoundingClientRect();
    }
  }, [isFocus]);
 
  return (
    <label>
      {/* (2) */}
      {label}: <input type="text" value={value} ref={ref} />
    </label>
  );
}
// With a callback ref, you don't have to use useEffect and useRef hooks anymore
function ComponentWithRefRead() {
  const [text, setText] = React.useState('Some text ...');
 
  function handleOnChange(event) {
    setText(event.target.value);
  }
 
  const ref = (node) => {
    if (!node) return;
 
    const { width } = node.getBoundingClientRect();
 
    document.title = `Width:${width}`;
  };

  const refOnlyRunForTheFirstRender = React.useCallback((node) => {
    if (!node) return;
 
    const { width } = node.getBoundingClientRect();
 
    document.title = `Width:${width}`;
  }, []);
 
  return (
    <div>
      <input type="text" value={text} onChange={handleOnChange} />
      <div>
        <span ref={ref}>{text}</span>
      </div>
    </div>
  );
}

```