Yeah I just use file system to caching file into static folder
and have a "bit" changed the hydrate function:
```javascript
function hydrate(filename_or_path) {
  if((!prebuildHTML["index.langx"] && !fs.existsSync(`/static/${filename_or_path}.html`)) || devMode) {
    console.time("Complie")
    const data = complie(
      parse(filename_or_path + ".waterx"),
      filename_or_path + ".waterx"
    );
    console.timeEnd("Complie")  
    // In Ram complier
    prebuildHTML[filename_or_path + ".waterx"] = data[0];
    prebuildJS[filename_or_path + ".waterx"] = data[1];
    prebuildRunScript[filename_or_path + ".waterx"] = data[2];
    // file type compiler
    // Create directory static if not found
    if(!fs.existsSync("static")) {
      fs.mkdirSync("static");
    }
    fs.writeFileSync("static/" + filename_or_path + ".html", data[0]);
    fs.writeFileSync("static/" + filename_or_path + ".js", data[1]);
    fs.writeFileSync("static/" + filename_or_path + "-pre.html", data[2]);
    // fs.writeFileSync("static/" + filename_or_path + ".js", data[2]);
    return data[2];
  } else {
    console.log(chalk.green("Using cache content"))
    if(!prebuildRunScript[filename_or_path + ".waterx"]) {
      return prebuildRunScript[filename_or_path + ".waterx"] = fs.readFileSync("static/" + filename_or_path + "-pre.html").toString();
    } else {
      return prebuildRunScript[filename_or_path + ".waterx"];
    }
  }
}
```
