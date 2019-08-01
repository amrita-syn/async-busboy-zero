# Promise Based Multipart Form Parser

Forked from 'async-busboy-plus'
 
### Options other than Busboy
1. tmpdir - Specify a location where the temp files will be stored
2. streamTimeout - Specify how long the temp file handles will exist. Addresses the scenario where a writeStream goes stale. Defualt set to 1 hr. 

The 'zero' because it doesn't leave any temp files or open write streams behind.

## Examples

### Async/Await (using temp files)
```js
import asyncBusboy from 'async-busboy-plus';

// Koa 2 middleware
async function(ctx, next) {
  const {files, fields, complete} = await asyncBusboy(ctx.req, {
    // default to os.tmpdir
    tmpdir: '/tmp',
    streamTimeout: 300000
  });

  // Make some validation on the fields
  if ( checkFiles(fields) ) {
    files.map(/* Do something with each file like uploading to s3 */)
  } else {
    return 'error';
  }
  complete()
}
```
