# SVG [![Build Status][travis-img]][travis-url]

Currently the library is limited to the parsing of the [data attribute][1] of
paths.

## [Documentation][docs]

## Usage

```rust
#![feature(core)]

extern crate svg;

use svg::path::{Command, Data, Positioning};

fn main() {
    let data = Data::parse("M0,0 l0,1 1,0 0,-1 z").ok().unwrap();

    for command in data.iter() {
        match command {
            &Command::MoveTo(Positioning::Absolute, ref coordinates) => {
                println!("Move to {:?}.", coordinates);
            },
            &Command::LineTo(Positioning::Relative, ref coordinates) => {
                println!("Draw line segments between {:?}.", coordinates);
            },
            &Command::ClosePath => {
                println!("Close the path.");
            },
            _ => {
                println!("Not sure what to do.");
            }
        }
    }
}
```

## Contributing

1. Fork the project.
2. Implement your idea.
3. Create a pull request.

[1]: http://www.w3.org/TR/SVG/paths.html#PathData

[travis-img]: https://travis-ci.org/bodoni/svg.svg?branch=master
[travis-url]: https://travis-ci.org/bodoni/svg
[docs]: https://bodoni.github.io/svg
