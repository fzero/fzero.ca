---
layout: post
title: 'The async web, or "Javascript sucks, but someone did something cool on it"'
date: 2013-10-20 13:23
comments: true
published: true
categories:
- articles
- geek
- web
- programming
---

(Disclaimer: this is ranty. Don't say I didn't warn you.)

I'm old in internet years. I was there for the first browser war, fighting my way through layouts full of `<table>` tags while adjusting margins with `shim.gif` to get around half-assed CSS implementations. You could even call me a veteran. If you have also been working with the web since the 90s, you know that [server-side Javascript isn't a new thing](http://en.wikipedia.org/wiki/Server-side_JavaScript#Server-side_JavaScript). Even so, it has become the new hotness lately.

<img src="http://nodejs.org/images/logos/nodejs-green.png" class="left"/>I'm talking about [Node.js](http://nodejs.org), of course. Everybody wants to jump into the real-time web bandwagon, and Node.js is the passport to the promised Web 3.0 land (or is it 4.0 already?). Single-page apps! Asynchronous connections! Websockets! [Webscale!](http://www.youtube.com/watch?v=b2F-DItXtZs) Woo!

Well, I'm all for it. No, seriously, it's cool stuff. The problem is, of all the languages anyone could have chosen to make this happen - which of course include Ruby, Python and even PHP - someone had to pick Javascript. [Wat?](https://www.destroyallsoftware.com/talks/wat)

While Javascript is ubiquitous and pretty easy to get started with, it's also so flawed someone took the time to create [a whole new language that gets "compiled" into it](http://coffeescript.org/) to make it less painful to develop larger applications. *And it's a huge success!* There's nothing quite like Coffeescript happening on other languages, and certainly not for the same reasons.[*](#asyncfootnote)

But yes, Node does work. Even if it forces certain [patterns that can become messy very quickly](http://www.gameclosure.com/blog/2013/03/unravelling-nested-callbacks-with-ff) and breaks built-in Javascript features like [exception handling](http://stackoverflow.com/questions/17572259/is-the-try-catch-finally-block-synchronous-in-node-js). You just have suck it up and code around it. Or, you know, just use Coffeescript and hope for the best.

Of course it's not all bad. There are amazing frameworks like [Meteor](http://www.meteor.com/) and [Derby](http://derbyjs.com/) that make it very easy to create real-time collaborative apps. [Express](http://expressjs.com/) is a pretty good platform to create JSON APIs and regular websites that, admittedly, perform way better than [Sinatra](http://www.sinatrarb.com/) (the Ruby equivalent). But I can't help thinking I could achieve the same results with less hassle if, say, Python was picked up by the hipsters as the foundation of the "new" asynchronous web craze (it has [Tornado](http://www.tornadoweb.org) after all).

To be honest, my hopes lie with [Go](http://golang.org) right now. It's still a bit rough around the edges, but so was Ruby when Rails exploded. Go is statically typed and compiles to native binaries, which makes it extremely fast and light. It's also built for concurrency and includes pretty good standard packages to build networked and web applications. The only missing pieces are a decent package manager (the [current state of affairs](http://dev.af83.com/2013/09/14/a-journey-in-golang-package-manager.html) is frankly very messy) and a web framework that can bring all that potential to fruition. [Revel](http://robfig.github.io/revel/) is promising, but it's still missing a few key parts to make it brilliant.

It's interesting to note that Go and Node.js even share similar patterns. Error handling is a good example. Here's a Go snippet to read a file and print its contents:

``` go
data, err := ioutil.ReadFile("/tmp/data.txt")
if err != nil { panic(err) }
fmt.Print(string(data))
```

And here's the Javascript equivalent:

``` javascript
fs.readFile('/tmp/data.txt', function (err, data) {
  if (err) throw err;
  console.log(data);
});
```

Take out the mandatory callback on Javascript and it's pretty much the same code. The main difference is Go gives you the **option** of [running functions asynchronously](https://gobyexample.com/goroutines) instead of forcing callbacks due to bad language design.

All things considered, it's a good time to be a developer. It's a pity the best technologies seldom become the most popular, while inexplicable fads take over the landscape from time to time. Such is life. But if people could realize that abandoning SQL completely wasn't such a good idea, who knows? Maybe the best tools for the job can become more popular used sooner rather than later.


---
<a name="asyncfootnote"></a>* _Before anyone mentions it, [Elixir](http://elixir-lang.org/) is a very different case from Coffeescript. [Erlang](http://www.erlang.org/)'s syntax is pretty far from mainstream, but the language and its tools are absurdly reliable and fast. Javascript is orders of magnitude slower and nothing can touch Erlang's built-in concurrency and fault tolerance._
