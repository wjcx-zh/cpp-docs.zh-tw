---
title: ATL 編碼方式參考
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: a284645030b5bcdb30b72d7df92231680efb36b4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831888"
---
# <a name="atl-encoding-reference"></a>ATL 編碼方式參考

在中找到的程式碼可支援各種常見網際網路標準的編碼，例如 uuencode、十六進位和 UTF8 *`atlenc.h`* 。

### <a name="functions"></a>函式

| 函式 | 使用案例 |
|--|--|
| [AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue) | 呼叫此函式可取得十六進位的數值。 |
| [AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode) | 將已編碼為十六進位文字的資料字串解碼，例如先前對 [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)的呼叫。 |
| [AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength) | 呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。 |
| [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode) | 呼叫此函式可將一些資料編碼為十六進位文字字串。 |
| [AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength) | 呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。 |
| [AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8) | 呼叫此函式可將 Unicode 字串轉換為 UTF-8。 |
| [BEncode](reference/atl-text-encoding-functions.md#bencode) | 呼叫此函式可使用 "B" 編碼方式轉換部分資料。 |
| [BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength) | 呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。 |
| [EscapeXML](reference/atl-text-encoding-functions.md#escapexml) | 呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。 |
| [GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars) | 呼叫此函式可取得字串中的擴充字元數目。 |
| [IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar) | 呼叫此函式，以找出指定的字元是否為擴充的字元 (小於32、大於126，而不是定位字元、換行字元或換行字元)  |
| [QEncode](reference/atl-text-encoding-functions.md#qencode) | 呼叫此函式可使用 "Q" 編碼方式轉換部分資料。 |
| [QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength) | 呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。 |
| [QPDecode](reference/atl-text-encoding-functions.md#qpdecode) | 解碼以引號可列印格式編碼的資料字串，例如先前對 [QPEncode](reference/atl-text-encoding-functions.md#qpencode)的呼叫。 |
| [QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength) | 呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。 |
| [QPEncode](reference/atl-text-encoding-functions.md#qpencode) | 呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。 |
| [QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength) | 呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。 |
| [UUDecode](reference/atl-text-encoding-functions.md#uudecode) | 將已 uuencode 編碼的資料字串解碼，例如先前對 [UUEncode](reference/atl-text-encoding-functions.md#uuencode)的呼叫。 |
| [UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength) | 呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。 |
| [UUEncode](reference/atl-text-encoding-functions.md#uuencode) | 呼叫此函式可對一些資料進行 UUENCODE 編碼。 |
| [UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength) | 呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。 |

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)
