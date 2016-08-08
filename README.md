# README

[RFC-5415](https://tools.ietf.org/html/rfc5415) and [RFC-5416](https://tools.ietf.org/html/rfc5416) compliant CAPWAP WTP (and AC) implementation.

This fork is currently focusing on the WTP side only.

## STATUS

NOTE: The WTP has been ported to libev, the AC has not been adjusted and is therefor broken for the moment.

### WTP tested and working features:

* 802.11b
* 802.11g
* 802.11a
* WMM/WME (mostly)
* Local MAC
* single radio, single WLAN mode
* 802.11n ([draft-ietf-opsawg-capwap-extension-06](https://tools.ietf.org/html/draft-ietf-opsawg-capwap-extension-06))
* WPA2-PSK

Only cards with cfg80211 netlink API are supported. The following devices
have been tested:

* Atheros AR9280 (Compex WLE200NX)
* Mediatek MT7602E, MT7612E (ZBT WG2626, ALL-WR1200AC_WRT)

### Planned WTP features:

* WPA2 Enterprise
* 802.11r - BSS fast transition
* Hybrid-MAC ([RFC-7494](https://tools.ietf.org/html/rfc7494))

## INSTALLATION

### Requirements

NOTE: To run WTP you must have a wireless card that has Linux driver based on the
      Generic IEEE 802.11 Networking Stack (mac80211).

* Linux 4.4 or newer
* automake 1.9 or newer
* autoconf
* libconfig-dev
* libjson0-dev
* libnl-dev
* libev-dev
* libtool
* libxml2-dev
* wolfssl 3.8 or newer


### Build

WolfSSL:

    ./configure --enable-dtls --enable-ipv6 --enable-aesgcm \
                --enable-aesccm --enable-aesni --enable-poly1305 \
                --enable-ecc --enable-ecc25519 --enable-chacha \
                --enable-supportedcurves --enable-dh --enable-psk \
                --disable-des3 --disable-arc4 --prefix=/usr/
    make
    make install

SmartCAPWAP:

    autoreconf -f -i
    ./configure --disable-ac
    make
    make install
