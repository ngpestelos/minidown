# Minidown  [![Build Status](https://travis-ci.org/jjyr/minidown.png?branch=master)](https://travis-ci.org/jjyr/minidown)

Minidown is yet another markdown parser, with:

* light weight
* no dependencies
* pure ruby
* fast
* follow GFM(GitHub Flavored Markdown)

## Installation

Add this line to your application's Gemfile:

    gem 'minidown'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install minidown

## Basic usage

```ruby
require 'minidown'

Minidown.render('*hello*')
#=> "<p><em>hello</em></p>"
```

## Custom your own handler

```ruby
highlight_with_pygments = ->(lang, content) {
  Pygments.highlight(content, :lexer => lang)
}

Minidown.render source, code_block_handler: highlight_with_pygments

# if you don't like pass options every time
parser_with_highlight = Minidown::Parser.new code_block_handler: highlight_with_pygments
parser_with_highlight.render source
```

## Command line

```
wget https://raw.github.com/mojombo/github-flavored-markdown/gh-pages/_site/sample_content.md
minidown sample_content.md > result.html
open result.html
```
looks nice!

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
