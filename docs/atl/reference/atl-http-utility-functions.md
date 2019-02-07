---
title: ATL HTTP 公用程式函式
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: be38dc8b8547574ea47021f8b14f21060a0755f0
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849644"
---
# <a name="atl-http-utility-functions"></a>ATL HTTP 公用程式函式

這些函式支援操作的 Url。

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes URL，其中包括將 unsafe 字元和空格轉換成逸出序列。|
|[AtlCombineUrl](#atlcombineurl)|將基底 URL 和相對 URL 結合成單一、 標準的 URL 中。|
|[AtlEscapeUrl](#atlescapeurl)|將所有 unsafe 字元逸出序列轉換。|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|取得與特定網際網路通訊協定或配置相關聯的預設連接埠號碼。|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|判斷字元是否為安全的 URL 中使用。|
|[AtlUnescapeUrl](#atlunescapeurl)|轉換回其原始值的逸出字元。|
|[RGBToHtml](#rgbtohtml)|將轉換[COLORREF](/windows/desktop/gdi/colorref)色彩值相對應的 HTML 文字的值。|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|

## <a name="requirements"></a>需求

**標頭：** atlutil.h

## <a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

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
要規範化的 URL。

*szCanonicalized*<br/>
要接收的正式的 URL 的呼叫端配置緩衝區。

*pdwMaxLength*<br/>
指標變數，其中包含以字元為單位的長度*szCanonicalized*。 如果函式成功，變數就會收到包含結束的 null 字元的緩衝區寫入的字元數。 如果函式失敗，變數就會收到所需的長度以位元組為單位的緩衝區，包括結束的 null 字元的空白字元。

*dwFlags*<br/>
ATL_URL 旗標來控制此函式的行為。

- ATL_URL_BROWSER_MODE 不會進行編碼或解碼"#"之後的字元或"？"，並不會移除尾端空白字元之後"？"。 如果未指定此值，編碼整個 URL，並移除尾端空白字元。

- ATL_URL_DECODE 會將所有 %xx 序列都轉換成字元，才會剖析 URL，包括逸出序列。

- ATL_URL_ENCODE_PERCENT 編碼發現任何百分比符號。 根據預設，不被編碼百分比符號。

- ATL_URL_ENCODE_SPACES_ONLY 編碼空間只。

- ATL_URL_ESCAPE 將轉換的所有逸出序列 （%xx) 到其對應的字元。

- ATL_URL_NO_ENCODE 不會轉換成逸出序列的不安全字元。

- ATL_URL_NO_META 不會移除中繼序列 (例如"。"和"..") 從 URL。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

就等於目前的版本[InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla)但不需要安裝的 WinInet 或 Internet Explorer。

## <a name="atlcombineurl"></a> AtlCombineUrl

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
基底 URL。

*szRelativeUrl*<br/>
相對於基底 URL 的 URL。

*szBuffer*<br/>
要接收的正式的 URL 的呼叫端配置緩衝區。

*pdwMaxLength*<br/>
指標變數，其中包含以字元為單位的長度*szBuffer*。 如果函式成功，變數就會收到包含結束的 null 字元的緩衝區寫入的字元數。 如果函式失敗，變數就會收到所需的長度以位元組為單位的緩衝區，包括結束的 null 字元的空白字元。

*dwFlags*<br/>
控制此函式行為的旗標。 請參閱[AtlCanonicalizeUrl](#atlcanonicalizeurl)。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

就等於目前的版本[InternetCombineUrl](/windows/desktop/api/wininet/nf-wininet-internetcombineurla)但不需要安裝的 WinInet 或 Internet Explorer。

## <a name="atlescapeurl"></a> AtlEscapeUrl

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
呼叫端配置的緩衝區，已轉換的 URL 將會寫入至其中。

*pdwStrLen*<br/>
DWORD 變數的指標。 如果此函數成功， *pdwStrLen*接收寫入包括結束的 null 字元緩衝區的字元數。 如果函式失敗，變數就會收到所需的長度以位元組為單位的緩衝區，包括結束的 null 字元的空白字元。 使用這個方法，寬字元版本時會*pdwStrLen*收到所需，不是位元組的數目的字元數目。

*dwMaxLength*<br/>
緩衝區的大小*lpszStringOut*。

*dwFlags*<br/>
ATL_URL 旗標來控制此函式的行為。 請參閱[ATLCanonicalizeUrl](#atlcanonicalizeurl)可能的值。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

## <a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

呼叫此函式可取得與特定網際網路通訊協定或配置相關聯的預設通訊埠編號。

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>參數

*m_nScheme*<br/>
[ATL_URL_SCHEME](atl-url-scheme-enum.md)識別您要取得的連接埠號碼的配置值。

### <a name="return-value"></a>傳回值

[ATL_URL_PORT](atl-typedefs.md#atl_url_port)與指定的配置或 ATL_URL_INVALID_PORT_NUMBER 相關聯，如果無法辨識的配置。

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

呼叫此函式可了解在 URL 中使用某個字元是否安全。

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>參數

*chIn*<br/>
要測試為安全的字元。

### <a name="return-value"></a>傳回值

傳回為 true，則如果輸入的字元因不安全，則為 FALSE。

### <a name="remarks"></a>備註

不應在 Url 中的字元可以使用此函式進行測試，並且使用轉換[AtlCanonicalizeUrl](#atlcanonicalizeurl)。

## <a name="atlunescapeurl"></a> AtlUnescapeUrl

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
呼叫端配置的緩衝區，已轉換的 URL 將會寫入至其中。

*pdwStrLen*<br/>
DWORD 變數的指標。 如果函式成功，變數就會收到包含結束的 null 字元的緩衝區寫入的字元數。 如果函式失敗，變數就會收到所需的長度以位元組為單位的緩衝區，包括結束的 null 字元的空白字元。

*dwMaxLength*<br/>
緩衝區的大小*lpszStringOut*。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

反轉所套用的轉換過程[AtlEscapeUrl](#atlescapeurl)。

## <a name="rgbtohtml"></a> RGBToHtml

將轉換[COLORREF](/windows/desktop/gdi/colorref)色彩值相對應的 HTML 文字的值。

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
呼叫端配置緩衝區，以接收 HTML 色彩值的文字。 緩衝區必須具有至少 8 個字元，包括 null 結束字元的空間空間）。

*nBuffer*<br/>
以位元組為單位 （包括 null 結束字元的空間） 的緩衝區大小。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

HTML 色彩值是井字號，後面接著 6 位數的十六進位值，針對每個色彩的紅色、 綠色和藍色元件使用的 2 個數字 （例如 #FFFFFF 是白色）。

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>參數

*st*<br/>
若要以 HTTP 的格式字串來取得系統時間。

*strTime*<br/>
接收 HTTP 日期時間，如 RFC 2616 中所定義的字串變數的參考 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) 和 RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt))。

## <a name="see-also"></a>另請參閱

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla)
