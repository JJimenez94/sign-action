# Code sign a file

This action signs `.nupkg` files and files that are supported by `signtool.exe` with a code signing certificate. This action only works on Windows and that means it should run on `windows-latest`.

## Inputs

### `certificate`

**Required** The base64 encoded certificate.

### `certificate-password`

**Required** The password for the certificate

### `certificate-sha1`

**Required** The SHA-1 value of the certificate

### `folder`

**Required** The folder that contains the files to sign.

### `recursive`

**Optional** Recursively search for supported files.

## Example usage

```
runs-on: windows-latest
steps:
  uses: MichaelVoelkel/code-sign-action@v1
  with:
    certificate: '${{ secrets.CERTIFICATE }}'
    certificate-password: '${{ secrets.CERTIFICATE_PASSWORD }}'
    certificate-sha1: '${{ secrets.CERTIFICATE_SHA1 }}'
    folder: 'files'
    recursive: true
```