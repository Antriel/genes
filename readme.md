# genes

[![CI](https://github.com/benmerckx/genes/workflows/CI/badge.svg)](https://github.com/benmerckx/genes/actions)

Generates split ES6 modules and Typescript definitions from Haxe modules.

Requires Haxe 4, status: experimental

## Usage

````
lix +lib genes
````

Install the library and add `-lib genes` to your hxml.


### Defines

- `-D dts` to generate Typescript definition files
- `-debug` or `-D js-source-map` to generate source maps
- `-D genes.extern_init_warning` display a warning wherever an extern `__init__` 
  is used as these are not generated by genes
- `-D genes.disable` disable genes completely (eg. to compare results to default
  haxe js generator)


## Dynamic imports

```haxe
import genes.Genes.dynamicImport;
import my.module.MyClass;
// ...
dynamicImport(MyClass -> new MyClass()).then(trace);
```

Translates to:

```js
import('./my/module/MyClass')
  .then(({MyClass}) => new MyClass())
  .then(console.log)
```

## Alternatives

- Split output with require calls: [hxgenjs](https://github.com/kevinresol/hxgenjs)
- Typescript definition generation: [hxtsdgen](https://github.com/nadako/hxtsdgen)
