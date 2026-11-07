# Cloakium Hongguo engine (jars)

Platform-independent jars from the bundled Hongguo desktop engine, used by the
`hongguo/` service in [quangvu30/cloakium](https://github.com/quangvu30/cloakium).

**Proprietary / private.** Do not redistribute. This repository exists so the Cloakium
Docker image can be built without a copy of the Hongguo app on the server.

- Engine version: `hongguo-helper-0.3.14`
- Captured: 2026-11-07 from `%LOCALAPPDATA%\HongguoWinUI\current\engine`
- Contents: `lib/*.jar` (37) + `signer/*.jar` (2), unmodified
- Size: ~16.8 MB

## Use in Cloakium

On the server, clone this repository and copy the two jar folders into the ignored
`hongguo/engine` directory (`hongguo/engine` already has a tracked `.gitkeep`, so clone
elsewhere):

```bash
git clone --depth 1 git@github.com:quangvu30/cloakium-hongguo-engine.git /tmp/hongguo-engine
cp -R /tmp/hongguo-engine/lib /tmp/hongguo-engine/signer hongguo/engine/
make hongguo
```

Or copy the two folders by hand. The Cloakium image installs the JRE and ffmpeg; JNA
unpacks its native library from `jna-jpms-*.jar`. Do **not** add `runtime/`, `ffmpeg/`
or `lib/native/` from a Windows install.

## Integrity

```bash
sha256sum -c SHA256SUMS
```

`manifest.json` records the source and the exact file count/size.
