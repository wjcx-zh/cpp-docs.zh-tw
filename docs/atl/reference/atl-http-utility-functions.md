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
ms.sourcegitcommit: 9ab4b38b2ba14aca2240d12fff966d36750a3229
ms.openlocfilehash: dd8b3a279148e2a5b72d96724c329e49cd5d3e5f
ms.lasthandoff: 02/24/2017

---
# <a name="atl-http-utility-functions"></a>ATL HTTP 公用程式函式

這些函式支援操作的 Url。

|||  
|-|-|  
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes URL，包括將 unsafe 字元和空格轉換成逸出序列。|  
|[AtlCombineUrl](#atlcombineurl)|將基底 URL 和相對 URL 結合成單一、 標準的 URL。|  
|[AtlEscapeUrl](#atlescapeurl)|將轉換成逸出序列的所有 unsafe 字元。|  
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|取得與特定網際網路通訊協定或配置相關聯的預設連接埠號碼。|  
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|判斷字元是否為安全可供使用的 url。|  
|[AtlUnescapeUrl](#atlunescapeurl)|轉換回其原始值的逸出字元。|  
|[RGBToHtml](#rgbtohtml)|將轉換[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)色彩值的 HTML 文字的值。|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|

## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  

## <a name="a-nameatlcanonicalizeurla-atlcanonicalizeurl"></a><a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl
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
 若要接收正式的 URL 的呼叫端配置緩衝區。  
  
 `pdwMaxLength`  
 包含的字元長度的變數的指標`szCanonicalized`。 如果函式成功，變數就會收到寫入不包括結束的 null 字元緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。  
  
 `dwFlags`  
 控制這個函式行為的旗標。 請參閱[ATL_URL 旗標](http://msdn.microsoft.com/library/76e8cc5c-4e17-4eb1-ac29-a94d5256c4a7)。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 就目前版本的[InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342) ，但不需要 WinInet 或 Internet Explorer 安裝。  
  
### <a name="see-also"></a>另請參閱  
 [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342)

 ## <a name="a-nameatlcombineurla-atlcombineurl"></a><a name="atlcombineurl"></a>AtlCombineUrl
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
 與基底 URL 相對 URL。  
  
 `szBuffer`  
 若要接收正式的 URL 的呼叫端配置緩衝區。  
  
 `pdwMaxLength`  
 包含的字元長度的變數的指標`szBuffer`。 如果函式成功，變數就會收到寫入不包括結束的 null 字元緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。  
  
 `dwFlags`  
 控制這個函式行為的旗標。 請參閱[ATL_URL 旗標](http://msdn.microsoft.com/library/76e8cc5c-4e17-4eb1-ac29-a94d5256c4a7)。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 就目前版本的[InternetCombineUrl](http://msdn.microsoft.com/library/windows/desktop/aa384355) ，但不需要 WinInet 或 Internet Explorer 安裝。  
  
## <a name="a-nameatlescapeurla-atlescapeurl"></a><a name="atlescapeurl"></a>AtlEscapeUrl
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
 呼叫端配置緩衝區寫入轉換過的 URL。  
  
 `pdwStrLen`  
 DWORD 變數的指標。 如果函式成功，`pdwStrLen`接收寫入緩衝區，不包括結束的 null 字元的字元數。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。 使用這個方法的寬字元版本時會`pdwStrLen`收到需要的位元組數目的字元數。  
  
 `dwMaxLength`  
 緩衝區的大小`lpszStringOut`。  
  
 `dwFlags`  
 控制這個函式行為的旗標。 請參閱[ATL_URL 旗標](http://msdn.microsoft.com/library/76e8cc5c-4e17-4eb1-ac29-a94d5256c4a7)。  
  
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
 [ATL_URL_PORT](atl-typedefs.md#atl_url_port)關聯於指定的配置或 ATL_URL_INVALID_PORT_NUMBER，如果無法辨識的配置。  

## <a name="a-nameatlisunsafeurlchara-atlisunsafeurlchar"></a><a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar
 呼叫此函式可了解在 URL 中使用某個字元是否安全。  
  
```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```  
  
### <a name="parameters"></a>參數  
 `chIn`  
 要測試為安全的字元。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果輸入的字元是否安全， **FALSE**否則。  
  
### <a name="remarks"></a>備註  
 不應在 Url 中的字元可以使用此函式進行測試，並使用轉換[AtlCanonicalizeUrl](#atlcanonicalizeurl)。  
  
## <a name="a-nameatlunescapeurla-atlunescapeurl"></a><a name="atlunescapeurl"></a>AtlUnescapeUrl
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
 呼叫端配置緩衝區寫入轉換過的 URL。  
  
 `pdwStrLen`  
 DWORD 變數的指標。 如果函式成功，變數就會收到寫入不包括結束的 null 字元緩衝區的字元數。 如果函式失敗，變數會接收所需的長度，以位元組為單位的緩衝區，包括結束的 null 字元的空間。  
  
 `dwMaxLength`  
 緩衝區的大小`lpszStringOut`。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 反轉所套用的轉換程序[AtlEscapeUrl](#atlescapeurl)。  
  
## <a name="a-namergbtohtmla-rgbtohtml"></a><a name="rgbtohtml"></a>RGBToHtml
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
 呼叫端配置緩衝區接收 HTML 色彩值的文字。 緩衝區空間必須為至少 8 個字元，包括 null 結束字元的空格）。  
  
 *nBuffer*  
 以位元組為單位 （包括 null 結束字元的空格） 的緩衝區大小。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 HTML 色彩值是井字號後面接著 6 位數的十六進位值，使用 2 位數的每個色彩的紅色、 綠色和藍色元件 （例如，#FFFFFF 是白色）。  
  
## <a name="a-namesystemtimetohttpdatea-systemtimetohttpdate"></a><a name="systemtimetohttpdate"></a>SystemTimeToHttpDate
呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。  
  
```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```  
  
### <a name="parameters"></a>參數  
 `st`  
 系統時間，以取得做為 HTTP 格式字串。  
  
 *strTime*  
 接收 HTTP 日期時間，如 RFC 2616 中所定義的字串變數的參考 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) 和 RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt))。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)   


