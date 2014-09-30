Working with Node.js Packages 
=============================

One of the most powerful features of the Node.js framework is the ability to easily extend it with additional Node Packaged Modules (NPMs).

A Node Packaged Module is a packaged library that can easily be shared, reused, and installed in different projects. There are many different modules available for a variety of purposes.

Node.js modules are created by various third-party organizations to provide important features that Node.js lacks out of the box.

Package.json
------------

Each Node Packaged Module includes a package.json file that defines the packages. The package.json file includes informational metadata such as the name, version, author, and contributors, as well as control metadata such as dependencies and other requirements that the Node Package Manager will use when performing actions such as installation and publishing.

##### Package.json
```
{ 
   "name": "my_module", 
   "version": "0.1.0", 
   "description": "a simple node.js module", 
   "dependencies" : { 
   		"express" : "latest" 
   	} 
}

```

##### Dependecies and devDependecies hash

Dependencies are specified with a simple hash of package name to version range. The version range is a string which has one or more space-separated descriptors. Dependencies can also be identified with a tarball or git URL.

   - version Must match version exactly
   - \>version Must be greater than version
   - \>=version etc
   - <version
   - <=version
   - ~version "Approximately equivalent to version" See semver(7)
   - ^version "Compatible with version" See semver(7)
   - 1.2.x 1.2.0, 1.2.1, etc., but not 1.3.0
   - http://... See 'URLs as Dependencies' below
   - \* Matches any version
   - "" (just an empty string) Same as *
   - version1 - version2 Same as >=version1 <=version2.
   - range1 || range2 Passes if either range1 or range2 are satisfied.
   - git... See 'Git URLs as Dependencies' below
   - user/repo See 'GitHub URLs' below
   - path/path/path See Local Paths below 

```

{ "dependencies" :
  { "foo" : "1.0.0 - 2.9999.9999"
  , "bar" : ">=1.0.2 <2.1.2"
  , "baz" : ">1.0.2 <=2.3.4"
  , "boo" : "2.0.1"
  , "qux" : "<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0"
  , "asd" : "http://asdf.com/asdf.tar.gz"
  , "til" : "~1.2"
  , "elf" : "~1.2.3"
  , "two" : "2.x"
  , "thr" : "3.3.x"
  , "lat" : "latest"
  , "dyl" : "~/projects/dyl"
  }
}

```

If someone is planning on downloading and using your module in their program, then they probably don't want or need to download and build the external test or documentation framework that you use.

In this case, it's best to list these additional items in a devDependencies hash.

```

{ "name": "ethopia-waza",
  "description": "a delightfully fruity coffee varietal",
  "version": "1.2.3",
  "devDependencies": {
    "coffee-script": "~1.6.3"
  },
  "scripts": {
    "prepublish": "coffee -o lib/ -c src/waza.coffee"
  },
  "main": "lib/waza.js"
}

```

To view the full [package.json specification].

One of the things I love about the Node modules is that there is a managed location called the Node Package Registry where packages are registered. The registry allows you to publish your own packages in a location where others can use them as well as download packages that others have created. The Node Package Registry is located at http:// npmjs.org . From this location, you can view the newest and most popular modules as well as search for specific packages.

##### Command-line options 

| Options   	| Description  									| Example               |
|---------------|-----------------------------------------------|-----------------------|
| search      	| Finds module packages in the repository       | npm search express    |
| install    	| Installs a package either using a package.json file from the repository or from a local location          | npm install , npm install express , npm install express@0.1.1 , npm install ../Module.tgz         |
| install -g  	| Installs a package in a globally accessible   | npm install express -g|
| remove		| Removes module  								| npm remove express 	|






[package.json specification]:https://www.npmjs.org/doc/files/package.json.html

