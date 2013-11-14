# Pry

Pry is a powerful alternative to the standard IRB shell for Ruby. It features syntax highlighting, runtime invocation, and source and documentation browsing. To learn more about it, check out the [Pry Wiki](https://github.com/pry/pry/wiki). The [end of this tutorial](https://github.com/bitmakerlabs/resources/blob/master/using_pry.md#more-about-pry) also includes additional external links.

As you are working on increasingly complex applications, you will need to acquaint yourself with problem solving and debugging. Pry can help by providing tools to gain more insight into what's going on with your code.

#### Source and Documentation Browsing

We install the gem by running the following command:

```bash
$ gem install pry
```

We start our pry session:

```bash
$ pry
```

We can view what commands are available while using pry:

```bash
pry(main)> help
```

We'll have to install an add on called "pry-doc", which provides access to Ruby core documentation and source code within Pry:

```bash
$ gem install pry-doc
```

You can check out anything you would find in the Ruby docs in your terminal. Try the following command:

```bash
pry(main)> show-doc Array
```

It should output a brief explanation of the Array class.

![Pry Show-doc Array](http://i.imgur.com/tZwKCLW.png)

You can also view documentation for specific methods:

```bash
pry(main)> show-doc Array#each
```

![Pry show-doc Array#each](http://i.imgur.com/nvIGZBb.png)

## Runtime Invocation Use Cases

Pry can be invoked in the middle of a running program. It opens a Pry session at the point it's called and makes all program state at that point available. It can be invoked on any object using the `my_object.pry` syntax or on the current binding (or any binding) using `binding.pry`. The Pry session will then begin within the scope of the object (or binding). When the session ends the program continues with any modifications you made to it.

There are a variety of use cases for runtime invocation of a Pry session, some include:

### Developer Console:

Having Pry run in its own thread giving you interactive access to your application while it is running.

### Debugging:

Inserting a binding.pry at the point in your program you want to debug, making all state at that point available for interactive inspection (including locals).

### REPL-oriented development and hot-patching:

Modifying the program while it is running to provide new features.

### Try it Yourself

Now let's get started with a couple Pry commands. We'll be using `show-input`, `amend-line N [replacement code]` and `binding.pry`. Here's an example of using `show-input` and `bind.pry` in combination.

```bash
pry(main)> def learning_pry
pry(main)>*   puts "Learning pry was an invaluable experience"
pry(main)>*   puts "Now I am set to conquer the world"
pry(main)>* show-input
1: def learning_pry
2:   puts "Learning pry was an valuable experience"
3:   puts "Now I am set to conquer the world"
pry(main)>*   amend-line 2 puts "Learning pry was an invaluable experience"
1: def learning_pry
2:   puts "Learning pry was an invaluable experience"
3:   puts "Now I am set to conquer the world"
pry(main)>*   show-input
1: def learning_pry
2:   puts "Learning pry was an invaluable experience"
3:   puts "Now I am set to conquer the world"
pry(main)>* end
```

Last and most importantly, we're going to learn how to use `binding.pry` to debug our Ruby programs. Create a ruby script with the following.

**`ruby_test.rb**
```ruby
def say_hello
  binding.pry
  puts '1', '2'
  puts '3', '4'
end

say_hello
```

In your terminal, type the following:

```bash
$ pry
pry(main)> load 'ruby_test.rb'
pry(main)> play -l 3
```

This shows how you can stop programs at any point and run specific lines of code in your program to better understand how it works.

## More about pry

[Railscasts: Pry with Rails](http://railscasts.com/episodes/280-pry-with-rails)

[Setting up Rails or Heroku to use Pry](https://github.com/pry/pry/wiki/Setting-up-Rails-or-Heroku-to-use-Pry#wiki-heroku)
