```
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

```
info: downloading installer

Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:

  /home/user_name/.rustup

This can be modified with the RUSTUP_HOME environment variable.

The Cargo home directory located at:

  /home/user_name/.cargo

This can be modified with the CARGO_HOME environment variable.

The cargo, rustc, rustup and other commands will be added to
Cargo's bin directory, located at:

  /home/user_name/.cargo/bin

This path will then be added to your PATH environment variable by
modifying the profile files located at:

  /home/user_name/.profile
  /home/user_name/.bash_profile
  /home/user_name/.bashrc

You can uninstall at any time with rustup self uninstall and
these changes will be reverted.

Current installation options:


   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable (default)
               profile: default
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
>
```

Select option **1**.

```
$ rustup show
Default host: x86_64-unknown-linux-gnu
rustup home:  /home/user_name/.rustup

stable-x86_64-unknown-linux-gnu (default)
rustc 1.58.1 (db9d1b20b 2022-01-20)
```

```
$ rustup toolchain install nightly
$ rustup default nightly
$ rustup target install x86_64-unknown-linux-musl
```

