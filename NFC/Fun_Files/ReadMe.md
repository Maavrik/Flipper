**BIG CHANGES COMING TO THIS SOON! Updated info as the below is no longer (entirely) true.**

Some files that are fun to use. Starting to get a better idea on the structure (Flipper format) of NFC files and payloads.

Example using the [RickRoll.nfc](https://github.com/UberGuidoZ/Flipper/blob/main/NFC/Fun_Files/RickRoll.nfc) file. Leave the data in pages 1 through 6 alone (though not always true, but it is for YouTube links.)

Page 7: 79 6F 75 74 <br>
Page 8: 75 2E 62 65 <br>
Page 9: 2F 64 51 77 <br>
Page 10: 34 77 39 57 <br>
Page 11: 67 58 63 51 <br>

This is simply the YouTube "[share](https://support.google.com/youtube/answer/57741)" link encoded into HEX and split into 4 byte chunks. See for yourself...

HEX from above: 79 6F 75 74 75 2E 62 65 2F 64 51 77 34 77 39 57 67 58 63 51 <br>
[Converted](https://www.binaryhexconverter.com/hex-to-ascii-text-converter): youtu.be/dQw4w9WgXcQ

The last byte in page 6 (0x04) defines what type of encoding ([data sheet](https://www.nxp.com/docs/en/data-sheet/NTAG213_215_216.pdf) and [URI identifier codes](https://learn.adafruit.com/adafruit-pn532-rfid-nfc/ndef)). To convert your link to HEX, use anything such as an [online tool](https://onlinehextools.com/convert-ascii-to-hex).

One limitation is the URL will be truncated if it goes beyond page 11! If your URL is less than exact, pad it with 00, making sure page 12 stays as "FE 00 00 00". Note that [TinyURL](https://tinyurl.com/app) links appear to fit well and conversion/use is free. If your link doesn't launch automatically when scanned, try using a different URI identifier.

Acknowledgements: RogueMaster | cyanic | Null Silvry | Equip | DDVL (for discussions, testing, and any files.)

Value&nbsp;&nbsp;&nbsp;&nbsp;Protocol &nbsp;&nbsp;&nbsp;&nbsp;([SOURCE](https://learn.adafruit.com/adafruit-pn532-rfid-nfc/ndef))<br>
------&nbsp;&nbsp;&nbsp;&nbsp;---------- <br>
0x00&nbsp;&nbsp;&nbsp;&nbsp; No prepending is done ... the entire URI is contained in the URI Field <br>
0x01&nbsp;&nbsp;&nbsp;&nbsp; http://www. <br>
0x02&nbsp;&nbsp;&nbsp;&nbsp; https://www. <br>
0x03&nbsp;&nbsp;&nbsp;&nbsp; http:// <br>
0x04&nbsp;&nbsp;&nbsp;&nbsp; https:// <br>
0x05&nbsp;&nbsp;&nbsp;&nbsp; tel: <br>
0x06&nbsp;&nbsp;&nbsp;&nbsp; mailto: <br>
0x07&nbsp;&nbsp;&nbsp;&nbsp; ftp://anonymous:anonymous@ <br>
0x08&nbsp;&nbsp;&nbsp;&nbsp; ftp://ftp. <br>
0x09&nbsp;&nbsp;&nbsp;&nbsp; ftps:// <br>
0x0A&nbsp;&nbsp;&nbsp;&nbsp; sftp:// <br>
0x0B&nbsp;&nbsp;&nbsp;&nbsp; smb:// <br>
0x0C&nbsp;&nbsp;&nbsp;&nbsp; nfs:// <br>
0x0D&nbsp;&nbsp;&nbsp;&nbsp; ftp:// <br>
0x0E&nbsp;&nbsp;&nbsp;&nbsp; dav:// <br>
0x0F&nbsp;&nbsp;&nbsp;&nbsp; news: <br>
0x10&nbsp;&nbsp;&nbsp;&nbsp; telnet:// <br>
0x11&nbsp;&nbsp;&nbsp;&nbsp; imap: <br>
0x12&nbsp;&nbsp;&nbsp;&nbsp; rtsp:// <br>
0x13&nbsp;&nbsp;&nbsp;&nbsp; urn: <br>
0x14&nbsp;&nbsp;&nbsp;&nbsp; pop: <br>
0x15&nbsp;&nbsp;&nbsp;&nbsp; sip: <br>
0x16&nbsp;&nbsp;&nbsp;&nbsp; sips: <br>
0x17&nbsp;&nbsp;&nbsp;&nbsp; tftp: <br>
0x18&nbsp;&nbsp;&nbsp;&nbsp; btspp:// <br>
0x19&nbsp;&nbsp;&nbsp;&nbsp; btl2cap:// <br>
0x1A&nbsp;&nbsp;&nbsp;&nbsp; btgoep:// <br>
0x1B&nbsp;&nbsp;&nbsp;&nbsp; tcpobex:// <br>
0x1C&nbsp;&nbsp;&nbsp;&nbsp; irdaobex:// <br>
0x1D&nbsp;&nbsp;&nbsp;&nbsp; file:// <br>
0x1E&nbsp;&nbsp;&nbsp;&nbsp; urn:epc:id: <br>
0x1F&nbsp;&nbsp;&nbsp;&nbsp; urn:epc:tag: <br>
0x20&nbsp;&nbsp;&nbsp;&nbsp; urn:epc:pat: <br>
0x21&nbsp;&nbsp;&nbsp;&nbsp; urn:epc:raw: <br>
0x22&nbsp;&nbsp;&nbsp;&nbsp; urn:epc: <br>
0x23&nbsp;&nbsp;&nbsp;&nbsp; urn:nfc: <br>
