# TPM2(rev. 1.59) SPI Driver for ESP32 in Rust

This project provides a Rust-based SPI driver for ESP32 (and similar microcontrollers) to communicate with a TPM 2.0 module. The goal is to enable secure cryptographic operations and key storage on embedded devices using a Trusted Platform Module (TPM).

## Features
- **SPI Communication**: Implements SPI-based communication between the ESP32 and a TPM 2.0 module.
- **TPM Command Handling**: Supports basic TPM commands such as `StartUp`, `SelfTest`, and `GetCapability`.
- **Asynchronous Execution**: Uses Rust's async capabilities for efficient non-blocking operations.
- **Error Handling**: Implements error handling for SPI communication failures and TPM response parsing.

## Hardware Requirements
- **ESP32 or ESP32-C3/S3** (or any similar Rust-compatible microcontroller with SPI support)
- **TPM 2.0 Module** (e.g., Infineon SLB9670, Nuvoton, or STMicroelectronics TPMs)
- **SPI Connections**:
  - **MOSI** → TPM `MOSI`
  - **MISO** → TPM `MISO`
  - **SCK** → TPM `CLK`
  - **CS** → TPM `CS`

## Software Requirements
- Rust with `esp32-hal`
- `embedded-hal` for SPI communication
- `tpm2-tss` (if using a higher-level TPM interface)
- `cargo-espflash` (for flashing firmware to ESP32)

## Installation & Usage

1. **TODO**:
   ```sh
   cargo install cargo-generate
   //https://github.com/esp-rs/esp-template
   https://www.reddit.com/r/embedded/comments/11hef6p/embedded_rust_tutorials_on_the_esp32c3/
   ```

2. **TODO**:
   ```sh
   cargo generate esp-rs/esp-template
   ```


## Example Code
Here's a simple example to send a TPM command over SPI:
```rust
TODO
```

## Roadmap
- [ ] Implement full TPM command set
- [ ] Add support for more TPM modules
- [ ] Improve documentation and add more examples

## License
This project is licensed under the MIT License. See `LICENSE` for more details.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request if you have improvements or bug fixes.