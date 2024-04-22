# asdf-rust


Rust plugin for [asdf](https://github.com/asdf-vm/asdf) version manager.

## Install

```shell
asdf plugin-add rust https://github.com/sripwoud/asdf-rust.git
```

After you have installed rust, do NOT follow the directions it outputs to update your PATH
 -- asdf's shim will handle that for you!

## Use

Check [asdf](https://github.com/asdf-vm/asdf) readme for instructions on how to install & manage versions of Rust.

### Customization
### Default `cargo` crates

asdf-rust can automatically install a default set of packages with `cargo` right after installing a Rust version.
To enable this feature, provide a `$HOME/.default-cargo-crates` file that lists one package per line, for example:

```text
// cli-tools
ripgrep

// install from source
--git https://github.com/sharkdp/bat
```

You can specify a non-default location of this file by setting a `ASDF_CRATE_DEFAULT_PACKAGES_FILE` variable.

`ASDF_RUST_PROFILE` variable can be used to install different from `default` profile (e.g. minimal or complete).

### Default rust components
`asdf-rust` will interactively ask you whether you want to install specific rust components (`rustup --component <components>`).  
Or it will default to the content of `$ASDF_RUST_DEFAULT_COMPONENTS` (`$HOME/.default-rust-components`).

### Default rust components
`asdf-rust` will interactively ask you whether you want to install specific rust targets (`rustup --target <targets>`).  
Or it will default to the content of `$ASDF_RUST_DEFAULT_TARGETS` (`$HOME/.default-rust-targets`).
