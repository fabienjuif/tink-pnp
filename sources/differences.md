## Sources
 - https://dev.to/arcanis/plugnplay-and-tink-4684
 - https://www.theregister.co.uk/2018/09/15/npm_yarn_project/
 - Petit clash: https://twitter.com/maybekatz/status/1040633445624377344

## Notes
 - **yarn** First of all, note that Plug'n'Play is a specification (arcanis)
 - **yarn** It only takes a single line of code from the dedicated PnP API to find out the location of the package you're looking for, no matter which tool you use. (arcanis)
    * It's made to provide better tools to packages that previously had to reimplement the module resolution logic by themselves, and certainly not make their lifes harder. (arcanis)
    * On top of this, we're fully transparent through the standard Node APIs, meaning that require.resolve works just as you expect. This makes Plug'n'Play compatible with the vast majority of the ecosystem, and the few packages that aren't can usually just migrate to require.resolve and be done with it. (arcanis)
 - **tink**, for better or worse, overrides the fs and child_process built-in modules (arcanis)
 - **tink**, doesn't get rid of the node_modules (arcanis)
    * Or at least not much more than what **pnpm** already does (arcanis)
    * node_modules still exist from Node's point of view, even if they are virtualized (arcanis)
    * the fact that the resolution relies on the node_modules nested hierarchy at all is [the problem] (arcanis).
 - Ecosystem: I believe we have a responsibility in ensuring the ecosystem is in a sane state that makes it possible for other tools to emerge and eventually replace us. (arcanis)
 - **tink**'s feature set seems closely aligned with what pnpm already promises (arcanis)
 - allowing dependencies to be installed on the fly (Thomas Clarburn)
 - With **tink**, the hope is that the process can become a bit less involved by removing the need for package installation via the npm install command. (Thomas Claburn)
 - In an email to The Register, Rebecca Turner, product manager of open source software at NPM, said **tink**'s goal is to make module installation not just transparent and faster but also invisible. (Thomas Claburn)
 - "At the moment, they differ in that Yarn Plug'n'Play doesn't change your workflow – you still have to run yarn to get a copy of your modules," (Rebecca Turner, via Thomas Claburn)
   * "By contrast, tink is drop-in-replacement for Node itself, so you just run your program with it and it will install the modules you need if they aren't yet on your system." (Rebecca Turner, via Thomas Claburn)

## Why node_modules resoluton is not good (arcanis)
 - Two of the main issues with node_modules are that
   * they make the boundaries between packages blurry (allowing to require dependencies by the sheer virtue of hoisting),
   * and that they put various optimizations entirely off the table due to the limitations of a filesystem-based resolution approach (the main one being path conflicts).

## Arcanis final notes
> Yarn's philosophy in general is very different from the one npm seemed to have adopted for their long-term plans. It's clear that they now wish to wrap Node behind an opinionated layer with various native integrations, as evidenced by the "automatic TypeScript and JSX support" features, and the way they prefer to lazily install their dependencies at runtime.
>
> As for Yarn, we believe in a sounder and more generic approach where as much as possible is done ahead of time, leaving little to no work on the CI and production servers, shortening the feedback loop, and increasing the trust you can have that your deployment will go through. Our responsibility goes into building a solid foundation that will allow for your applications to stay stable and predictable for the years to come. You can be sure that we won't let that go into the way of the user experience though, and we'll soon have very exciting features to show you how serious we are 😊
