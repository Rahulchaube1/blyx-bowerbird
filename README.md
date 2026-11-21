<img src="assets/logo.png" width="112" height="112" alt="Bowerbird logo">

# Bowerbird

Decide whether a proposed numeric-core dependency upgrade fits a declared version range. This Blyx workflow framework is part of the packaging and code quality collection.

String sorting places 1.10 before 1.2. Check numeric ordering and the consumer's upper bound separately. [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-bowerbird.git
cd blyx-bowerbird
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-bowerbird) · [Package page](https://www.blyx-lang.space/packages/bowerbird) · [Handbook](https://doc.blyx-lang.space/guide/bowerbird)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-bowerbird.git vendor/bowerbird
```

```blyx
use vendor::bowerbird::bowerbird;

fn main() {
    let installed = [1, 2, 9];
    let candidate = [1, 10, 0];
    let lower = [1, 0, 0];
    let upper = [2, 0, 0];
    let result = bowerbird_upgrade(installed, candidate, lower, upper);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
1
1
1
1
```

## API

`bowerbird_upgrade(installed, candidate, lower, upper)`

Returns [allowed upgrade, candidate versus installed, major/minor/patch index changed, within range]. Equal versions are allowed. This release handles numeric cores and explicit bounds. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| installed | Vector of values, each a nonnegative exact integer |
| candidate | Vector of values, each a nonnegative exact integer |
| lower | Vector of values, each a nonnegative exact integer |
| upper | Vector of values, each a nonnegative exact integer |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "1,2,9" "1,10,0" "1,0,0" "2,0,0"
```

## Libraries

- [SemVerCore](https://github.com/Rahulchaube1/blyx-semvercore/tree/v0.1.0) — Compare two numeric semantic-version cores lexicographically.
- [VersionBand](https://github.com/Rahulchaube1/blyx-versionband/tree/v0.1.0) — Check membership of a numeric-version core in a half-open dependency interval.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-bowerbird/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
