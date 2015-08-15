# chromium-vaapi
PKGBUILD for chromium stable with VAAPI support for Linux enabled, working with the latest version of Chromium Stable.

VA-API related patch is based on http://bazaar.launchpad.net/~saiarcot895/chromium-browser/chromium-browser.trusty.beta/view/200/debian/patches/enable_vaapi_on_linux.diff

But that patch above is **no longer working** under latest version of Chromium. So I did some modification to make it work.

Other patches are from ArchLinux's official repository, so is the PKGBUILD.

This repository will follow up the latest version of Chromium in ArchLinux repository while making VA-API based Video decoding working under Linux.

## Working Functions

- HTML5 H.264 Video Decode
- Flash `StageVideo` object Video Decode

## Not Working Functions

- HTML5 VP8/9 Video Decode (install chrome extension h264ify for Youtube)
- Flash `Video` object Video Decode (Adobe doesn't have this support for pepper Flash in any platform)

## Working Sites

- Youtube (with h264ify installed)
- Youtube Flash
- Bilibili (with HTML5 player extension, but danmaku will use medium to high cpu under HTML5)
- Youku (right click the player, and click enable GPU acceleration)

## Not Working Sites

- Hulu (using `Video` object)
- Bilibili (using `Video` object)
- Youtube (Youtube sends VP8/9 codec video to Chrome by default)

## Use `Video` object hardware acceleration under Linux (FireFox with NVIDIA Cards)

If you're using NVIDIA GPUs, try wine-staging(with dxva2 enabled) and pipelight under Firefox to run the non-pepper version of Flash Player for Windows(which is the only version with `Video` object hardware decoding) under Linux.
Sites like Bilibili (with original official player) will work with pipelight installation.
Using Intel Cards in wine-staging with dxva2 enabled will lead to GPU hanging.
