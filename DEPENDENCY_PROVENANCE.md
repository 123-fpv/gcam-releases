# Additional dependency provenance

The FreeImage DLL bundled by the OCP wheel reports version 3.18.0 through the constants used by its exported FreeImage_GetVersion function (read-only PE inspection, without loading the DLL). SHA256: 670ad2bf7cf19d05a739bc7fc508d27205dade420375a475c0f9437096a37850.

FreeImage3180-source.zip is the official upstream archive, verified against SHA256 f41379682f9ada94ea7b34fe86bf9ee00935a3147be41b6569c9605a53e438fd published by the conda-forge packaging recipe. The release also includes a recipe snapshot at commit 41097b4e51f069a1ec27ee7cf30387aa49d6d62f. This snapshot provides packaging context and patches; the exact conda build number and patch set that produced the bundled DLL have not been independently established. It must not be described as a verified reproducible build of that binary.

The release retains upstream license texts and source references and supplies matching upstream base-version sources. These checks are not a legal opinion, a complete transitive dependency legal audit, or a guarantee that every binary can be reproduced byte-for-byte.
