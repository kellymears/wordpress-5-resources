# Tooling

## The Pragmatic Developer’s Guide to the WordPress Block Editor
### Part I. Developer Tooling
---
For someone who has never worked with modern JavaScript the process of developing for the new editor is going to pose a number of hurdles — both syntactic and conceptual. The largest of the hurdles are JS preprocessors and their associated build tools (most commonly Webpack & Babel). You’ll find these snarly, intimidating bundles of code employed to seemingly endless, magical ends  in both the byzantine halls of corporate monorepos and the humble foyers of your overly chatty neighborhood code dealers 👋🏽. 

With little exception, preprocessors are broadly essential to the way today’s JavaScript sourcerers engage in their dark arts. 

For a beginner, the most frustrating thing about this paradigm is that we’re talking about barriers to entry  — one literally can’t get started with the business of beginning until they’ve either figured them out or figured out a way to sidestep them long enough to learn what it is they’re even _hoping to accomplish_.

Thankfully, these shortcuts exist and some of them are simple enough to have running within 10 minutes. Others take a bit more leg work but are worth it if one were planning to put some serious time in.

Ahmad Awais’ [create-guten-block starter](https://github.com/ahmadawais/create-guten-block) is currently the defacto starter kit for block-building — and for good reason. It’s bulletproof, requires little-to-no-comprehension and allows a newbie to get a functional (albeit basic) environment up-and-running quick. Unfortunately it doesn’t have _browsersync_, which means you will need to manually refresh your browser after every change. Maybe you’re used to that workflow, but if you’ve been using something that already leverages “hot loading” (like Roots’ Sage 9 😉) it’s going to be a rough transition. 

So, yay Ahmad! The community needs this and is truly indebted to your contributions. But beyond that I won't be talking about it further — except to note that if you, my dear Reader, think you have found a good fit with Ahmad’s kit you should feel free to get it up and running and rejoin us just a bit farther down the page — you’ll be limited only in the sense that your experience won’t be quite as smashing. Moving on!

Another option is [Laravel Mix](https://github.com/JeffreyWay/laravel-mix). This is a great option and please do avail yourself. It is, unfortunately, just a little out of scope for this article but is likely to be the tooling I settle down with for the long haul (I’m planning to propose over the upcoming holiday break). 

And then there is, of course, the formant shape of what is yet to come —  K Adam's [“Hot Module Replacement For Gutenberg Blocks”](https://humanmade.com/2018/11/26/hot-module-replacement-for-gutenberg-blocks/) is probably the most intriguing developer-oriented overview of block production anybody has put together so far. If you’re not the type to go full-on _/My Bloody Valentine/_ every time someone says the word “engineer” then I bet that article is exactly what you’re looking for. If it’s too much for you then welcome to the club, friend. The coffee is terrible but stick with it — we’re going places.

For the purposes of this article I’m going to use [webpack.io](https://webpack.io), an upstart framework by [Swashata Ghosh](https://swas.io). Licensed MIT. I’m not going to bother really explaining too much as I have a lot of ground to cover, and Swashata’s documentation is pretty good. That said, I will still try to hit on all the pre-reqs needed to get going. Like so:

### Establishing a Dev Environment
---
Create a folder for your plugin and within that folder install the wpackio command line tool. Finish by running the CLI’s bootstrap script.  It’ll ask you questions with relatively obvious answers. You want React and Sass, which are preselected anyway.
``` sh
$ mkdir voxels && cd voxels
$ npx @wpackio/cli
$ yarn bootstrap
```

In `wpackio.project.js`  we’re going to give our plugin a camelCased name and indicate the name of the folder it resides in:
[image:4B85EA65-BC0D-46EC-AD82-2C8A19D9ED98-15904-00001941366478AE/image-1.png]

Then, under files, we are going to indicate where we’re stashing our block src JS. Note that I have included two entry points — one is for the actual blocks themselves. The other is in case you have any extra JS you’d like to run outside the editor — no Gutenbergian scripts are enqueued by default for the reader. So, if you want that, make sure to include the `public` entry as demonstrated. 
[image:48E25364-A874-459F-91B6-86A0176AE121-15904-0000196B678B9A52/image-2.png]

Last thing before we move on to the next file — we need to clue Babel in to the fact that we’re going to be utilizing JSX and that these rules are applicable to `wp.element.createElement`, WordPress’ stand-in for `React`. By the way, it is so, so WordPress’ style to turn something like `React` into `wp.element.createElement`, wouldn’t you agree? 💁🏽‍♀️)

##### [IMG] ####

`wpackio.server.js` is your dev environment. It is relatively easy to configure. Set  your `host` and `proxy`. Using the external IP is better than something like localhost. I found this particularly true when developing  in Docker.

One small gotcha — if you are using Bedrock or have otherwise deviated from the WordPress factory default you’ll need to adjust your `distPublicPath`. 

Here is my config in full:

##### [IMG] ####

Last bit of setup is to enqueue the development and production assets in your main plugin file. This must be done ASAP and its accomplished using a helper class included with wpack.io. 

I chose to do this by defining a small class, but this is light enough to easily be a couple simple functions. Note that later on you may very well find yourself writing more PHP to go along with your blocks so personally I think having a structure in place to keep that all organized is the Way To Go ™️. But, for the sake of clarity I’m breaking everything out into functional units.

``` js
$webpack = new \WPackio\Enqueue(
   'voxels', // #NOTE when in doubt, use your appName from step #1
   'assets', // #NOTE as defined in wpackio.project.js
   '0.0.1',
   'plugin',
   __FILE__ 
);
```

Then, we hook our scripts up to the helper class:
``` php
add_action( 'admin_enqueue_scripts', 'webpack_assets_editor' );
add_action( 'wp_enqueue_scripts', 'webpack_assets_public' );

function webpack_assets_editor() {
	$webpack->enqueue( 'blocks', 'editor', [
		'js' => true,
      'css' => true,
      'js_dep' => [
      	'wp-blocks',
         	'wp-element',
          'wp-components',
          'wp-editor',
          'lodash',
          'wp-i18n',
          'wp-hooks',
          'wp-data'],
        'css_dep' => [],
        'in_footer' => true,
        'media' => 'all',
     ]
  );
}

function webpack_assets_public() {
	$this->webpack->enqueue( 'blocks', 'public', [] );
}
```

Now you’re all set to install: `$ composer install` and `$ yarn && yarn build` should kick everything off. Try out `yarn start`, and you should see the message in browser indicating that you are all synced up and ready to ready to… well, read through the Github Issues which will be henceforth referred to as “The Gutenberg Docs”. 

I do want to point out one important thing that’s happening in the above `$webpack->enqueue()`. The dependencies above need to be included here because otherwise we will not have access to Automatic’s packages from within our sanctuary. You may want to pass in other stuff beyond what I have but that should get you going. 

Hopefully, with that, you have enough to get started. Download some source code and pick it apart. Do, forreal, read those github issues. And the [Gutenberg documentation](https://wordpress.org/gutenberg/handbook/), despite being crappier than my jokes and flimsier than [Gutenberg’s current rating on wordpress.org](https://wordpress.org/plugins/gutenberg/), is a legitimately useful resource from time-to-time. 

