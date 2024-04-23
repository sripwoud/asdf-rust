I initially forked  [asdf-rust](https://github.com/code-lever/asdf-rust) because I wanted to automate adding specific components and targets to my rust installation.  
Until I realized this is overkill; one can simply use an [asdf plugin hook](https://asdf-vm.com/manage/configuration.html#plugin-hooks) instead:

`post_asdf_install_rust` (make it executable: `chmod +x post_asdf_install_rust`)
``` shell
#!/bin/bash

export RUSTUP_HOME="$XDG_DATA_HOME/asdf/installs/rust/$1"
rustup component add rust-analyzer rust-src
rustup target add wasm32-unknown-unknown

```

`$ASDF_CONFIG_FILE`
```
post_asdf_install_rust = "$XDG_CONFIG_HOME/asdf/post_asdf_install_rust" $1
```

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
#### Default `cargo` crates

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

#### Default rust components
`asdf-rust` will interactively ask you whether you want to install specific rust components (`rustup --component <components>`).  
Or it will default to the content of `$ASDF_RUST_DEFAULT_COMPONENTS` (`$HOME/.default-rust-components`).

#### Default rust targets
`asdf-rust` will interactively ask you whether you want to install specific rust targets (`rustup --target <targets>`).  
Or it will default to the content of `$ASDF_RUST_DEFAULT_TARGETS` (`$HOME/.default-rust-targets`).
