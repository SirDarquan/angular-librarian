# Migration Documentation

## Custom Configurations

For all migrations, first, make sure you have no altered any of the following
files:

- `karma.conf.js`
- `tasks/rollup.js`
- `webpack/*`

If you have, it is **highly** suggested that you move whatever customizations
you have done into configuration files per the
[Custom Configurations](README.md#custom-config) section of the `README.md`.

## Upgrading

The best path of migration is to use the built-in upgrade command in
one of the following ways:

```shell
ngl u
ngl up
ngl upgrade
npm run g u
npm run g up
npm run g ugrade
```

After doing that, following the version-specific list of migration steps.

## Migrations

- [< 1.0.0-beta.12 to 1.0.0-beta.12](#1beta12)

### <a id="1beta12"></a>From < 1.0.0-beta.12 to 1.0.0-beta.12

To migrate to this version, manually change the following:

1. Remove files:
    - `tsconfig.build.json`
    - `webpack/webpack.build.json`
2. Remove from `package.json`:
    - `scripts`
        - `build:aot`
        - `build:copy`
        - `build:pack`
        - `pretagVersion`
    - `jsnext:main`
    - `types`
3. Add to `package.json`:
    - `"es2015": "./<package name>.js"`
    - `"module": "./<package name>.es5.js"`
    - `"typings": "./<package name>.d.ts"`
4. Change in `package.json`:
    - `"main": "./<package name>.bundle.js"` to `"main": "./bundles/<package name>.umd.js"`