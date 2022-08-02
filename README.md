# s3simple

s3simple is a small bash script/function for fetching files from and putting
files into Amazon's S3 service. It has only two dependencies (curl and
openssl), both of which are usually pre-installed or easily available on most
modern unixes.

## Usage

1. Download the [s3simple](s3simple) script somewhere.
2. Set `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` and optionally `AWS_SESSION_TOKEN` environment variables.
3. Run `s3simple` with a method, an `s3://` url and, optionally, a local filename.

For example:

    export AWS_ACCESS_KEY_ID=AKxxx
    export AWS_SECRET_ACCESS_KEY=zzzz
    # optionally provide a temporary session token
    export AWS_SESSION_TOKEN=wwww...

    # get a file
    ./s3simple get s3://mybucket/myfile.txt myfile.txt

    # put a file
    ./s3simple put s3://mybucket/foo.txt foo.txt

    # get a file and pipe to tar
    s3simple get s3://mybucket/foo.tgz | tar -zx

You can also copy the s3simple function into your bash scripts.

## License

MIT license, see LICENSE.txt for details.
