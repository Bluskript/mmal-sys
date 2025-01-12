# Rust definitions for mmal

This is the library used on the Raspberry Pi to interact with VideoCore. Basic
functions are to control the camera, encode and decode video. Applications that
use it (natively, not via Rust) include `raspistill` and `VLC`.

[Documentation](https://pedrosland.github.io/mmal-sys/)

These FFI definitions are, for the most part, automatically generated by
bindgen.

If you would like to generate the bindings yourself, simply enable the
`generate_bindings` feature. By default the pre-generated bindings are used.

Please note that I have no idea what I am doing with rust so bindgen could
probably be tweaked to improve its output.

PRs welcome. Breaking changes that make the library better to use eg changing
`constified_enum_module` are also welcome.

Steps for improvement:

-   Evaluate if rust nightly is useful or switch on/off bindgen's nightly flag
    if running in nightly or not
-   Make API as natural as possible
-   Implement `fmt::Display` trait for more types or remove it entirely

## Compile on a non-pi host

Find the latest raspberry pi firmware:
https://github.com/raspberrypi/firmware/tags

Substitude `$firmware` with the name of the latest tag.

```bash
sudo wget -O - https://github.com/raspberrypi/firmware/archive/$firmware.tar.gz | sudo tar -xzf - -C / --strip-components 2 firmware-$firmware/hardfp/opt/vc
```
