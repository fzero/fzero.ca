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

I'm old in internet years. I was there for the first browser war, fighting my way through layouts made with `<table>` tags while adjusting margins with `shim.gif` to get around half-assed CSS implementations. You could even call me a veteran. If you have also been working with the web since the 90s, you know that [server-side Javascript isn't a new thing](http://en.wikipedia.org/wiki/Server-side_JavaScript#Server-side_JavaScript), even though it has become the new hotness lately.

<img src="http://nodejs.org/images/logos/nodejs-green.png" class="left"/>I'm talking about [Node.js](http://nodejs.org), of course. Everybody wants to jump into the real-time web bandwagon, and Node.js is the passport to the promised Web 3.0 land (or is it 4.0 already?). Single-page apps! Asynchronous connections! Websockets! [Webscale!](http://www.youtube.com/watch?v=b2F-DItXtZs) Woo!

Well, I'm all for it. No, seriously, it's cool stuff. The problem is, of all the languages anyone could have picked to make this happen, someone had to pick Javascript. [Wat?](https://www.destroyallsoftware.com/talks/wat)

While Javascript is ubiquitous and pretty easy to get started with, it's also so flawed someone took the time to create [a whole new language that gets "compiled" into it](http://coffeescript.org/) to make development less painful. *And it's a huge success!* There's nothing quite like Coffeescript happening on other languages, and certainly not for the same reasons.[*](#asyncfootnote)

But yes, Node does work pretty well. The V8 Javascript engine out-performs most popular runtimes in other languages, including Ruby's MRI[*](#mrifootnote) and cPython. But since everything is asynchronous, it forces certain [patterns that can become messy very quickly](http://www.gameclosure.com/blog/2013/03/unravelling-nested-callbacks-with-ff) and breaks built-in Javascript features like [exception handling](http://stackoverflow.com/questions/17572259/is-the-try-catch-finally-block-synchronous-in-node-js). Want better performance? Then you have suck it up and code around it. Or, you know, just use Coffeescript and hope for the best.

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

Take out the mandatory callback on Javascript and it's pretty much the same code. You have to pass errors around and handle them manually; Go doesn't have exceptions _by design_ and Javascript's asynchronous behavior _breaks them_. The main difference is Go gives you the _option_ of [running functions asynchronously](https://gobyexample.com/goroutines) instead of _forcing callbacks_ due to bad design.

Another similarity: neither Javascript or Go have a class-based object model. Javascript uses objects that work pretty much like associative arrays in PHP (or hashes in Ruby, or dictionaries in Python). They're not _really_ objects derived from classes - they just kinda sorta work like them.

``` javascript
// Defining a rectangle object
var rectangle = {
  width: 5,
  height: 10
};

// Adding an area() method
rectangle.area = function() {
  return this.width * this.height;
};


// Adding a perimeter() method
rectangle.perimeter = function() {
  return 2 * this.width + 2 * this.height;
};

// Calling the methods
rectangle.area();
rectangle.perimeter();
```

[Go has type structures that can contain data and functions](https://gobyexample.com/structs), therefore working just like classes (but only if you want to). It even provides [inheritance through embedding](http://golang.org/doc/effective_go.html#embedding).

``` go
// Defining a rectangle type
type rectangle struct {
    width, height int
}

// Adding an area() method to rectangle
func (r *rectangle) area() int {
    return r.width * r.height
}

// Adding a perimeter() to rectangle
func (r *rectangle) perimeter() int {
    return 2 * r.width + 2 * r.height
}

func main() {
    r := rectangle {
      width: 5,
      height: 10
    }

    // Here we call the 2 methods defined for our struct.
    fmt.Println("Area: ", r.area())
    fmt.Println("Perimeter:", r.perimeter())
    // ...
}
```

All things considered, it's a good time to be a developer. It's a pity the best technologies seldom become the most popular, while inexplicable fads take over the landscape from time to time. Such is life. But if people could realize that abandoning SQL completely wasn't such a good idea, who knows? Maybe the best tools for the job can become more popular sooner rather than later.


---
<a name="asyncfootnote"></a>* _Before anyone mentions it, [Elixir](http://elixir-lang.org/) is to [Erlang](http://www.erlang.org/) as [Scala](http://www.scala-lang.org/) is to [Java](http://www.java.com/). Also, it goes whithout saying that Javascript is orders of magnitude slower and less fault-tolerant than Erlang._

<a name="mrifootnote"></a>* _[jRuby](http://jruby.org/) is a completely different story, though - particularly the latest release. But then you need to run your code in the JVM. Take that as you will._
