---
title: CUrl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
dev_langs:
- C++
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afb0f7abc079d699cfcf682356b88b9cc8aa2bb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366230"
---
# <a name="curl-class"></a>CUrl 類別
這個類別表示的 URL。 它可讓您操作各自 URL 的每個項目是否剖析現有的 URL 字串，或建置全新的字串。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CUrl
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CUrl::CUrl](#curl)|建構函式。|  
|[CUrl:: ~ CUrl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CUrl::Canonicalize](#canonicalize)|呼叫此方法，將 URL 字串轉換成標準格式。|  
|[CUrl::Clear](#clear)|呼叫此方法，以清除所有 URL 欄位。|  
|[CUrl::CrackUrl](#crackurl)|呼叫這個方法來解碼並剖析的 URL。|  
|[CUrl::CreateUrl](#createurl)|呼叫這個方法來建立 URL。|  
|[CUrl::GetExtraInfo](#getextrainfo)|呼叫這個方法來取得額外的資訊 (例如*文字*或 #*文字*) 從 URL。|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|呼叫此方法以取得其長度的額外資訊 (例如*文字*或 #*文字*) 從 URL 擷取。|  
|[CUrl::GetHostName](#gethostname)|呼叫此方法以從 URL 取得主機名稱。|  
|[CUrl::GetHostNameLength](#gethostnamelength)|呼叫這個方法來取得主機名稱的長度。|  
|[CUrl::GetPassword](#getpassword)|呼叫此方法以從 URL 取得的密碼。|  
|[CUrl::GetPasswordLength](#getpasswordlength)|呼叫此方法以取得密碼的長度。|  
|[CUrl::GetPortNumber](#getportnumber)|呼叫這個方法，取得 ATL_URL_PORT 方面的連接埠號碼。|  
|[CUrl::GetScheme](#getscheme)|呼叫這個方法來取得 URL 配置。|  
|[CUrl::GetSchemeName](#getschemename)|呼叫這個方法，取得 URL 的配置名稱。|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|呼叫這個方法來取得 URL 的配置名稱的長度。|  
|[CUrl::GetUrlLength](#geturllength)|呼叫這個方法來取得 URL 的長度。|  
|[CUrl::GetUrlPath](#geturlpath)|呼叫這個方法，取得 URL 路徑。|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|呼叫這個方法，取得 URL 路徑長度。|  
|[CUrl::GetUserName](#getusername)|呼叫此方法以從 URL 取得使用者名稱。|  
|[CUrl::GetUserNameLength](#getusernamelength)|呼叫這個方法來取得使用者名稱的長度。|  
|[CUrl::SetExtraInfo](#setextrainfo)|呼叫此方法以設定額外的資訊 (例如*文字*或 #*文字*) 的 url。|  
|[CUrl::SetHostName](#sethostname)|呼叫此方法以設定主機名稱。|  
|[CUrl::SetPassword](#setpassword)|呼叫這個方法來設定密碼。|  
|[CUrl::SetPortNumber](#setportnumber)|呼叫此方法以設定 ATL_URL_PORT 方面的連接埠號碼。|  
|[CUrl::SetScheme](#setscheme)|呼叫此方法以設定 URL 配置。|  
|[CUrl::SetSchemeName](#setschemename)|呼叫此方法以設定 URL 的配置名稱。|  
|[CUrl::SetUrlPath](#seturlpath)|呼叫此方法以設定的 URL 路徑。|  
|[CUrl::SetUserName](#setusername)|呼叫此方法以設定使用者名稱。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|指派指定`CUrl`物件與目前`CUrl`物件。|  
  
## <a name="remarks"></a>備註  
 `CUrl` 可讓您操作的 URL，例如路徑或連接埠的數字欄位。 `CUrl` 了解下列形式的 Url:  
  
 \<配置 >://\<使用者名稱 >:\<密碼 > @\<主機名稱 >:\<通訊埠編號 > /\<UrlPath >\<ExtraInfo >  
  
 （某些欄位是選擇性的）。例如，請考慮此 URL:  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl)剖析它，如下所示：  
  
-   配置:"http"或[ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   UserName:"someone"  
  
-   密碼: 「 密碼 」  
  
-   主機名稱:"www.microsoft.com"  
  
-   通訊埠編號： 80  
  
-   UrlPath:"visualc/stuff.htm"  
  
-   ExtraInfo:"#contents"  
  
 若要操控 UrlPath 欄位 （例如），您會使用[GetUrlPath](#geturlpath)， [GetUrlPathLength](#geturlpathlength)，和[SetUrlPath](#seturlpath)。 您可以使用[CreateUrl](#createurl)建立完整的 URL 字串。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlutil.h  
  
##  <a name="canonicalize"></a>  CUrl::Canonicalize  
 呼叫此方法，將 URL 字串轉換成標準格式。  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 控制規範化旗標。 如果未不指定任何旗標 ( `dwFlags` = 0)，方法將所有 unsafe 字元和中繼順序轉換 (例如\\。，\..，和\\...) 來逸出序列。 `dwFlags` 可以是下列值之一：  
  
-   ATL_URL_BROWSER_MODE： 不進行編碼或解碼字元之後"#"或""並不會移除尾端空白字元之後""。 如果未指定此值，會編碼整個 URL，並移除尾端空白字元。  
  
-   ATL_URL _DECODE： 將所有 %xx 序列都轉換成字元，包括逸出序列之前在剖析 URL。  
  
-   ATL_URL _ENCODE_PERCENT： 編碼遇到任何百分比符號。 根據預設，未編碼的百分比符號。  
  
-   ATL_URL _ENCODE_SPACES_ONLY： 空間只會將編碼。  
  
-   ATL_URL _NO_ENCODE： 不會轉換成逸出序列不安全的字元。  
  
-   ATL_URL _NO_META： 不會移除中繼序列 (例如"。"和"..") 從 URL。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 將轉換成標準格式，包括將 unsafe 字元和逸出序列的空格轉換。  
  
##  <a name="clear"></a>  CUrl::Clear  
 呼叫此方法，以清除所有 URL 欄位。  
  
```
inline void Clear() throw();
```  
  
##  <a name="crackurl"></a>  CUrl::CrackUrl  
 呼叫這個方法來解碼並剖析的 URL。  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszUrl`  
 URL。  
  
 `dwFlags`  
 指定要轉換中的所有逸出字元的 ATL_URL_DECODE 或 ATL_URL_ESCAPE`lpszUrl`剖析之後及其實際值。 （在 Visual c + + 2005年之前 ATL_URL_DECODE 轉換所有逸出字元剖析之前）。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="createurl"></a>  CUrl::CreateUrl  
 這個方法會建構 CUrl 物件的元件欄位的 URL 字串。  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszUrl*  
 以保存完整的 URL 字串的字串緩衝區。  
  
 `pdwMaxLength`  
 最大長度*lpszUrl*字串緩衝區。  
  
 `dwFlags`  
 指定要轉換中的所有逸出字元 ATL_URL_ESCAPE *lpszUrl*為實際值。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會附加個別的欄位，才能建構完整的 URL 字串使用下列格式：  
  
 **\<配置 >://\<使用者 >:\<傳遞 > @\<網域 >:\<連接埠 >\<路徑 >\<額外 >**  
  
 當呼叫這個方法，`pdwMaxLength`參數一開始應該包含所參考的字串緩衝區的最大長度*lpszUrl*參數。 值`pdwMaxLength`參數會以更新的 URL 字串的實際長度。  
  
### <a name="example"></a>範例  
 這個範例會示範建立 CUrl 物件，以及擷取其 URL 字串  
  
 [!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="curl"></a>  CUrl::CUrl  
 建構函式。  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>參數  
 `urlThat`  
 `CUrl`複製來建立 URL 的物件。  
  
##  <a name="dtor"></a>  CUrl:: ~ CUrl  
 解構函式。  
  
```
~CUrl() throw();
```  
  
##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo  
 呼叫這個方法來取得額外的資訊 (例如*文字*或 #*文字*) 從 URL。  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回字串，包含額外的資訊。  
  
##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength  
 呼叫此方法以取得其長度的額外資訊 (例如*文字*或 #*文字*) 從 URL 擷取。  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回字串，包含額外資訊的長度。  
  
##  <a name="gethostname"></a>  CUrl::GetHostName  
 呼叫此方法以從 URL 取得主機名稱。  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的主機名稱。  
  
##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength  
 呼叫這個方法來取得主機名稱的長度。  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回主機名稱的長度。  
  
##  <a name="getpassword"></a>  CUrl::GetPassword  
 呼叫此方法以從 URL 取得的密碼。  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回密碼。  
  
##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength  
 呼叫此方法以取得密碼的長度。  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回密碼的長度。  
  
##  <a name="getportnumber"></a>  CUrl::GetPortNumber  
 呼叫此方法以取得通訊埠編號。  
  
```
inline ATL_URL_PORT GetPortNumber() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的連接埠號碼。  
  
##  <a name="getscheme"></a>  CUrl::GetScheme  
 呼叫這個方法來取得 URL 配置。  
  
```
inline ATL_URL_SCHEME GetScheme() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回[ATL_URL_SCHEME](atl-url-scheme-enum.md)描述 URL 的配置值。  
  
##  <a name="getschemename"></a>  CUrl::GetSchemeName  
 呼叫這個方法，取得 URL 的配置名稱。  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 URL 配置名稱 （例如"http"或"ftp"）。  
  
##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength  
 呼叫這個方法來取得 URL 的配置名稱的長度。  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 URL 的配置名稱長度。  
  
##  <a name="geturllength"></a>  CUrl::GetUrlLength  
 呼叫這個方法來取得 URL 的長度。  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 URL 長度。  
  
##  <a name="geturlpath"></a>  CUrl::GetUrlPath  
 呼叫這個方法，取得 URL 路徑。  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 URL 路徑。  
  
##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength  
 呼叫這個方法，取得 URL 路徑長度。  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 URL 路徑長度。  
  
##  <a name="getusername"></a>  CUrl::GetUserName  
 呼叫此方法以從 URL 取得使用者名稱。  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回使用者名稱。  
  
##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength  
 呼叫這個方法來取得使用者名稱的長度。  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回使用者名稱的長度。  
  
##  <a name="operator_eq"></a>  CUrl::operator =  
 指派指定`CUrl`物件與目前`CUrl`物件。  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>參數  
 `urlThat`  
 `CUrl`物件複製到目前的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回目前物件的參考。  
  
##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo  
 呼叫此方法以設定額外的資訊 (例如*文字*或 #*文字*) 的 url。  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszInfo*  
 字串，包含要在 URL 中包含的額外資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="sethostname"></a>  CUrl::SetHostName  
 呼叫此方法以設定主機名稱。  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszHost`  
 主機名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setpassword"></a>  CUrl::SetPassword  
 呼叫這個方法來設定密碼。  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszPass*  
 密碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setportnumber"></a>  CUrl::SetPortNumber  
 呼叫此方法以設定連接埠號碼。  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>參數  
 *nPrt*  
 連接埠號碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setscheme"></a>  CUrl::SetScheme  
 呼叫此方法以設定 URL 配置。  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>參數  
 `nScheme`  
 其中一個[ATL_URL_SCHEME](atl-url-scheme-enum.md)配置值。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您也可以設定配置依名稱 (請參閱[CUrl::SetSchemeName](#setschemename))。  
  
##  <a name="setschemename"></a>  CUrl::SetSchemeName  
 呼叫此方法以設定 URL 的配置名稱。  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszSchm*  
 URL 配置名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您也可以藉由設定配置[ATL_URL_SCHEME](atl-url-scheme-enum.md)常數 (請參閱[CUrl::SetScheme](#setscheme))。  
  
##  <a name="seturlpath"></a>  CUrl::SetUrlPath  
 呼叫此方法以設定的 URL 路徑。  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszPath`  
 URL 路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setusername"></a>  CUrl::SetUserName  
 呼叫此方法以設定使用者名稱。  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszUser*  
 使用者名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)
