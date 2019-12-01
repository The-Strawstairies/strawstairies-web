# strawstairies-web
A website for the strawstaries!

## Building Notes

When deploying on the POE web server, you need to
change the `base` property in the `config.js` file to read `base: "/2019/strawstairies/",` in order for the links to be relative when running `npm run build`.

For running as the root on a server, such as GH pages, Netlify, or a custom server, the base property can just be deleted and the default value used.
