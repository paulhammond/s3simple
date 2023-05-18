# s3simple

s3simple is a small bash script/function for fetching objects from and putting
files into Amazon’s S3 Simple Storage service.

It is intended for use in early bootstrapping of a system, and it has only two
dependencies (curl and openssl), both of which are usually pre-installed or
easily available as packages. If the [AWS CLI][] is available you should use it
instead of this script.

Note that s3simple uses [S3 Signature V2][] which was [deprecated] in 2019. As
a result it only works with buckets created before June 2020, in regions that
existed before 2014. Support for [S3 Signature V4][] in bash is probably
possible, but it is not implemented here.

[AWS CLI]: https://aws.amazon.com/cli/
[S3 Signature V2]: https://docs.aws.amazon.com/general/latest/gr/signature-version-2.html
[S3 Signature V4]: https://docs.aws.amazon.com/AmazonS3/latest/API/sig-v4-authenticating-requests.html
[deprecated]: https://aws.amazon.com/blogs/aws/amazon-s3-update-sigv2-deprecation-period-extended-modified/

## Usage

1. Download the [s3simple](s3simple) script somewhere.
2. Set `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` and optionally
`AWS_SESSION_TOKEN` and `S3_SERVER` environment variables.
3. Run `s3simple` with a method, an `s3://` url and, optionally, a local
filename.

For example:

    export AWS_ACCESS_KEY_ID=AKxxx
    export AWS_SECRET_ACCESS_KEY=zzzz
    # optionally provide a temporary session token
    export AWS_SESSION_TOKEN=wwww...
    # optionally provide an S3 server address
    export S3_SERVER=http://my-s3.example.com:9000

    # get a file
    ./s3simple get s3://mybucket/myfile.txt myfile.txt

    # fetch metadata about an object
    ./s3simple head s3://mybucket/myfile.txt

    # put a file
    ./s3simple put s3://mybucket/foo.txt foo.txt

    # get a file and pipe to tar
    s3simple get s3://mybucket/foo.tgz | tar -zx

You are encouraged to copy the s3simple function into your bash scripts and edit
it to suit your needs.

## License

MIT license, see LICENSE.txt for details.
