[![npm version](https://badgen.net/npm/v/vast-client)](https://badgen.net/npm/v/vast-client)
[![downloads per week](https://badgen.net/npm/dw/vast-client)](https://badgen.net/npm/dw/vast-client)
[![license](https://badgen.net/npm/license/vast-client)](https://badgen.net/npm/license/vast-client)

# VAST Client JS

Vast Client JS is a JavaScript library to fetch and parse Digital Video Ad Serving Template (VAST) documents.

This library provides three components:

* A **VAST Client** to fetch and parse VAST XML resources into JavaScript Objects.
* A **VAST Parser** to directly parse a VAST XML.
* A **VAST Tracker** to batch and call tracking URLs.

For the full API documentation go [here](#api).
For the full Class reference go [here](https://github.com/dailymotion/vast-client-js/blob/master/docs/api/class-reference.md)

Complies with the [VAST 4.2 specification](https://iabtechlab.com/wp-content/uploads/2019/06/VAST_4.2_final_june26.pdf) provided by the [Interactive Advertising Bureau (IAB)](https://www.iab.com/).

## Get Started

VAST Client JS is available as an NPM package and can be easily installed with:

```Bash
npm i @dailymotion/vast-client
```

Then import the components you need.

### VASTClient

If you need to fetch and parse VAST documents, you can use the **VASTClient**:

```javascript
import { VASTClient } from '@dailymotion/vast-client'

const vastClient = new VASTClient();

vastClient.get('https://www.examplevast.com/vast.xml')
  .then(res => {
    // Do something with the parsed VAST response
  })
  .catch(err => {
    // Deal with the error
  });
```

In addition to fetching and parsing a VAST resource, **VASTClient** provides options to filter a sequence of calls based on count and time of execution, together with the possibility to track URLs using **VASTTracker**.

### VASTParser

To directly parse a VAST XML you can use the **VASTParser**:

```Javascript
import { VASTParser } from '@dailymotion/vast-client'

const vastParser = new VASTParser();

vastParser.parseVAST(vastXml)
  .then(res => {
    // Do something with the parsed VAST response
  })
  .catch(err => {
    // Deal with the error
  });
```

### VASTTracker

To track the execution of an ad use the **VASTTracker**:

```Javascript
import { VASTTracker } from '@dailymotion/vast-client'

const vastTracker = new VASTTracker(vastClient, ad, creative);

// Track an impression for the given ad
vastTracker.trackImpression();
```

## API Documentation<a name="api"></a>

The API documentation is organized by components:

* [VASTClient](docs/api/vast-client.md)
* [VASTParser](docs/api/vast-parser.md)
* [VASTTracker](docs/api/vast-tracker.md)

**:warning: IMPORTANT :warning:** : the release of the `3.0` version of the library introduced many breaking changes in the API.

Read the [3.0 migration guide](docs/api/3.0-migration.md) to update your project or follow the [2.0 migration guide](docs/api/2.0-migration.md) or [1.x API documentation](docs/api/1.x) if you're still using the old version.

### Pre-bundled versions

We provide several pre-bundled versions of the client (see [`dist` directory](dist/))

#### Bundlers

A version for js bundlers (like webpack or rollup) is available by default when adding the lib using a package manager (like npm or yarn): [`vast-client.js`](dist/vast-client.js) or [`vast-client.min.js`](dist/vast-client.min.js) [minified].

```javascript
const import {
  VASTClient,
  VASTParser,
  VASTTracker
} from '@dailymotion/vast-client'

const vastClient = new VASTClient();
const vastParser = new VASTParser();
const vastTracker = new VASTTracker();
```

#### Browser script

A pre-bundled version of VAST Client JS is available: [`vast-client-browser.min.js`](dist/vast-client-browser.min.js) [minified].

You can add the script directly to your page and access the library's components through the `VAST` object.

```html
<script src="vast-client-browser.min.js"></script>
```

```javascript
const vastClient = new VAST.VASTClient();
const vastParser = new VAST.VASTParser();
const vastTracker = new VAST.VASTTracker();
```

#### Node

A pre-bundled version for node is available too: [`vast-client-node.js`](dist/vast-client-node.js) or [`vast-client-node.min.js`](dist/vast-client-node.min.js) [minified].

```javascript
const VAST = require('@dailymotion/vast-client')

const vastClient = new VAST.VASTClient();
const vastParser = new VAST.VASTParser();
const vastTracker = new VAST.VASTTracker();
```

## Build / Contribute

See [CONTRIBUTING](docs/CONTRIBUTING.md)
