# api documentation for  [highlight (v0.2.4)](https://github.com/andris9/highlight#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-highlight.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-highlight) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-highlight.svg)](https://travis-ci.org/npmdoc/node-npmdoc-highlight)
#### Highlight code syntax with node.js

[![NPM](https://nodei.co/npm/highlight.png?downloads=true)](https://www.npmjs.com/package/highlight)

[![apidoc](https://npmdoc.github.io/node-npmdoc-highlight/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-highlight_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-highlight/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-highlight/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-highlight/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Andris Reinman"
    },
    "bugs": {
        "url": "https://github.com/andris9/highlight/issues"
    },
    "dependencies": {},
    "deprecated": "Not maintained anymore",
    "description": "Highlight code syntax with node.js",
    "devDependencies": {},
    "directories": {
        "lib": "./lib"
    },
    "dist": {
        "shasum": "8ac02875b03f5935e0675852b76cfe1fd58e0dff",
        "tarball": "https://registry.npmjs.org/highlight/-/highlight-0.2.4.tgz"
    },
    "gitHead": "a955fd043e73a5d304e0987515641f1075bb88b2",
    "homepage": "https://github.com/andris9/highlight#readme",
    "licenses": [
        {
            "type": "BSD",
            "url": "http://github.com/andris9/highlight/blob/master/LICENSE"
        }
    ],
    "main": "./lib/highlight",
    "maintainers": [
        {
            "name": "andris",
            "email": "andris@node.ee"
        },
        {
            "name": "guileen",
            "email": "guileen@gmail.com"
        }
    ],
    "name": "highlight",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/andris9/highlight.git"
    },
    "scripts": {},
    "version": "0.2.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module highlight](#apidoc.module.highlight)
1.  [function <span class="apidocSignatureSpan"></span>highlight (text, tabReplace, useCodeBlocks)](#apidoc.element.highlight.highlight)
1.  [function <span class="apidocSignatureSpan">highlight.</span>Highlight ()](#apidoc.element.highlight.Highlight)
1.  [function <span class="apidocSignatureSpan">highlight.</span>init (cb, langs, opts)](#apidoc.element.highlight.init)
1.  object <span class="apidocSignatureSpan">highlight.</span>languages
1.  object <span class="apidocSignatureSpan">highlight.</span>loadedLanguages



# <a name="apidoc.module.highlight"></a>[module highlight](#apidoc.module.highlight)

#### <a name="apidoc.element.highlight.highlight"></a>[function <span class="apidocSignatureSpan"></span>highlight (text, tabReplace, useCodeBlocks)](#apidoc.element.highlight.highlight)
- description and source-code
```javascript
function highlight(text, tabReplace, useCodeBlocks){
  tabReplace = tabReplace || '    ';
  text = text.replace(/\r\n|\r|\n/g, '\n'); // remove \r
  if (!!useCodeBlocks) {
    // JS regexpes have some multiline issues, so we temporarily remove them
    return text
      .replace(/\n/g,'\uffff')
      .replace(/<code([^>]*)>(.*?)<\/code>/gm, function(original, attrs, source){
        return '<code'+attrs+'>'+hljs.highlightText(source.replace(/\uffff/g,"\n"), tabReplace)+'</code>';
      })
      .replace(/&amp;(\w+;)/g,'&$1').replace(/\uffff/g,"\n");
  } else {
    return hljs.highlightText(text, tabReplace);
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.highlight.Highlight"></a>[function <span class="apidocSignatureSpan">highlight.</span>Highlight ()](#apidoc.element.highlight.Highlight)
- description and source-code
```javascript
function backwardsCompat() {
  // currently synchronous
  Highlight.init(function () {}, ['php']);
  return Highlight.highlight.apply(null, arguments);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.highlight.init"></a>[function <span class="apidocSignatureSpan">highlight.</span>init (cb, langs, opts)](#apidoc.element.highlight.init)
- description and source-code
```javascript
function init(cb, langs, opts) {
  if (!Array.isArray(langs)) {
    langs = Highlight.languages.slice();
  }

  loadLangs(cb, langs);
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
