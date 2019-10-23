# Repro for issue
Issue: https://github.com/nuxt/nuxt.js/issues/5800

- Deployed here https://repro-v-if-bug-85xpxq7h9.now.sh
- Can also send and id parameter to deployment: https://repro-v-if-bug-85xpxq7h9.now.sh/?id=ok
- CodeSandbox https://codesandbox.io/s/github/iiAku/repro-v-if-bug

While running yarn dev, I did have the v-node mismatch but it can also disapear from time to time. While being generated through yarn generate and deployed from that you are getting a DOMException. This is heavily link with the fact that it has multiple v-if/v-else logic and nested v-if from vue.js.


# repro-v-if-bug

> My epic Nuxt.js project

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
