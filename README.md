# hashlib-additional - Additional hashlib-compatible hashing digests

* https://pypi.org/project/hashlib-additional/
* https://github.com/rfinnie/python-hashlib-additional

## About

This module packages several additional hashing digests in a hashlib-compatible format.
It implements the following digests:

* null - Always outputs null byte "hashes", with a configurable digest_size
* random - Always outputs random "hashes", with a configurable digest_size
* crc32 - CRC32 digest, 4 byte digest_size
* adler32 - Adler-32 digest, 4 byte digest_size
* fletcher16 - Fletcher 8-bit implementation, 2 byte digest_size
* fletcher32 - Fletcher 16-bit implementation, 4 byte digest_size
* fletcher64 - Fletcher 32-bit implementation, 8 byte digest_size
* cksum - Unix cksum checksum, 4 byte digest_size
* sysv - Unix System V checksum, 2 byte digest_size
* bsd - BSD checksum, 2 byte digest_size
* udp - UDP checksum, 2 byte digest_size
* twoping - 2ping checksum, 2 byte digest_size

Unless stated, all digest outputs are big-endian (network byte order).

"sysv", "bsd" and "cksum" results are just the hash (in byte form), even though technically the full checksum (as returned by "sum" and "cksum") is comprised of the decimal hash and input length, separated by a space.

## Example

```
>>> import hashlib_additional
>>> digest = hashlib_additional.new('crc32')
>>> digest.update(b'foo')
>>> digest.hexdigest()
'8c736521'

>>> hashlib_additional.algorithms_available
{'adler32', 'bsd', 'cksum', 'crc32', 'fletcher16', 'fletcher32',
 'fletcher64', 'null', 'random', 'sysv', 'twoping', 'udp'}

>>> digest = hashlib_additional.twoping(b'bar')
>>> digest.digest()
b'+\x9e'
```

## License

Copyright (c) 2019-2020 Ryan Finnie

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

