```javascript
const raw = $json["textPlain"] || "";

// UTF-8 decoding function for misinterpreted characters
function fixEncoding(str) {
  const buffer = Buffer.from(str, 'binary'); // force raw binary interpretation
  return buffer.toString('utf8');            // then decode properly into UTF-8
}

// Final cleaning (line breaks + extra spaces)
const cleaned = fixEncoding(raw)
  .replace(/\r?\n/g, ' ')      // remove line breaks
  .replace(/\s{2,}/g, ' ')     // remove double spaces
  .trim();

return [{
  json: {
    message: cleaned
  }
}];
```