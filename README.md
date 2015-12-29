Primer-Angular2
======

try Angular2.

## Memo

### ngFor

    <li *ngFor="#hero of heroes">

- The (*) prefix to ngFor indicates that the <li> element and its children constitute a master template.
- The # prefix before "hero" identifies the hero as a local template variable. We can reference this variable within the template to access a hero’s properties.


### Service

      heroService = new HeroService(); // don't do this

That's a bad idea for several reasons including

- Our component has to know how to create a HeroService. If we ever change the HeroService constructor, we'll have to find every place we create the service and fix it. Running around patching code is error prone and adds to the test burden.

- We create a new service each time we use "new". What if the service should cache heroes and share that cache with others? We couldn't do that.

<br>

We have to teach the injector how to make a HeroService by registering a HeroService provider. Do that by adding the following providers array property to the bottom of the component metadata in the @Component call.

    providers: [HeroService]

<br>

We stated earlier that if we injected the parent AppComponent HeroService into the HeroDetailComponent, we must not add a providers array to the HeroDetailComponent metadata.

Why? Because that tells Angular to create a new instance of the HeroService at the HeroDetailComponent level. The HeroDetailComponent doesn't want its own service instance; it wants its parent's service instance. Adding the providers array creates a new service instance that shadows the parent instance.

Think carefully about where and when to register a provider. Understand the scope of that registration. Be careful not to create a new service instance at the wrong level.

## Slides

<script async class="speakerdeck-embed" data-id="16d2fc71c92e43efb9fa76e2264883dd" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

<script async class="speakerdeck-embed" data-id="6bf0c89c81364e4bbd2d2ddf4d92763c" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## TypeScript

> <a href="http://liginc.co.jp/190026" target="_blank">【 TypeScript入門】特徴と機能の一部をまとめました | 株式会社LIG</a>