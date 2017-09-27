# ⚠️️ DISCLAIMER ⚠️️

This project is...
* not actively maintained
* not actively supported and is not guaranteed to be compatible with all versions of Clair
* intended for local usage only and does not follow the best practices for production usage of Clair

# analyze-local-images

This is a basic tool that enables quick analysis of local Docker images with [Clair](https://github.com/coreos/clair).

## Install

First install [Go](https://golang.org/doc/install) and [glide](https://glide.sh) and then run the following commands:

    $ git clone git@github.com:coreos/analyze-local-images.git $HOME/analyze-local-images-gopath/src/github.com/coreos/analyze-local-images
    $ export GOPATH=$HOME/analyze-local-images-gopath
    $ cd $HOME/analyze-local-images-gopath/src/github.com/coreos/analyze-local-images
    $ glide install
    $ go install github.com/coreos/analyze-local-images

## Usage

### Clair is a local process or inside of a container running on my current machine

```
analyze-local-images <Docker Image>
```


### Clair is running inside of container on a local VM (e.g. Docker For Mac)

```shell
analyze-local-images -endpoint "http://<CLAIR-IP-ADDRESS>:6060" -my-address "<MY-IP-ADDRESS>" <Docker Image>
```
我的例子：
clair地址：192.168.10.11
my-address：192.168.10.34
```shell
./analyze-local-images -endpoint "http://192.168.10.11:6060" -my-address "192.168.10.34" nginx:1.11.5
```

执行结果：
```shell
2017/09/27 03:41:30 Saving nginx:1.11.5 to local disk (this may take some time)
2017/09/27 03:41:34 Retrieving image history
2017/09/27 03:41:35 Setting up HTTP server (allowing: 192.168.10.11)
2017/09/27 03:41:35 Analyzing 8 layers... 
2017/09/27 03:41:35 Analyzing 1f2a121fc3e47c2a96bbb719774b1ba01560ff7294dc2fb12dfd9db0381d0b98
2017/09/27 03:41:35 Analyzing 8d8b679a55bc4cde7d7f104d3fd993d860c22accd3d7c094baa0c7f68d6c1373
2017/09/27 03:41:35 Analyzing a6c255f07aa81442a470ee69f00ac8ed782c9224a39ac8211d400736182054d5
2017/09/27 03:41:35 Analyzing 688deb3ebd319308ca2270ed1d3766bd3fa2c65fd6bfa812695d7ada411c9288
2017/09/27 03:41:35 Analyzing a906acdecdc61bc8e17fe95d0681f2d17c04076867d0a91e5188966714cb946b
2017/09/27 03:41:35 Analyzing 49c4ad89029f519f90c5060bb0e25446daa557ab377054b5d12b116d69d84354
2017/09/27 03:41:35 Analyzing 4205260e35c318813aaa03c5a537733693f0b265ba7b464f07f92b47ee5e1e17
2017/09/27 03:41:35 Analyzing ef068b58f0cd1ba3e391f5a916004e9181fa71334430633b4d05b4277e145c91
2017/09/27 03:41:35 Retrieving image's vulnerabilities
Clair report for image nginx:1.11.5 (2017-09-27 03:41:35.484442466 +0000 UTC)
CVE-2017-0393 (High)
    A denial of service vulnerability in libvpx in Mediaserver could enable a remote
    attacker to use a specially crafted file to cause a device hang or reboot.
    This issue is rated as High due to the possibility of remote denial of service.
    Product: Android. Versions: 4.4.4, 5.0.2, 5.1.1, 6.0, 6.0.1, 7.0, 7.1. Android
    ID: A-30436808.

    Package:       libvpx @ 1.3.0-3
    Link:          https://security-tracker.debian.org/tracker/CVE-2017-0393
    Layer:         a906acdecdc61bc8e17fe95d0681f2d17c04076867d0a91e5188966714cb946b

CVE-2016-3881 (High)
    The decoder_peek_si_internal function in vp9/vp9_dx_iface.c in libvpx in
    mediaserver in Android 4.x before 4.4.4, 5.0.x before 5.0.2, 5.1.x before 5.1.1,
    6.x before 2016-09-01, and 7.0 before 2016-09-01 allows remote attackers to
    cause a denial of service (buffer over-read, and device hang or reboot) via a
    crafted media file, aka internal bug 30013856.

    Package:       libvpx @ 1.3.0-3
    Link:          https://security-tracker.debian.org/tracker/CVE-2016-3881
    Layer:         a906acdecdc61bc8e17fe95d0681f2d17c04076867d0a91e5188966714cb946b

CVE-2016-4448 (High)
    Format string vulnerability in libxml2 before 2.9.4 allows attackers to have
    unspecified impact via format string specifiers in unknown vectors.

    Package:       libxml2 @ 2.9.1+dfsg1-5+deb8u3
    Link:          https://security-tracker.debian.org/tracker/CVE-2016-4448
    Layer:         a906acdecdc61bc8e17fe95d0681f2d17c04076867d0a91e5188966714cb946b

CVE-2016-10164 (High)
    Multiple integer overflows in libXpm before 3.5.12, when a program requests
    parsing XPM extensions on a 64-bit platform, allow remote attackers to cause a
    denial of service (out-of-bounds write) or execute arbitrary code via (1) the
    number of extensions or (2) their concatenated length in a crafted XPM file,
    which triggers a heap-based buffer overflow.

    Package:       libxpm @ 1:3.5.11-1
    Fixed version: 1:3.5.12-0+deb8u1
    Link:          https://security-tracker.debian.org/tracker/CVE-2016-10164
    Layer:         a906acdecdc61bc8e17fe95d0681f2d17c04076867d0a91e5188966714cb946b

CVE-2017-5225 (High)
    LibTIFF version 4.0.7 is vulnerable to a heap buffer overflow in the
    tools/tiffcp resulting in DoS or code execution via a crafted BitsPerSample
    value.

    Package:       tiff @ 4.0.3-12.3+deb8u1
    Fixed version: 4.0.3-12.3+deb8u3
    Link:          https://security-tracker.debian.org/tracker/CVE-2017-5225
    Layer:         a906acdecdc61bc8e17fe95d0681f2d17c04076867d0a91e5188966714cb946b

```
Clair needs filesystem access to the image files.
If you run Clair locally, this tool will store the files in the system's temporary folder and Clair will find them there.
It means if Clair is running in Docker, the host's temporary folder must be mounted in the Clair's container.
If you run Clair remotely, this tool will run a small HTTP server to let Clair downloading them.
It listens on the port 9279 and allows a single host: Clair's IP address, extracted from the `-endpoint` parameter.
The `my-address` parameters defines the IP address of the HTTP server that Clair will use to download the images.
With boot2docker, these parameters would be `-endpoint "http://192.168.99.100:6060" -my-address "192.168.99.1"`.

As it runs an HTTP server and not an HTTP**S** one, be sure to **not** expose sensitive data and container images.
