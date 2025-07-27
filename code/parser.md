```js
return items.map(item => { 
  const texteNettoye = item.json.output.replace(/【[^【】]*?†[^【】]*?】/g, '');
  return {
    json: {
      ...item.json,
      output: texteNettoye
    }
  };
});
```
