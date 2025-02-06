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

1. **Install Rust and ESP32 Toolchain**:
   ```sh
   rustup install stable
   rustup target add riscv32imc-unknown-none-elf # For ESP32-C3
   cargo install cargo-espflash
   ```

2. **Clone the repository**:
   ```sh
   git clone https://github.com/yourusername/tpm2-spi-rust
   cd tpm2-spi-rust
   ```

3. **Build and flash the firmware**:
   ```sh
   cargo espflash /dev/ttyUSB0
   ```

4. **Run the example program**:
   ```sh
   cargo run --example tpm_test
   ```

## Example Code
Here's a simple example to send a TPM command over SPI:
```rust
use esp_hal::spi::Spi;
use embedded_hal::blocking::spi::Transfer;

fn tpm_send_command(spi: &mut Spi, command: &[u8]) -> Result<Vec<u8>, &'static str> {
    let mut response = vec![0; command.len()];
    spi.transfer(&mut response, command).map_err(|_| "SPI Transfer Failed")?;
    Ok(response)
}
```

## Roadmap
- [ ] Implement full TPM command set
- [ ] Add support for more TPM modules
- [ ] Improve documentation and add more examples

## License
This project is licensed under the MIT License. See `LICENSE` for more details.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request if you have improvements or bug fixes.