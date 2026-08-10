# qd-bloom.github.io

The dashboard moved behind Cloudflare Access.

It was previously served here as an encrypted single-page artifact. That
was safe only while the passphrase carried ~98 bits of entropy: the
ciphertext was world-readable, so a weak key would have been grindable
offline indefinitely. The passphrase is now a memorable one, which is fine
behind an authenticating proxy and would not be fine here — so the
ciphertext was removed rather than left in git with a weak key.

Source: https://github.com/EdwardoSunny/qd-bloom
