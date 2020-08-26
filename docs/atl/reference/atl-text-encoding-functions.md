---
title: ATL 文字編碼函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 330a73e0d41bf384a799635d5f2e6f09f7e3dd03
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833851"
---
# <a name="atl-text-encoding-functions"></a>ATL 文字編碼函式

這些函數支援文字編碼和解碼。

|函式|描述|
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|呼叫此函式可取得十六進位的數值。|
|[AtlGetVersion](#atlgetversion)|呼叫此函式可取得您所使用的 ATL 程式庫版本。  |
|[AtlHexDecode](#atlhexdecode)|將已編碼為十六進位文字的資料字串解碼，例如先前對 [AtlHexEncode](#atlhexencode)的呼叫。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。|
|[AtlHexEncode](#atlhexencode)|呼叫此函式可將一些資料編碼為十六進位文字字串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[AtlHexValue](#atlhexvalue)|呼叫此函式可取得十六進位的數值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|呼叫此函式可將 Unicode 字串轉換為 UTF-8。 |
|[BEncode](#bencode)|呼叫此函式可使用 "B" 編碼方式轉換部分資料。|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[EscapeXML](#escapexml)|呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。|
|[GetExtendedChars](#getextendedchars)|呼叫此函式可取得字串中的擴充字元數目。|
|[IsExtendedChar](#isextendedchar)|呼叫此函式，以找出指定的字元是否為擴充的字元 (小於32、大於126，而不是定位字元、換行字元或換行字元) |
|[QEncode](#qencode)|呼叫此函式可使用 "Q" 編碼方式轉換部分資料。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[QPDecode](#qpdecode)|解碼以引號可列印格式編碼的資料字串，例如先前對 [QPEncode](#qpencode)的呼叫。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。|
|[QPEncode](#qpencode)|呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[UUDecode](#uudecode)|將已 uuencode 編碼的資料字串解碼，例如先前對 [UUEncode](#uuencode)的呼叫。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。|
|[UUEncode](#uuencode)|呼叫此函式可對一些資料進行 UUENCODE 編碼。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|

## <a name="requirements"></a>規格需求

**標頭：** atlenc.h。h

## <a name="atlgethexvalue"></a><a name="atlgethexvalue"></a> AtlGetHexValue

呼叫此函式可取得十六進位的數值。

```cpp
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>參數

*下巴*<br/>
十六進位字元 ' 0 '-' 9 '、' A'-'z-'F ' 或 ' a'-'z-'F '。

### <a name="return-value"></a>傳回值

轉譯為十六進位數位之輸入字元的數值。 例如，' 0 ' 的輸入會傳回值0，而 ' A ' 的輸入會傳回值10。 如果輸入字元不是十六進位數位，此函數會傳回-1。

## <a name="atlgetversion"></a><a name="atlgetversion"></a> AtlGetVersion

呼叫此函式可取得您所使用的 ATL 程式庫版本。

```cpp
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>參數

*保存*<br/>
保留的指標。

### <a name="return-value"></a>傳回值

傳回您正在編譯或執行之 ATL 程式庫版本的 DWORD 整數值。

## <a name="example"></a>範例

函數應該如下所示呼叫。

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="atlhexdecode"></a><a name="atlhexdecode"></a> AtlHexDecode

將已編碼為十六進位文字的資料字串解碼，例如先前對 [AtlHexEncode](#atlhexencode)的呼叫。

```cpp
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>參數

*pSrcData*<br/>
包含要解碼之資料的字串。

*nSrcLen*<br/>
*PSrcData*的長度（以字元為單位）。

*pbDest*<br/>
呼叫端配置的緩衝區，以接收已解碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *pbDest*的長度（以位元組為單位）。 如果函式成功，則變數會接收寫入至緩衝區的位元組數目。 如果函式失敗，則變數會收到緩衝區的必要長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

## <a name="atlhexdecodegetrequiredlength"></a><a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength

呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。

```cpp
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
編碼字串中的字元數。

### <a name="return-value"></a>傳回值

緩衝區所需的位元組數目，此緩衝區可能會保存已解碼的 *nSrcLen* 字元字串。

## <a name="atlhexencode"></a><a name="atlhexencode"></a> AtlHexEncode

呼叫此函式可將一些資料編碼為十六進位文字字串。

```cpp
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
包含要編碼之資料的緩衝區。

*nSrcLen*<br/>
要編碼之資料的長度（以位元組為單位）。

*szDest*<br/>
呼叫端配置的緩衝區，用來接收編碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *szDest*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會以緩衝區的字元接收所需的長度。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

來源資料的每個位元組會編碼為2個十六進位字元。

## <a name="atlhexencodegetrequiredlength"></a><a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```cpp
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

### <a name="return-value"></a>傳回值

可能保存 *nSrcLen* 位元組之編碼資料的緩衝區所需的字元數。

## <a name="atlhexvalue"></a><a name="atlhexvalue"></a> AtlHexValue

呼叫此函式可取得十六進位的數值。

```cpp
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>參數

*下巴*<br/>
十六進位字元 ' 0 '-' 9 '、' A'-'z-'F ' 或 ' a'-'z-'F '。

### <a name="return-value"></a>傳回值

轉譯為十六進位數位之輸入字元的數值。 例如，' 0 ' 的輸入會傳回值0，而 ' A ' 的輸入會傳回值10。 如果輸入字元不是十六進位數位，此函數會傳回-1。

## <a name="atlunicodetoutf8"></a><a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8

呼叫此函式可將 Unicode 字串轉換為 UTF-8。

```cpp
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>參數

*wszSrc*<br/>
要轉換的 Unicode 字串

*nSrc*<br/>
Unicode 字串的長度（以字元為單位）。

*szDest*<br/>
呼叫端配置的緩衝區，以接收已轉換的字串。

*nDest*<br/>
緩衝區的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

傳回已轉換之字串的字元數。

### <a name="remarks"></a>備註

若要判斷已轉換字串所需的緩衝區大小，請呼叫此函式，將0傳遞給 *szDest* 和 *nDest*。

## <a name="bencode"></a><a name="bencode"></a> BEncode

呼叫此函式可使用 "B" 編碼方式轉換部分資料。

```cpp
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
包含要編碼之資料的緩衝區。

*nSrcLen*<br/>
要編碼之資料的長度（以位元組為單位）。

*szDest*<br/>
呼叫端配置的緩衝區，用來接收編碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *szDest*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會以緩衝區的字元接收所需的長度。

*pszCharSet*<br/>
轉換所使用的字元集。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

"B" 編碼配置在 RFC 2047 () 中有所說明 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 。

## <a name="bencodegetrequiredlength"></a><a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```cpp
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

*nCharsetLen*<br/>
要用於轉換之字元集的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

可能保存 *nSrcLen* 位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

"B" 編碼配置在 RFC 2047 () 中有所說明 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 。

## <a name="escapexml"></a><a name="escapexml"></a> EscapeXML

呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。

```cpp
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>參數

*szIn*<br/>
要轉換的字串。

*nSrclen*<br/>
要轉換之字串的長度（以字元為單位）。

*szEsc*<br/>
呼叫端配置的緩衝區，以接收已轉換的字串。

*nDestLen*<br/>
呼叫端配置之緩衝區的長度（以字元為單位）。

*dwFlags*<br/>
描述如何執行轉換的 ATL_ESC 旗標。

- ATL_ESC_FLAG_NONE 預設行為。 引號和單引號不會轉換。
- ATL_ESC_FLAG_ATTR 引號和單引號會分別轉換成 `&quot;` 和 `&apos;` 。

### <a name="return-value"></a>傳回值

已轉換字串的長度（以字元為單位）。

### <a name="remarks"></a>備註

此函數所執行的可能轉換如下表所示：

|來源|Destination|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a><a name="getextendedchars"></a> GetExtendedChars

呼叫此函式可取得字串中的擴充字元數目。

```cpp
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*szSrc*<br/>
要分析的字串。

*nSrcLen*<br/>
字串的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

傳回 [IsExtendedChar](#isextendedchar)所決定之字串內的擴充字元數目。

## <a name="isextendedchar"></a><a name="isextendedchar"></a> IsExtendedChar

呼叫此函式，以找出指定的字元是否為擴充的字元 (小於32、大於126，而不是定位字元、換行字元或換行字元) 

```cpp
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>參數

*>ch*<br/>
要測試的字元

### <a name="return-value"></a>傳回值

如果延伸字元，則為 TRUE，否則為 FALSE。

## <a name="qencode"></a><a name="qencode"></a> QEncode

呼叫此函式可使用 "Q" 編碼方式轉換部分資料。

```cpp
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
包含要編碼之資料的緩衝區。

*nSrcLen*<br/>
要編碼之資料的長度（以位元組為單位）。

*szDest*<br/>
呼叫端配置的緩衝區，用來接收編碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *szDest*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會以緩衝區的字元接收所需的長度。

*pszCharSet*<br/>
轉換所使用的字元集。

*pnNumEncoded*<br/>
變數的指標，該變數會在傳回時包含必須轉換的 unsafe 字元數目。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

"Q" 編碼配置在 RFC 2047 () 中有所說明 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 。

## <a name="qencodegetrequiredlength"></a><a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```cpp
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

*nCharsetLen*<br/>
要用於轉換之字元集的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

可能保存 *nSrcLen* 位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

"Q" 編碼配置在 RFC 2047 () 中有所說明 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 。

## <a name="qpdecode"></a><a name="qpdecode"></a> QPDecode

解碼以引號可列印格式編碼的資料字串，例如先前對 [QPEncode](#qpencode)的呼叫。

```cpp
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
在包含要解碼之資料的緩衝區。

*nSrcLen*<br/>
在 *PbSrcData*的長度（以位元組為單位）。

*szDest*<br/>
擴展呼叫端配置的緩衝區，以接收已解碼的資料。

*pnDestLen*<br/>
擴展變數的指標，其中包含 *szDest*的長度（以位元組為單位）。 如果函式成功，則變數會接收寫入至緩衝區的位元組數目。 如果函式失敗，則變數會收到緩衝區的必要長度（以位元組為單位）。

*dwFlags*<br/>
在描述如何執行轉換的 ATLSMTP_QPENCODE 旗標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

加上引號的可列印編碼配置將于 RFC 2045 () 中說明 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 。

## <a name="qpdecodegetrequiredlength"></a><a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength

呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。

```cpp
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
編碼字串中的字元數。

### <a name="return-value"></a>傳回值

緩衝區所需的位元組數目，此緩衝區可能會保存已解碼的 *nSrcLen* 字元字串。

### <a name="remarks"></a>備註

加上引號的可列印編碼配置將于 RFC 2045 () 中說明 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 。

## <a name="qpencode"></a><a name="qpencode"></a> QPEncode

呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。

```cpp
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
包含要編碼之資料的緩衝區。

*nSrcLen*<br/>
要編碼之資料的長度（以位元組為單位）。

*szDest*<br/>
呼叫端配置的緩衝區，用來接收編碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *szDest*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會以緩衝區的字元接收所需的長度。

*dwFlags*<br/>
描述如何執行轉換的 ATLSMTP_QPENCODE 旗標。

- ATLSMTP_QPENCODE_DOT 如果句號出現在行首，則會將它新增至輸出以及編碼。

- ATLSMTP_QPENCODE_TRAILING_SOFT 附加 `=\r\n` 至編碼的字串。

加上引號的可列印編碼配置將于 [RFC 2045](https://www.ietf.org/rfc/rfc2045.txt)中說明。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

加上引號的可列印編碼配置將于 RFC 2045 () 中說明 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 。

## <a name="qpencodegetrequiredlength"></a><a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```cpp
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

### <a name="return-value"></a>傳回值

可能保存 *nSrcLen* 位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

加上引號的可列印編碼配置將于 RFC 2045 () 中說明 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 。

## <a name="uudecode"></a><a name="uudecode"></a> UUDecode

將已 uuencode 編碼的資料字串解碼，例如先前對 [UUEncode](#uuencode)的呼叫。

```cpp
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
包含要解碼之資料的字串。

*nSrcLen*<br/>
*PbSrcData*的長度（以位元組為單位）。

*pbDest*<br/>
呼叫端配置的緩衝區，以接收已解碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *pbDest*的長度（以位元組為單位）。 如果函式成功，則變數會接收寫入至緩衝區的位元組數目。 如果函式失敗，則變數會收到緩衝區的必要長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此 uuencoding 執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="uudecodegetrequiredlength"></a><a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength

呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。

```cpp
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
編碼字串中的字元數。

### <a name="return-value"></a>傳回值

緩衝區所需的位元組數目，此緩衝區可能會保存已解碼的 *nSrcLen* 字元字串。

### <a name="remarks"></a>備註

此 uuencoding 執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="uuencode"></a><a name="uuencode"></a> UUEncode

呼叫此函式可對一些資料進行 UUENCODE 編碼。

```cpp
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
包含要編碼之資料的緩衝區。

*nSrcLen*<br/>
要編碼之資料的長度（以位元組為單位）。

*szDest*<br/>
呼叫端配置的緩衝區，用來接收編碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含 *szDest*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會以緩衝區的字元接收所需的長度。

*lpszFile*<br/>
在 *dwFlags*中指定 ATLSMTP_UUENCODE_HEADER 時，要加入標頭中的檔案。

*dwFlags*<br/>
控制此函式行為的旗標。

- ATLSMTP_UUENCODE_HEADE 標頭將會進行編碼。

- ATLSMTP_UUENCODE_END 將會編碼結尾。

- 將會執行 ATLSMTP_UUENCODE_DOT 資料裝。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此 uuencoding 執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="uuencodegetrequiredlength"></a><a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```cpp
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

### <a name="return-value"></a>傳回值

可能保存 *nSrcLen* 位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

此 uuencoding 執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="see-also"></a>另請參閱

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl-com-desktop-components.md)
