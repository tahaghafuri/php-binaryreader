# binaryreader

binaryreader is a faster and more elegant alternative to PHP's pack/unpack functions for parsing binary data.

## Installation

### Pre-built Binaries
Pre-built binaries for Windows, macOS, and Linux are available in the [Releases](https://github.com/tahaghafuri/php-binaryreader/releases) section.

Supported configurations:
- PHP 8.2 and 8.3
- Non-Thread Safe (NTS)
- x64 architectures
- macOS, and Linux platforms

### PHP Configuration
Add the following line to your php.ini:
```ini
extension=binaryreader
```

## Usage
```php
$data = "..."; // your binary data
$read_little_endian = true;
$reader = new BinaryReader($data, $read_little_endian);
$text = $reader->readStringC();
```

## API Reference

### Constructor
```php
__construct(string $data, bool $littleEndian = false)
```

### Properties
- `endian: bool` - Get/set endianness (true = little, false = big)
- `position: int` - Get/set cursor position
- `size: int` - Get buffer size

### Methods

#### Basic Types
- `readBool(): bool`
- `readInt8(): int`
- `readUInt8(): int`
- `readInt16(): int`
- `readUInt16(): int`
- `readInt32(): int`
- `readUInt32(): int`
- `readInt64(): int`
- `readUInt64(): int`
- `readFloat(): float`
- `readDouble(): float`

#### Array Types
- `readBoolArray(?int $length = null): array`
- `readInt8Array(?int $length = null): array`
- `readUInt8Array(?int $length = null): string`
- `readInt16Array(?int $length = null): array`
- `readUInt16Array(?int $length = null): array`
- `readInt32Array(?int $length = null): array`
- `readUInt32Array(?int $length = null): array`
- `readInt64Array(?int $length = null): array`
- `readUInt64Array(?int $length = null): array`
- `readFloatArray(?int $length = null): array`
- `readDoubleArray(?int $length = null): array`

#### String Types
- `readStringC(): string` - Read null-terminated string
- `readString(?int $length = null): string` - Read length-prefixed string
- `readStringAligned(): string` - Read aligned string
- `readStringCArray(?int $length = null): array`
- `readStringArray(?int $length = null): array`
- `readStringAlignedArray(?int $length = null): array`

#### Utility Methods
- `align(int $boundary): int`
- `readVarInt(): int`
- `readLSB(?int $length = null): string`
