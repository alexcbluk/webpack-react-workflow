## Installation
```
npm install webpack -g
npm install webpack-dev-server -g
npm install karma-cli -g
npm install
```

## Workflow
1. Run webpack-dev-server on port 5000. This will watch your files and reload the page when it detects any change.
>```
>webpack-dev-server --port 5000 --inline
>```  

2. Run a http server on port 5001 (you could use [http-server](https://www.npmjs.com/package/http-server)). This represents your back-end application (e.g. Rails).
>```
>http-server -p 5001
>```

3. Open http://localhost:5001 on your browser.

4. Make changes (you should see changes being applied simultaneously on the browser). 

5. Once finished changing files, run webpack to compile the bundle(s) into the filesystem.
>```
>npm run build
>```

## Unit tests and code coverage
```
npm test
```

### Code coverage
We use [Istanbul](http://istanbul-js.org/) for unit test code coverage reports.
But because Istanbul does not currently understand the ECMAScript 6 syntax, we
use a tool bridging these two technologies called [Isparta](https://github.com/douglasduteil/isparta).
This extension allows us to generate reports for the actual ES6 source, not the
ES5-compatible code "transpiled" by [Babel](http://babeljs.io).

The actual integration of Isparta with the [Karma](http://karma-runner.github.io/0.13/index.html)
tests runner is done via a [Webpack](http://webpack.github.io) pre-loader. We
have opted for a pre-loader instead of a loaded to clearly separate the coverage
generation from other actions that involve various source code transformations.
This is 100% arbitrary and the coverage reporter might as well be included in
the subsequent loaders step.

### Running results on command line
As we have now introduced a React component that depends on the DOM's
`document` object, you won't be able to run the application directly
from command line (at least in the current configuration).

## Clean project
```
npm run clean
```
