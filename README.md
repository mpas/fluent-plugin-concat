# fluent-plugin-concat

[![Build Status](https://travis-ci.org/okkez/fluent-plugin-concat.svg?branch=master)](https://travis-ci.org/okkez/fluent-plugin-concat)

Fluentd Filter plugin to concatenate multiline log separated in multiple events.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'fluent-plugin-concat'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install fluent-plugin-concat

## Configuration

**key** (required)

The key for part of multiline log.

**separator**

The separator of lines.
Default value is `"\n"`.

**n\_lines**

The number of lines.
This is exclusive with `multiline_start_regex`.

**multiline\_start\_regexp**

The regexp to match beginning of multiline.
This is exclusive with `n_lines.`

**stream\_identity\_key**

The key to determine which stream an event belongs to.

## Usage

Every 10 events will be concatenated into one event.

```aconf
<filter docker.log>
  @type concat
  key message
  n_lines 10
</filter>
```

Specify first line of multiline by regular expression.

```aconf
<filter docker.log>
  @type concat
  key message
  multiline_start_regexp /^Start/
</filter>
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

