<h1 align="center">byte reader</h1>
<p align="center">A <strong>minimum</strong> byte-by-byte reader for parsing input.</p>

<div align="right">
    <img alt="build check status of byte_reader" src="https://github.com/kana-rus/byte_reader/actions/workflows/check.yml/badge.svg"/>
    <img alt="test status of byte_reader" src="https://github.com/kana-rus/byte_reader/actions/workflows/test.yml/badge.svg"/>
</div>


## Usage
```rust
use byte_reader::Reader;

fn main() {
    // Get a `&[u8]` or `Vec<u8>` input from
    // a File, standard input, or something
    let sample_input = b"Hello, byte_reader!".as_bytes();

    // Create mutable `r`
    let mut r = Reader::new(sample_input);

    // Use some simple operations
    // to parse the input
    r.consume("Hello").unwrap();
    r.consume(",").unwrap();
    r.skip_whitespace();
    let name = r.read_snake().unwrap(); // byte_reader
    let name_starts_at = r.column();    // 8
    r.consume("!").unwrap();

    println!("Greeted to {name}.");
    println!("The name starts at column {name_start_at} on line 1.");
}
```
