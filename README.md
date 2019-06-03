# Promise Based Multipart Form Parser

forked from 'async-busboy', add complete method to delete tmpfile

## Examples

### Async/Await (using temp files)
```js
import asyncBusboy from 'async-busboy-plus';

// Koa 2 middleware
async function(ctx, next) {
  const {files, fields, complete} = await asyncBusboy(ctx.req);

  // Make some validation on the fields before upload to S3
  if ( checkFiles(fields) ) {
    files.map(uploadFilesToS3)
  } else {
    return 'error';
  }
  complete()
}
```
