# Destiny changes

- `tls`: the `openssl-static` configuration and the optional
  `openssl-static` dependency are removed. Destiny-Org/packages does not
  carry `openssl-static` (it bundled prebuilt OpenSSL libraries that Destiny
  cannot build and that would need manual security updates). TLS uses the
  system's OpenSSL through the `openssl` package.
