# Mikado Graph Generator

Welcome to a DSL for creating Mikado Graphs using *GraphViz*.

## Installation

Add this line to your application's Gemfile:

```ruby
gem "mikado_graph"
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install mikado_graph

### Prerequisites

Ensure you have *GraphViz* installed. On macOS you can install it using Homebrew with the following command:

```bash
brew install graphviz
```

## Usage

You can use this gem's DSL in the following way to create a Mikado Graph generator definition file:

```ruby
require "mikado_graph"

MikadoGraph::Generator.generate do
  state("State A").depends_on do
    state("State B").depends_on do
      state("State D")
      state("State E")
    end
    state("State C").depends_on do
      state("State F")
      state("State G")
    end
  end
end
```

You can then execute this file in the terminal using:

```bash
ruby multi_level_mikado_graph_generator.rb | dot -Tpng -o img/multi_level_mikado_graph.png
```

This will utilize the *GraphViz* `dot` command to create this PNG output of the above Mikado Graph generator definition:

![Multi-Level Mikado Graph](https://github.com/snasirca/mikado_graph_generator/blob/master/img/multi_level_mikado_graph.png)

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/snasirca/mikado_graph_generator. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).