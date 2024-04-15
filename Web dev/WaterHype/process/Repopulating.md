#normal
# Client side population process

- Damn it easy as this:
```javascript
	function hydrate(filename_or_path) {
	
		const data = complie(parse("index.waterx"), "index.waterx")
	
		// if(!prebuildHTML["index.langx"]) {
	
		prebuildHTML["index.waterx"] = data[0]
	
		prebuildJS["index.waterx"] = data[1]
	
		// }
	
		const js = data[2]
	
	  
	
		return js
	
	}
```

# Will me more