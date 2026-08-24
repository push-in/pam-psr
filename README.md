<div align="center">

# pushinbr/pam-psr

## Compatibility package — do not use in new applications

This repository exists so older Composer projects keep installing safely. The maintained product is **[PAM HTTP PSR](https://github.com/push-in/pam-http-psr)**.

[![Replacement](https://img.shields.io/badge/replacement-pushinbr/pam--http--psr-2563eb?style=flat-square)](https://packagist.org/packages/pushinbr/pam-http-psr)
![Status](https://img.shields.io/badge/status-migration%20only-f59e0b?style=flat-square)

</div>

---

## Use this instead

```bash
pam composer require pushinbr/pam-http-psr
```

[PAM HTTP PSR](https://github.com/push-in/pam-http-psr) contains the active documentation, API examples, releases, issue tracker, and production guidance.

## Why the name changed

PSR-7/15/17 adaptation belongs to the HTTP product, not to the small PAM runtime.

## Migrate an existing project

Commit your current `composer.json` and `composer.lock`, then run:

```bash
pam composer remove pushinbr/pam-psr
pam composer require pushinbr/pam-http-psr
pam doctor
```

Run the application test suite before committing the new lockfile. Composer may continue to resolve this bridge transitively during a staged migration; application code should target the replacement package directly.

## Support policy

- No new features are added here.
- Security or resolution fixes may be published only to preserve migration safety.
- New documentation and issues belong to [PAM HTTP PSR](https://github.com/push-in/pam-http-psr).
- The package is marked abandoned on Packagist in favor of `pushinbr/pam-http-psr`.

This explicit compatibility repository is intentional: old installs remain understandable without making the current PAM ecosystem ambiguous.
