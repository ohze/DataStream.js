DataStream.js
=============

### Install
```bash
npm i datastream-js
```
### Usage
```typescript
import DataStream from "datastream-js";

const ds = new DataStream();
ds.writeInt8(3).writeUtf8WithLen("Xin chào");

const ds2 = new DataStream(ds.buffer);
expect(ds2.readStruct([
    'num', 'int8',
    'len', 'uint16',
    'greet', 'string,utf-8:len'])
).to.deep.equal({
    num: 3,
    len: 9, // new TextEncoder('utf-8').encode('Xin chào').length == 9
    greet: "Xin chào"
});

// see other methods in the typescript source code [DataStream.ts]
```

DataStream.js is a library for reading data from ArrayBuffers, see [this HTML5Rocks article](http://www.html5rocks.com/en/tutorials/webgl/typed_arrays/) for documentation.

There is a JPEG marker decoder example in jpeg.html, it prints out JPEG marker contents and uses the jpg.js library to decode the JPEG and draw it on a canvas element.

LICENSE
=======

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
