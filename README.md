# Nuxt Full Static

[Going full static](https://nuxtjs.org/blog/going-full-static)

## Build Setup

```bash
# install dependencies
npm install

# serve with hot reload at localhost:3000
npm run dev

# build for production and launch server
npm run build && npm run start

# generate static project
npm run build && npm run export

# serve static site after build and export
npm run serve
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

## About

### Intro and some history

Recently, Nuxt released version 2.13.0 which came with a host of new features. The feature I was most excited about was the full static site generation. You may think, "Hey, Nuxt can already generate static sites." and you'd be right but it turns out that the old method was more pre-rendering than static site generation. This release aims to solve that issue and make Nuxt more friendly to full static generation which is especially helpful to us JAMstack folks.

Previously, if you wanted to generate a static site, you would use the `nuxt generate` command. This would pre-render all your assets into a `dist` folder which you could serve or deploy for a big performance boost.

## Using full static site generation

Nuxt 2.13.0 introduces a new `nuxt.config.js` option, `target` which can be set to `static` to take advantage of the new capabilities. `target` will default to `server` for traditional Nuxt SSR applications.

Now when you want to generate a full static site you will be able to use `nuxt build` after setting the `target` option to `static` in `nuxt.config.js`. After the build finishes, the static site can be generated by using `nuxt export`. Once the static files are generated you can serve the app using `nuxt serve`.

> If you don't want to set the `target` option in `nuxt.config.js` for some reason you can run the build command with the target flag value set to static (`nuxt build --target static`)

And, that's it. That's all you have to do to take advantage of full static site generation.

`nuxt export` is set to replace `nuxt generate` which will be depreciated in Nuxt 3. Right now, `generate` will remain as a alias to `export`.

## Observations (How it works in the wild)

So far I've set up a new project using the `target: static` option and upgraded an existing project to use it as well. Both were simple to upgrade and get the full static export working.

The new project had a slightly quicker page load at 1.7 using `export` while the same minimal project used to clock in at 2.0 seconds. When load times are this quick, 300 milliseconds is a nice improvement. Using Google Lighthouse to benchmark, the page speed score varies between 98-100 for a new project. My existing project which has a few more pages, increased it's page speed score from low 70s to 88-90.

## Conclusion

I'm definitely excited about this new feature and already using it for personal projects. As a JAMstack aficionado, I love being able to optimize performance and get faster page loads using a developer-friendly framework like Nuxt. Here's to this and other future imporvements sure to come.

## References

[New project created with create-nuxt-app using full static site generation](https://github.com/jbratcher/nuxt-full-static-2.13.0)
[Live Demo](https://boring-pike-ec0592.netlify.app/)

[Existing project refactored to use full static site generation](https://github.com/jbratcher/nuxt-netlify-cms-starter-kit)
[Live Demo](https://admiring-clarke-8c0fde.netlify.app/)

[Nuxt Official Blog - Going Full Static](https://nuxtjs.org/blog/going-full-static/)
