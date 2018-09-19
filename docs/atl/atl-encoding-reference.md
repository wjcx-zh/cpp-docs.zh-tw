---
title: ATL 編碼參考 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e34b6d3764c0096e30c0e1f27c36194fd5d44110
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088822"
---
# <a name="atl-encoding-reference"></a>ATL 編碼方式參考

Atlenc.h 中找到的程式碼支援各種常見的網際網路標準，例如 uuencode、 十六進位和 UTF8 編碼方式。

### <a name="functions"></a>函式

|||
|-|-|
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|呼叫此函式可取得十六進位的數值。|
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|將已編碼為十六進位的文字，例如由先前呼叫的資料字串解碼[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)。|
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。|
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|呼叫此函式可將一些資料編碼為十六進位文字字串。|
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|呼叫此函式可將 Unicode 字串轉換為 UTF-8。|
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|呼叫此函式可使用 "B" 編碼方式轉換部分資料。|
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。|
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|呼叫此函式可取得字串中的擴充字元數目。|
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|呼叫此函式，了解所指字元是否為擴充字元 (小於 32、大於 126，而且不是定位字元、換行字元或歸位字元)|
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|呼叫此函式可使用 "Q" 編碼方式轉換部分資料。|
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|將已編碼為 quoted-printable 格式，例如由先前呼叫的資料字串解碼[QPEncode](reference/atl-text-encoding-functions.md#qpencode)。|
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。|
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。|
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|將已使用 uuencode 編碼例如由先前呼叫的資料字串解碼[UUEncode](reference/atl-text-encoding-functions.md#uuencode)。|
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。|
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|呼叫此函式可對一些資料進行 UUENCODE 編碼。|
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)

