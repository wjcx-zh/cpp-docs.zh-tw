---
title: ATL HTTP 公用程式函式
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: d2e30f940ded0bf355000cd42ff46a67662b54f5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833981"
---
# <a name="atl-http-utility-functions"></a>ATL HTTP 公用程式函式

這些函數支援 Url 的操作。

|函式|描述|
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|正常化 URL，包括將 unsafe 字元和空格轉換成 escape 序列。|
|[AtlCombineUrl](#atlcombineurl)|將基底 URL 和相對 URL 合併為單一的標準 URL。|
|[AtlEscapeUrl](#atlescapeurl)|將所有不安全的字元轉換成 escape 序列。|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|取得與特定網際網路通訊協定或配置相關聯的預設通訊埠編號。|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|判斷字元是否可在 URL 中安全使用。|
|[AtlUnescapeUrl](#atlunescapeurl)|將已轉義的字元轉換回其原始值。|
|[RGBToHtml](#rgbtohtml)|將 [COLORREF](/windows/win32/gdi/colorref) 值轉換為對應于該色彩值的 HTML 文字。|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|

## <a name="requirements"></a>規格需求

**標頭：** atlutil。h

## <a name="atlcanonicalizeurl"></a><a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

呼叫此函式可規範化 URL，包括將 Unsafe 字元和空格轉換成逸出序列。

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*szUrl*<br/>
要正式的 URL。

*szCanonicalized*<br/>
呼叫端配置的緩衝區，用來接收正式的 URL。

*pdwMaxLength*<br/>
變數的指標，其中包含 *szCanonicalized*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數，包括結束的 null 字元。 如果函式失敗，則變數會收到所需的緩衝區長度（以位元組為單位），包括結束 null 字元的空間。

*dwFlags*<br/>
ATL_URL 旗標，用來控制此函數的行為。

- ATL_URL_BROWSER_MODE 不會在 "#" 或 "？" 之後編碼或解碼字元，而且在 "？" 之後不會移除尾端空白字元。 如果未指定此值，則會編碼整個 URL，並移除尾端空白字元。

- ATL_URL_DECODE 在剖析 URL 之前，將所有的% XX 序列轉換成字元，包括 escape 序列。

- ATL_URL_ENCODE_PERCENT 將遇到的任何百分比符號編碼。 依預設，不會編碼百分比符號。

- ATL_URL_ENCODE_SPACES_ONLY 只將空格編碼。

- ATL_URL_ESCAPE 會將 (% XX) 的所有 ESCAPE 序列轉換為其對應的字元。

- ATL_URL_NO_ENCODE 不會將 unsafe 字元轉換成 escape 序列。

- ATL_URL_NO_META 不會移除中繼序列 (例如 "." 和 "..."從 URL ) 。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

行為與目前版本的 [InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) 相同，但不需要安裝 WinInet 或 Internet Explorer。

## <a name="atlcombineurl"></a><a name="atlcombineurl"></a> AtlCombineUrl

呼叫此函式可將基底 URL 和相對 URL 結合成單一、標準的 URL。

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*szBaseUrl*<br/>
基本 URL。

*szRelativeUrl*<br/>
相對於基底 URL 的 URL。

*szBuffer*<br/>
呼叫端配置的緩衝區，用來接收正式的 URL。

*pdwMaxLength*<br/>
變數的指標，其中包含 *szBuffer*的長度（以字元為單位）。 如果函式成功，則變數會接收寫入緩衝區的字元數，包括結束的 null 字元。 如果函式失敗，則變數會收到所需的緩衝區長度（以位元組為單位），包括結束 null 字元的空間。

*dwFlags*<br/>
控制此函式行為的旗標。 請參閱 [AtlCanonicalizeUrl](#atlcanonicalizeurl)。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

行為與目前版本的 [InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) 相同，但不需要安裝 WinInet 或 Internet Explorer。

## <a name="atlescapeurl"></a><a name="atlescapeurl"></a> AtlEscapeUrl

呼叫此函式會將所有 Unsafe 字元轉換成逸出序列。

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*lpszStringIn*<br/>
要轉換的 URL。

*lpszStringOut*<br/>
呼叫端配置的緩衝區，已轉換的 URL 將會寫入至該緩衝區。

*pdwStrLen*<br/>
DWORD 變數的指標。 如果函式成功， *pdwStrLen* 會接收寫入緩衝區的字元數，包括結束的 null 字元。 如果函式失敗，則變數會收到所需的緩衝區長度（以位元組為單位），包括結束 null 字元的空間。 使用這個方法的寬字元版本時， *pdwStrLen* 會收到所需的字元數，而不是位元組數。

*dwMaxLength*<br/>
緩衝區 *lpszStringOut*的大小。

*dwFlags*<br/>
ATL_URL 旗標，用來控制此函數的行為。 如需可能的值，請參閱 [ATLCanonicalizeUrl](#atlcanonicalizeurl) 。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

## <a name="atlgetdefaulturlport"></a><a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

呼叫此函式可取得與特定網際網路通訊協定或配置相關聯的預設通訊埠編號。

```cpp
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>參數

*m_nScheme*<br/>
[ATL_URL_SCHEME](atl-url-scheme-enum.md)值，識別您要取得其埠號碼的配置。

### <a name="return-value"></a>傳回值

如果無法辨識配置，則為與指定之配置相關聯的 [ATL_URL_PORT](atl-typedefs.md#atl_url_port) 或 ATL_URL_INVALID_PORT_NUMBER。

## <a name="atlisunsafeurlchar"></a><a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

呼叫此函式可了解在 URL 中使用某個字元是否安全。

```cpp
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>參數

*下巴*<br/>
要測試安全性的字元。

### <a name="return-value"></a>傳回值

如果輸入字元不安全，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

您可以使用此函式來測試不應該在 Url 中使用的字元，並使用 [AtlCanonicalizeUrl](#atlcanonicalizeurl)進行轉換。

## <a name="atlunescapeurl"></a><a name="atlunescapeurl"></a> AtlUnescapeUrl

呼叫此函式將逸出字元轉換回其原始值。

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>參數

*lpszStringIn*<br/>
要轉換的 URL。

*lpszStringOut*<br/>
呼叫端配置的緩衝區，已轉換的 URL 將會寫入至該緩衝區。

*pdwStrLen*<br/>
DWORD 變數的指標。 如果函式成功，則變數會接收寫入緩衝區的字元數，包括結束的 null 字元。 如果函式失敗，則變數會收到所需的緩衝區長度（以位元組為單位），包括結束 null 字元的空間。

*dwMaxLength*<br/>
緩衝區 *lpszStringOut*的大小。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

反轉 [AtlEscapeUrl](#atlescapeurl)所套用的轉換進程。

## <a name="rgbtohtml"></a><a name="rgbtohtml"></a> RGBToHtml

將 [COLORREF](/windows/win32/gdi/colorref) 值轉換為對應于該色彩值的 HTML 文字。

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>參數

*color*<br/>
RGB 色彩值。

*pbOut*<br/>
呼叫端配置的緩衝區，用來接收 HTML 色彩值的文字。 緩衝區的空間必須至少為8個字元，包括 null 結束字元) 的空間。

*nBuffer*<br/>
緩衝區的大小（以位元組為單位） (包括 null 結束字元的空間) 。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

HTML 色彩值是一符號，後面接著6位數的十六進位值，每個色彩的紅色、綠色和藍色元件都使用2個數字 (例如，#FFFFFF 為白色) 。

## <a name="systemtimetohttpdate"></a><a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>參數

*聖*<br/>
以 HTTP 格式字串形式取得的系統時間。

*strTime*<br/>
字串變數的參考，可接收 RFC 2616 中定義的 HTTP 日期時間（如 RFC ([https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)) 和 rfc 1123 ([https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)) ）。

## <a name="see-also"></a>另請參閱

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
