# Code sign a file

This action signs files that are supported by `signtool.exe` with a code signing certificate. This action only works on Windows _but_ dynamically finds `signtool` and should therefore run with self-hosted runners that have it. Also, this action allows to provide the password for the base64-encoded `pfx` file and its SHA1 hash (also called thumbprint in Windows). Other tools either have a fixed path in the code or do not allow to enter password or hash.

## Inputs

### `certificate`

**Required** The base64 encoded certificate.

### `certificate-password`

**Required** The password for the certificate

### `certificate-sha1`

**Required** The SHA-1 value of the certificate

### `folder`

**Required** The folder that contains the files to sign.

### `extensions`

**Optional** List of files to sign, this should be a string separated by comma.

### `recursive`

**Optional** Recursively search for supported files.

## Example usage

```
runs-on: windows-latest
steps:
  uses: JJimenez94/sign-action@v1.1
  with:
    certificate: '${{ secrets.CERTIFICATE }}'
    certificate-password: '${{ secrets.CERTIFICATE_PASSWORD }}'
    certificate-sha1: '${{ secrets.CERTIFICATE_SHA1 }}'
    folder: 'files'
    extensions: 'exe,dll'
    recursive: true
```
