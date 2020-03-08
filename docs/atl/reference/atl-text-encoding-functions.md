---
title: ATL 文字編碼函數
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
ms.openlocfilehash: 1380d33c485c1ac895558bbcaf86c902c6074cd4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865019"
---
# <a name="atl-text-encoding-functions"></a>ATL 文字編碼函數

這些函數支援文字編碼和解碼。

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|呼叫此函式可取得十六進位的數值。|
|[AtlGetVersion](#atlgetversion)|呼叫此函式可取得您所使用的 ATL 程式庫版本。  |
|[AtlHexDecode](#atlhexdecode)|將已編碼為十六進位文字的資料字串（例如先前的[AtlHexEncode](#atlhexencode)呼叫）解碼。|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。|
|[AtlHexEncode](#atlhexencode)|呼叫此函式可將一些資料編碼為十六進位文字字串。|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[AtlHexValue](#atlhexvalue)|呼叫此函式可取得十六進位的數值。 |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|呼叫此函式可將 Unicode 字串轉換為 UTF-8。 |
|[BEncode](#bencode)|呼叫此函式可使用 "B" 編碼方式轉換部分資料。|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[EscapeXML](#escapexml)|呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。|
|[GetExtendedChars](#getextendedchars)|呼叫此函式可取得字串中的擴充字元數目。|
|[IsExtendedChar](#isextendedchar)|呼叫此函式可找出指定的字元是否為擴充字元（小於32，大於126，而不是定位字元、換行字元或回車符）|
|[QEncode](#qencode)|呼叫此函式可使用 "Q" 編碼方式轉換部分資料。  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[QPDecode](#qpdecode)|將已以引號可列印格式編碼的資料字串（例如先前的[QPEncode](#qpencode)呼叫）解碼。|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。|
|[QPEncode](#qpencode)|呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|
|[UUDecode](#uudecode)|將已 uuencode 編碼的資料字串（例如先前呼叫的[UUEncode](#uuencode)）解碼。|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。|
|[UUEncode](#uuencode)|呼叫此函式可對一些資料進行 UUENCODE 編碼。 |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。|

## <a name="requirements"></a>需求

**標頭：** atlenc。h

## <a name="atlgethexvalue"></a>AtlGetHexValue

呼叫此函式可取得十六進位的數值。

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>參數

*下巴*<br/>
十六進位字元 ' 0 '-' 9 '、' A'-'z-'F ' 或 ' a'-'z-'F '。

### <a name="return-value"></a>傳回值

輸入字元的數值，此值會解讀為十六進位數位。 例如，' 0 ' 的輸入傳回0的值，而 ' A ' 的輸入傳回10的值。 如果輸入字元不是十六進位數位，此函數會傳回-1。

## <a name="atlgetversion"></a>AtlGetVersion

呼叫此函式可取得您所使用的 ATL 程式庫版本。

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>參數

*保留*<br/>
保留的指標。

### <a name="return-value"></a>傳回值

傳回您要編譯或執行之 ATL 程式庫版本的 DWORD 整數值。

## <a name="example"></a>範例

函式的呼叫方式應如下所示。

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="atlhexdecode"></a>AtlHexDecode

將已編碼為十六進位文字的資料字串（例如先前的[AtlHexEncode](#atlhexencode)呼叫）解碼。

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>參數

*pSrcData*<br/>
字串，包含要解碼的資料。

*nSrcLen*<br/>
*PSrcData*的長度（以字元為單位）。

*pbDest*<br/>
呼叫端配置的緩衝區，用來接收解碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含*pbDest*的長度（以位元組為單位）。 如果函式成功，變數會接收寫入緩衝區的位元組數目。 如果函式失敗，變數會收到緩衝區所需的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

## <a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength

呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的十六進位編碼字串解碼的資料。

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
編碼字串中的字元數。

### <a name="return-value"></a>傳回值

緩衝區所需的位元組數目，可以保存*nSrcLen*字元的已解碼字串。

## <a name="atlhexencode"></a>AtlHexEncode

呼叫此函式可將一些資料編碼為十六進位文字字串。

```
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
變數的指標，其中包含*szDest*的長度（以字元為單位）。 如果函式成功，變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會接收緩衝區中所需的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

來源資料的每個位元組都會編碼為2個十六進位字元。

## <a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

### <a name="return-value"></a>傳回值

可能保存*nSrcLen*位元組之編碼資料的緩衝區所需的字元數。

## <a name="atlhexvalue"></a>AtlHexValue

呼叫此函式可取得十六進位的數值。

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>參數

*下巴*<br/>
十六進位字元 ' 0 '-' 9 '、' A'-'z-'F ' 或 ' a'-'z-'F '。

### <a name="return-value"></a>傳回值

輸入字元的數值，此值會解讀為十六進位數位。 例如，' 0 ' 的輸入傳回0的值，而 ' A ' 的輸入傳回10的值。 如果輸入字元不是十六進位數位，此函數會傳回-1。

## <a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8

呼叫此函式可將 Unicode 字串轉換為 UTF-8。

```
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
呼叫端配置的緩衝區，用來接收轉換後的字串。

*nDest*<br/>
緩衝區的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

傳回已轉換字串的字元數。

### <a name="remarks"></a>備註

若要判斷轉換後的字串所需的緩衝區大小，請呼叫此函式，為*szDest*和*nDest*傳遞0。

## <a name="bencode"></a>BEncode

呼叫此函式可使用 "B" 編碼方式轉換部分資料。

```
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
變數的指標，其中包含*szDest*的長度（以字元為單位）。 如果函式成功，變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會接收緩衝區中所需的長度（以字元為單位）。

*pszCharSet*<br/>
轉換時要使用的字元集。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

「B」編碼配置會在 RFC 2047 （[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）中說明。

## <a name="bencodegetrequiredlength"></a>BEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

*nCharsetLen*<br/>
要用於轉換之字元集的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

可能保存*nSrcLen*位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

「B」編碼配置會在 RFC 2047 （[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）中說明。

## <a name="escapexml"></a>EscapeXML

呼叫此函式可將無法在 XML 中安全使用的字元轉換成安全的對等字元。

```
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
呼叫端配置的緩衝區，用來接收轉換後的字串。

*nDestLen*<br/>
呼叫端配置緩衝區的長度（以字元為單位）。

*dwFlags*<br/>
描述如何執行轉換的 ATL_ESC 旗標。

- ATL_ESC_FLAG_NONE 預設行為。 不會轉換引號和單引號。
- ATL_ESC_FLAG_ATTR 的引號和單引號會分別轉換成 `&quot;` 和 `&apos;`。

### <a name="return-value"></a>傳回值

已轉換字串的長度（以字元為單位）。

### <a name="remarks"></a>備註

此函式所執行的可能轉換如下表所示：

|來源|Destination|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a>GetExtendedChars

呼叫此函式可取得字串中的擴充字元數目。

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*szSrc*<br/>
要分析的字串。

*nSrcLen*<br/>
字串的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

傳回在字串中找到的擴充字元數，由[IsExtendedChar](#isextendedchar)決定。

## <a name="isextendedchar"></a>IsExtendedChar

呼叫此函式可找出指定的字元是否為擴充字元（小於32，大於126，而不是定位字元、換行字元或回車符）

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>參數

*頻道*<br/>
要測試的字元

### <a name="return-value"></a>傳回值

如果已擴充字元，則為 TRUE，否則為 FALSE。

## <a name="qencode"></a>QEncode

呼叫此函式可使用 "Q" 編碼方式轉換部分資料。

```
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
變數的指標，其中包含*szDest*的長度（以字元為單位）。 如果函式成功，變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會接收緩衝區中所需的長度（以字元為單位）。

*pszCharSet*<br/>
轉換時要使用的字元集。

*pnNumEncoded*<br/>
傳回之變數的指標，包含必須轉換的不安全字元數目。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

「Q」編碼配置會在 RFC 2047 （[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）中說明。

## <a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

*nCharsetLen*<br/>
要用於轉換之字元集的長度（以字元為單位）。

### <a name="return-value"></a>傳回值

可能保存*nSrcLen*位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

「Q」編碼配置會在 RFC 2047 （[https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)）中說明。

## <a name="qpdecode"></a>QPDecode

將已以引號可列印格式編碼的資料字串（例如先前的[QPEncode](#qpencode)呼叫）解碼。

```
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
在*PbSrcData*的長度（以位元組為單位）。

*szDest*<br/>
脫銷呼叫端配置的緩衝區，用來接收解碼的資料。

*pnDestLen*<br/>
脫銷變數的指標，其中包含*szDest*的長度（以位元組為單位）。 如果函式成功，變數會接收寫入緩衝區的位元組數目。 如果函式失敗，變數會收到緩衝區所需的長度（以位元組為單位）。

*dwFlags*<br/>
在描述如何執行轉換的 ATLSMTP_QPENCODE 旗標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

在 RFC 2045 （[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）中會描述以引號列印的編碼配置。

## <a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength

呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的加上引號可列印編碼字串解碼的資料。

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
編碼字串中的字元數。

### <a name="return-value"></a>傳回值

緩衝區所需的位元組數目，可以保存*nSrcLen*字元的已解碼字串。

### <a name="remarks"></a>備註

在 RFC 2045 （[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）中會描述以引號列印的編碼配置。

## <a name="qpencode"></a>QPEncode

呼叫此函式可採用加上引號的可列印格式對一些資料進行編碼。

```
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
變數的指標，其中包含*szDest*的長度（以字元為單位）。 如果函式成功，變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會接收緩衝區中所需的長度（以字元為單位）。

*dwFlags*<br/>
描述如何執行轉換的 ATLSMTP_QPENCODE 旗標。

- ATLSMTP_QPENCODE_DOT 如果某個期間出現在行首，則會將它新增至輸出以及已編碼的。

- ATLSMTP_QPENCODE_TRAILING_SOFT 會將 `=\r\n` 附加至編碼的字串。

以引號列印的編碼配置會在[RFC 2045](https://www.ietf.org/rfc/rfc2045.txt)中說明。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

在 RFC 2045 （[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）中會描述以引號列印的編碼配置。

## <a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

### <a name="return-value"></a>傳回值

可能保存*nSrcLen*位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

在 RFC 2045 （[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)）中會描述以引號列印的編碼配置。

## <a name="uudecode"></a>UUDecode

將已 uuencode 編碼的資料字串（例如先前呼叫的[UUEncode](#uuencode)）解碼。

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>參數

*pbSrcData*<br/>
字串，包含要解碼的資料。

*nSrcLen*<br/>
*PbSrcData*的長度（以位元組為單位）。

*pbDest*<br/>
呼叫端配置的緩衝區，用來接收解碼的資料。

*pnDestLen*<br/>
變數的指標，其中包含*pbDest*的長度（以位元組為單位）。 如果函式成功，變數會接收寫入緩衝區的位元組數目。 如果函式失敗，變數會收到緩衝區所需的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

這個 uuencoding 的執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength

呼叫此函式可取得以位元組為單位的緩衝區大小，該緩衝區大小可包含從指定長度的 UUENCODE 編碼字串解碼的資料。

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
編碼字串中的字元數。

### <a name="return-value"></a>傳回值

緩衝區所需的位元組數目，可以保存*nSrcLen*字元的已解碼字串。

### <a name="remarks"></a>備註

這個 uuencoding 的執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="uuencode"></a>UUEncode

呼叫此函式可對一些資料進行 UUENCODE 編碼。

```
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
變數的指標，其中包含*szDest*的長度（以字元為單位）。 如果函式成功，變數會接收寫入緩衝區的字元數。 如果函式失敗，變數會接收緩衝區中所需的長度（以字元為單位）。

*lpszFile*<br/>
當*dwFlags*中指定了 ATLSMTP_UUENCODE_HEADER 時，要加入標頭的檔案。

*dwFlags*<br/>
控制此函式行為的旗標。

- ATLSMTP_UUENCODE_HEADE 標頭將會進行編碼。

- ATLSMTP_UUENCODE_END END 會進行編碼。

- 將會執行 ATLSMTP_UUENCODE_DOT 的資料裝。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

這個 uuencoding 的執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength

呼叫此函式可取得以字元為單位的緩衝區大小，該緩衝區大小可包含從指定大小的資料解碼的字串。

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>參數

*nSrcLen*<br/>
要編碼的資料位元組數目。

### <a name="return-value"></a>傳回值

可能保存*nSrcLen*位元組之編碼資料的緩衝區所需的字元數。

### <a name="remarks"></a>備註

這個 uuencoding 的執行會遵循 POSIX P 1003.2 b/D11 規格。

## <a name="see-also"></a>另請參閱

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl-com-desktop-components.md)
