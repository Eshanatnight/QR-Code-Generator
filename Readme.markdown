QR Code generator library
=========================

Features
--------

Core features:

* Available in 6 programming languages, all with nearly equal functionality: Java, TypeScript/JavaScript, Python, Rust, C++, C
* Significantly shorter code but more documentation comments compared to competing libraries
* Supports encoding all 40 versions (sizes) and all 4 error correction levels, as per the QR Code Model 2 standard
* Output format: Raw modules/pixels of the QR symbol
* Detects finder-like penalty patterns more accurately than other implementations
* Encodes numeric and special-alphanumeric text in less space than general text
* Open source code under the permissive MIT License

Manual parameters:

* User can specify minimum and maximum version numbers allowed, then library will automatically choose smallest version in the range that fits the data
* User can specify mask pattern manually, otherwise library will automatically evaluate all 8 masks and select the optimal one
* User can specify absolute error correction level, or allow the library to boost it if it doesn't increase the version number
* User can create a list of data segments manually and add ECI segments

Optional advanced features (Java only):

* Encodes Japanese Unicode text in kanji mode to save a lot of space compared to UTF-8 bytes
* Computes optimal segment mode switching for text with mixed numeric/alphanumeric/general/kanji parts

More information about QR Code technology and this library's design can be found on the project home page.


Examples
--------


C++ language:

```c++
#include <string>
#include <vector>
#include "QrCode.hpp"
using namespace qrcodegen;

// Simple operation
QrCode qr0 = QrCode::encodeText("Hello, world!", QrCode::Ecc::MEDIUM);
std::string svg = toSvgString(qr0, 4);  // See QrCodeGeneratorDemo

// Manual operation
std::vector<QrSegment> segs =
    QrSegment::makeSegments("3141592653589793238462643383");
QrCode qr1 = QrCode::encodeSegments(
    segs, QrCode::Ecc::HIGH, 5, 5, 2, false);
for (int y = 0; y < qr1.getSize(); y++) {
    for (int x = 0; x < qr1.getSize(); x++) {
        (... paint qr1.getModule(x, y) ...)
    }
}
```

License
-------

[LICENSE: UNLICENSE](./LICENSE)
