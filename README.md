# strawstairies-web
A website for the strawstaries!

<https://poe.dieterbrehm.com/>

## Building Notes

### Build and running commands
Before you can build or run anything, you need the dependencies:

``` bash
npm install
```

In order to build the site, run:

``` bash
npm run build
```

In order to start a development server (with hot reloading!):

``` bash
npm run dev
```

### The POE website server
When deploying on the POE web server, you need to change the `base` property in
the `config.js` file to read `base: "/2019/strawstairies/",` in order for the
links to be relative when running `npm run build`. Then, copy the
`.vuepress/dist/` folder into the appropriate POE server folder to finish
setting it up.

For running as the root on a server, such as GH pages, Netlify, or a custom
server, the base property can just be deleted and the default value used.

### Netlify
It is important to know that commits pushed to the master branch of this repo
are *automatically* pushed onto the Netlify-hosted version of the site. In fact,
pushing a commit causes an API trigger on the Netlify setup which starts a new
build! While this might not be the best option, it works for our small team, the
small scale nature of the site, and the short timescale of the project.
