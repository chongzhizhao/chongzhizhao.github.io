Some [helpful](https://gador.github.io/how-to-manage-passwords-with-pass.html)
[resources](https://medium.com/@davidpiegza/using-pass-in-a-team-1aa7adf36592)
can be [found](https://wiki.archlinux.org/title/Pass) online. But of course,
refer to the [manual](https://www.passwordstore.org/) first.

The `pass` tool depends on the `gpg` utility. The `pass-tomb` extension, on the other
hand, is optional based on personal preferences. The command below should open prompts
that demand some personal information before generating a key pair.

```
gpg --gen-key
```

The tool can then be set up by running

```
pass init <gpg_id>
```
