---
notion-id: 297982ca-e761-8081-9134-e6753ee1fa45
---
## Fundamentals and environment

LibreTranslate

- the API that can be used to detect AND translate text from different languages

How to handle timeouts and handle errors

- wrap POST request code in a try-except block to handle potential errors
- multiple sessions:
    - use timeout parameter of requests
    - post() sets a max wait time for server response

API (application programming interface)

- set of rules that lets one program talk to another

Environment variable

- a name/value pair stored in the OS rather than within the application
- can be read at runtime though

[GitHub streak code](https://chatgpt.com/s/t_68fc4a951fd481919a1a8b309665b05f)

LibreTranslate request shape

Example of “hello vro” from english to arabic

```javascript
const res = await fetch("https://libretranslate.com/translate", {
	method: "POST",
	body: JSON.stringify({
		q: "hello vro",
		source: "auto",
		target: "ar",
		format: "text",
		alternatives: 3,
		api_key: ""
	}),
	headers: { "Content-Type": "application/json" }
});

console.log(await res.json());
```

## Behavioural design (what my shi must do)

Define public functions that will be exposed

- `detect_language_(text) -> (lang_code, confidence)` 
- `translate(text, source, target) -> (translated_text, metadata)`
- `back_translate(original_text, styled_english) -> (back_translated_text, metadata)`

Metadata keys that will be returned

`cached` - bool

`error` - str (optional)

`source_detected`

`latency_ms`


Failure policies

On transient (temporary) network error??

Timeouts

Caching policy

TTL (time to live)

LRU (least recently used) eviction when capacity exceeded

## HTTP requests

### What they contain

Methods

- GET (retrieve data)
- POST (submit data)
- PUT (update data)
- DELETE (remove data)

URL

Headers (metadata)

Body (actual data being sent)

## HTTP responses


## Future Optimisations

- [ ] Limit the length of input
- [x] Limit the length of output (through prompting)
- [ ] Embed the user’s input
- [ ] Streaming the tokens (as tokens are generated) - bitstream
- [ ] SH file
- [ ] duplication

ollama serve &

python backend.py

streamlit 

