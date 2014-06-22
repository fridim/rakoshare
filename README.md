Rakoshare
=========

Rakoshare is a sharing tool to synchronize a folder on multiple
computers with no configuration.

It was inspired by Bittorrent Sync and aims to be an Open Source
alternative. Internally it reuses the Bittorrent protocol to build a
more dynamic protocol.

Rakoshare is forked off of
[Taipei-Torrent](https://github.com/jackpal/Taipei-Torrent), a pure go
Bittorrent application.

Current Status
--------------

Working but unstable. Anything, both in the implementation or the
protocol, can change at any time (although the general idea should
    remain the same)

Rakoshare might currently eat your data if you're not cautious.

Tested on Linux.

Development Roadmap
-------------------

*  Encryption

    * Encrypting the communications is of course expected, but something
      more interesting will be to encrypt data at-rest, so it can be
      shared with untrusted parties

*  Capabilities

    * The ids should have built-in capabilities, allowing holders to
      either being able to read and write, only read, or only store the
      content (without being able to decipher it)

*  Speed
    * Rakoshare is currently naive in how the folders are checked, there
      is room for improvement on this side

Download, Install, and Build Instructions
-----------------------------------------

1. Download and install the Go tools from http://golang.org

2. Use the "go" command to download, install, and build the Rakoshare
app:

    go get github.com/rakoo/rakoshare

Usage Instructions
------------------

1. Create a share id tuple:

  `$ ./rakoshare -gen`

  The result will be a list of different ids, each with a different
  capability:

  ```
  WriteReadStore: Zc3U2tGWsardUBxTcSPdSS5aPgwV3rakPe4xcVm6qbC8
  ReadStore: ENjn1seRA5cWRuFkpzsHuZu6mRDSBLgHviNH9xjgpCpiJg7jZzJ5BqurhTMn9aDJ678kvbkESeki9dS3sZEWEczZ
  Store: QcTRtY4E2E32k9tHx3X2tN8NLCPjYwWyXMhdh9R1dZ7jok5MJcv61zUGicj5KsbnbfGf5Cogb1xFf9JzyRq5H6s1
  ```

  or use one that someone gave you

2. If you receive content from someone else, make sure the directory is
   created:

  `$ mkdir ~/Doc`

3. Start the share with one of the ids you created earlier, or with one
   you were given:

  `$ rakoshare -fileDir ~/Doc -id <the_previous_id> -useLPD=true -useDHT=true`

4. The share is started. If you used a WriteReadStore id, then you have
   the capability of writing things that will be spread to everyone;
   otherwise you will only be able to receive from others.

For more info:

    rakoshare -help

Third-party Packages
--------------------

http://code.google.com/p/bencode-go - Bencode encoder/decoder

https://github.com/zeebo/bencode    - Another Bencode encoder/decoder

http://code.google.com/p/go-nat-pmp - NAT-PMP firewall client

https://github.com/hailiang/gosocks - SOCKS5 proxy support

https://github.com/nictuku/dht      - Distributed Hash Table

https://github.com/nictuku/nettools - Network utilities

Related Projects
----------------

https://github.com/jackpal/Taipei-Torrent is the base of rakoshare

Discussion
----------

Please open issues on the github tracker
(https://github.com/rakoo/rakoshare/issues), or discuss over the mailing
list: rakoshare served-by librelist.com
