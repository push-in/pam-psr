# pushinbr/pam-psr-bridge

PSR-7, PSR-15 and PSR-17 interoperability for Pam using the official PHP-FIG
interfaces.

```bash
pam composer require pushinbr/pam-psr-bridge
```

Pass a PSR-15 handler and middleware to `Pam\App::handler()` and
`Pam\App::middleware()`; Pam converts native requests and responses at the runtime
boundary.

## License

Free and open-source under the [Apache License 2.0](LICENSE). You may use,
modify, and distribute this package for any purpose, including commercially.


## Recommended PAM workflow

Install inside an existing PAM project with `pam composer require pushinbr/pam-psr-bridge`. PAM performs the package operation through its private PHP runtime; a global PHP or Composer installation is not required.

Run `pam doctor` after dependency changes and before creating a release. The project remains a normal Composer project with a standard manifest, lockfile, PSR-4 autoloading, and `vendor/autoload.php`.

## API guide

| Surface | Use it for |
| --- | --- |
| PSR-7 | Convert PAM native requests and responses to the official HTTP message interfaces. |
| PSR-15 | Run middleware and request handlers through `App::middleware()` and `App::handler()`. |
| PSR-17 | Use installed HTTP factories where a package requires standard message construction. |
| Runtime boundary | Convert once at the edge while PAM retains native transport ownership. |

Pass a PSR-15 handler to `Pam\App::handler()` and PSR-15 middleware to `Pam\App::middleware()`. Keep blocking-library behavior in mind: standards compatibility does not make synchronous package I/O asynchronous.

## Production checklist

- Keep request data and mutable state scoped to the current request.
- Test success, validation failure, exception, cancellation, and timeout paths.
- Configure explicit limits and avoid unbounded payloads, queues, or retained collections.
- Run `pam doctor`, `pam test`, and the relevant integration suite before release.
- Validate real dependencies and workload behavior; compatibility is not inferred from package installation alone.

## Troubleshooting

- **Class not found:** run `pam composer install`, verify PSR-4 configuration, and rerun `pam doctor`.
- **Behavior differs over the network:** reproduce with PAM's transport integration tests; in-memory execution does not model the socket boundary.
- **A dependency blocks a worker:** use PAM-native I/O, a compatible event loop, a process pool, or additional isolated workers.

## Documentation and support

- [PAM introduction](https://push-in.github.io/pam-docs/introduction/)
- [Package ecosystem](https://push-in.github.io/pam-docs/packages/overview/)
- [Runtime compatibility](https://push-in.github.io/pam-docs/runtime/compatibility/)
- [Report an issue](https://github.com/push-in/pam-psr-bridge/issues)

Report security vulnerabilities through GitHub private vulnerability reporting or the PAM security policy, not a public issue.
