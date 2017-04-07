---
title: "ATL HTTP 公用程式函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 0f55ad2529ac32647d72336b426e0790f5617561
ms.lasthandoff: 03/31/2017

---
# <a name="atl-http-utility-functions"></a>ATL HTTP 公用程式函式

這些函式支援操作的 Url。

|||  
|-|-|  
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes URL，包括將 unsafe 字元和空格轉換成逸出序列。|  
|[AtlCombineUrl](#atlcombineurl)|將基底 URL 和相對 URL 結合成單一、 標準的 URL。|  
|[AtlEscapeUrl](#atlescapeurl)|所有 unsafe 字元轉換成逸出序列。|  
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|取得與特定網際網路通訊協定或配置相關聯的預設連接埠號碼。|  
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|判斷字元是否為安全可供在 URL 中使用。|  
|[AtlUnescapeUrl](#atlunescapeurl)|轉換回其原始值的逸出字元。|  
|[RGBToHtml](#rgbtohtml)|將轉換[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)色彩值的 HTML 文字的值。|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|

## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  

## <a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl
呼叫此函式可規範化 URL，包括將 Unsafe 字元和空格轉換成逸出序列。  
  
```    
inline BOOL AtlCanonicalizeUrl(  
   LPCTSTR szUrl,  
   LPTSTR szCanonicalized,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>參數  
 `szUrl`  
 要規範化 URL。  
  
 `szCanonicalized`  
 呼叫端配置緩衝區接收正式的 URL。  
  
 `pdwMaxLength`  
 變數，其中包含以字元為單位的長度指標`szCanonicalized`。 如果函式成功，變數就會收到不包括結束的 null 字元的緩衝區寫入的字元數。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。  
  
 `dwFlags`  
 ATL_URL 旗標控制此函式的行為。 

- `ATL_URL_BROWSER_MODE`不會進行編碼或解碼字元之後"#"或"？"，並不會移除尾端空白字元之後"？"。 如果未指定此值，會編碼整個 URL，並移除尾端空白字元。
- `ATL_URL_DECODE`將所有 %xx 序列都轉換成字元，包括逸出序列之前在剖析 URL。
- `ATL_URL_ENCODE_PERCENT`任何遇到的百分比符號會將編碼。 根據預設，未編碼的百分比符號。
- `ATL_URL_ENCODE_SPACES_ONLY`空間只會將編碼。
- `ATL_URL_ESCAPE`將所有逸出序列 （%xx) 轉換成其對應的字元。
- `ATL_URL_NO_ENCODE`不會轉換成逸出序列不安全的字元。
- `ATL_URL_NO_META`不會移除中繼序列 (例如"。"和"..") 從 URL。 
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 行為類似的目前版本[InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342) ，但不需要安裝的 WinInet 或 Internet Explorer。  
  
### <a name="see-also"></a>另請參閱  
 [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342)

 ## <a name="atlcombineurl"></a>AtlCombineUrl
 呼叫此函式可將基底 URL 和相對 URL 結合成單一、標準的 URL。  
  
```    
inline BOOL AtlCombineUrl(  
   LPCTSTR szBaseUrl,  
   LPCTSTR szRelativeUrl,  
   LPTSTR szBuffer,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>參數  
 *szBaseUrl*  
 基底 URL。  
  
 *szRelativeUrl*  
 相對於基底 URL 的 URL。  
  
 `szBuffer`  
 呼叫端配置緩衝區接收正式的 URL。  
  
 `pdwMaxLength`  
 變數，其中包含以字元為單位的長度指標`szBuffer`。 如果函式成功，變數就會收到不包括結束的 null 字元的緩衝區寫入的字元數。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。  
  
 `dwFlags`  
 控制此函式的行為的旗標。 請參閱[ATL_URL 旗標](http://msdn.microsoft.com/library/76e8cc5c-4e17-4eb1-ac29-a94d5256c4a7)。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 行為類似的目前版本[InternetCombineUrl](http://msdn.microsoft.com/library/windows/desktop/aa384355) ，但不需要安裝的 WinInet 或 Internet Explorer。  
  
## <a name="atlescapeurl"></a>AtlEscapeUrl
 呼叫此函式會將所有 Unsafe 字元轉換成逸出序列。  
  
```    
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
 `lpszStringIn`  
 要轉換的 URL。  
  
 `lpszStringOut`  
 呼叫端配置的緩衝區，將寫入已轉換的 URL。  
  
 `pdwStrLen`  
 DWORD 變數的指標。 如果函式成功，`pdwStrLen`接收寫入緩衝區，不包括結束的 null 字元的字元數。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。 使用此方法的寬字元版本時`pdwStrLen`接收要求的字元數目，不是位元組的數目。  
  
 `dwMaxLength`  
 緩衝區的大小`lpszStringOut`。  
  
 `dwFlags`  
 ATL_URL 旗標控制此函式的行為。 請參閱[ATLCanonicalizeUrl](#atlcanonicalizeurl)可能的值。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
## <a name="atlgetdefaulturlport"></a> 
 呼叫此函式可取得與特定網際網路通訊協定或配置相關聯的預設通訊埠編號。  
  
```  
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();  
```  
  
### <a name="parameters"></a>參數  
 *m_nScheme*  
 [ATL_URL_SCHEME](atl-url-scheme-enum.md)識別您要取得的連接埠號碼的配置值。  
  
### <a name="return-value"></a>傳回值  
 [ATL_URL_PORT](atl-typedefs.md#atl_url_port)與指定的配置或 ATL_URL_INVALID_PORT_NUMBER 相關，如果無法辨識的配置。  

## <a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar
 呼叫此函式可了解在 URL 中使用某個字元是否安全。  
  
```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```  
  
### <a name="parameters"></a>參數  
 `chIn`  
 要測試為安全的字元。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**輸入的字元是不安全，如果**FALSE**否則。  
  
### <a name="remarks"></a>備註  
 不應在 Url 中的字元可以使用這個函式進行測試，並使用轉換[AtlCanonicalizeUrl](#atlcanonicalizeurl)。  
  
## <a name="atlunescapeurl"></a>AtlUnescapeUrl
 呼叫此函式將逸出字元轉換回其原始值。  
  
```    
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
 `lpszStringIn`  
 要轉換的 URL。  
  
 `lpszStringOut`  
 呼叫端配置的緩衝區，將寫入已轉換的 URL。  
  
 `pdwStrLen`  
 DWORD 變數的指標。 如果函式成功，變數就會收到不包括結束的 null 字元的緩衝區寫入的字元數。 如果函式失敗，變數會收到所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。  
  
 `dwMaxLength`  
 緩衝區的大小`lpszStringOut`。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 反轉所套用的轉換程序[AtlEscapeUrl](#atlescapeurl)。  
  
## <a name="rgbtohtml"></a>RGBToHtml
將轉換[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)色彩值的 HTML 文字的值。  
  
```  
bool inline RGBToHtml(  
   COLORREF color,  
   LPTSTR pbOut,  
   long nBuffer);  
```  
  
### <a name="parameters"></a>參數  
 `color`  
 RGB 色彩值。  
  
 `pbOut`  
 呼叫端配置緩衝區接收 HTML 色彩值的文字。 緩衝區空間必須為至少 8 個字元，包括 null 結束字元的空間）。  
  
 *nBuffer*  
 以位元組為單位 （包括 null 結束字元的空間） 的緩衝區大小。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 HTML 色彩值是井字號後面接著 6 位數的十六進位值，使用 2 位數的每個色彩的紅色、 綠色和藍色元件 （例如，#FFFFFF 是白色）。  
  
## <a name="systemtimetohttpdate"></a>SystemTimeToHttpDate
呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。  
  
```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```  
  
### <a name="parameters"></a>參數  
 `st`  
 為 HTTP 格式字串來取得系統時間。  
  
 *strTime*  
 接收 HTTP 日期時間，如 RFC 2616 中定義的字串變數的參考 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) 和 RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt))。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)   


