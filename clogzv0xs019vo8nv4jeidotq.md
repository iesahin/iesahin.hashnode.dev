---
title: "perl error building rust-openssl with maturin, ubuntu and manylinux"
datePublished: Thu Nov 02 2023 09:19:26 GMT+0000 (Coordinated Universal Time)
cuid: clogzv0xs019vo8nv4jeidotq
slug: perl-error-building-rust-openssl-with-maturin-ubuntu-and-manylinux
canonical: https://emresahin.net/perl-error-building-rust-openssl-with-maturin-ubuntu-and-manylinux/

---

While building [Python packages for Xvc](https://github.com/iesahin/xvc.py) with maturin, I was receiving in Github Actions CI for Linux packages.

    Can't locate IPC/Cmd.pm in @INC (@INC contains: /home/runner/work/xvc.py/xvc.py/target/x86_64-unknown-linux-gnu/release/build/openssl-sys-844a96d66ae533b1/out/openssl-build/build/src/util/perl /usr/local/lib64/perl5 /usr/local/share/perl5 /usr/lib64/perl5/vendor_perl /usr/share/perl5/vendor_perl /usr/lib64/perl5 /usr/share/perl5 . /home/runner/work/xvc.py/xvc.py/target/x86_64-unknown-linux-gnu/release/build/openssl-sys-844a96d66ae533b1/out/openssl-build/build/src/external/perl/Text-Template-1.56/lib)
    

The issue seemed to be a missing `perl` package. Building `rust-openssl` now seems to require `perl-core` package.

I added a `apt-get update && apt-get install perl-core` to the CI configuration. But that didn't work.

Because, [as this Github issue comment said](https://github.com/sfackler/rust-openssl/issues/2036#issuecomment-1724324145) maturin with its `manylinux` support uses different kind of Docker containers to build the packages. We must detect if it's a CentOS or Debian based container and install missing packages.

_Building wheels_ step in the config should be similar to:

          - name: Build wheels
            uses: PyO3/maturin-action@v1
            with:
              target: ${{ matrix.target }}
              manylinux: auto
              args: --release --out dist
              before-script-linux: |
                # If we're running on rhel centos, install needed packages.
                if command -v yum &> /dev/null; then
                    yum update -y && yum install -y perl-core openssl openssl-devel pkgconfig libatomic
    
                    # If we're running on i686 we need to symlink libatomic
                    # in order to build openssl with -latomic flag.
                    if [[ ! -d "/usr/lib64" ]]; then
                        ln -s /usr/lib/libatomic.so.1 /usr/lib/libatomic.so
                    fi
                else
                    # If we're running on debian-based system.
                    apt update -y && apt-get install -y libssl-dev openssl pkg-config
                fi
    

This will the specified script before running the maturin build command in the container and add missing packages.