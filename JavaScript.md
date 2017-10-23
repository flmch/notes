

[TOC]

# JavaScript

## Manipulation

- read csv file
1. use module: read-line (async)
    ```js
    lineReader.eachLine('filename.csv', function(line, last){
    	console.log(line);
    })
    ```
2. use module: csv (async)
    ```js
    var stream = fs.createReadStream("集奥接口.csv");
     
    csv
     .fromStream(stream)
     .on("data", function(data){
         console.log(data);
         console.log(data.length);
     })
     .on("end", function(){
         console.log("done");
     });
    ```
3. use module: read-line-sync (sync)
    ```js
    lineReader.eachLine('filename.csv', function(line, last){
    	console.log(line);
    })

    LineReaderSync = require("line-reader-sync")
    lrs = new LineReaderSync("filename.csv")
    while(true){
      var line = lrs.readline()
      if(line === null){
        console.log("EOF");
        break;
      }else{
        console.log("line without \n",line)
      }
    }
    //or 
    console.log(lrs.toLines())
    ```

