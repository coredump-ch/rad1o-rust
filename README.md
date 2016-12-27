# Rust Rad1o

HW: NXP LPC4330
https://rad1o.badge.events.ccc.de/more_hardware

## Generate HW interface code from SVD

Download SVD from https://www.lpcware.com/content/nxpfile/lpc43sxx-svd-file

    svd2rust -i LPC43xx_43Sxx.svd gpio > src/peripheral/gpio.rs
    rustfmt src/peripheral/gpio.rs

## Building

    xargo build --target thumbv7em-none-eabihf -v --release
    arm-none-eabi-objcopy --strip-unneeded -O binary \
        target/thumbv7em-none-eabihf/release/logo \
        target/thumbv7em-none-eabihf/release/logo.c1d

### Inspect build

    arm-none-eabi-objdump -SD target/thumbv7em-none-eabihf/release/logo | less
