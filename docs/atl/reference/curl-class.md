---
title: "CUrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: eda63a8dc704dd471d8078b848d95fc9fb44f58f
ms.lasthandoff: 02/24/2017

---
# <a name="curl-class"></a>CUrl 類別
這個類別表示的 URL。 它可讓您管理每個項目各自的 url 是否剖析現有的 URL 字串，或建置全新的字串。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CUrl
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CUrl::CUrl](#curl)|建構函式。|  
|[CUrl:: ~ CUrl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CUrl::Canonicalize](#canonicalize)|呼叫這個方法，將 URL 字串轉換成標準格式。|  
|[CUrl::Clear](#clear)|呼叫此方法，以清除所有 URL 的欄位。|  
|[CUrl::CrackUrl](#crackurl)|呼叫這個方法來解碼並剖析 URL。|  
|[CUrl::CreateUrl](#createurl)|呼叫這個方法來建立 URL。|  
|[CUrl::GetExtraInfo](#getextrainfo)|呼叫這個方法來取得額外資訊 (例如*文字*或 #*文字*) 從 URL。|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|呼叫這個方法來取得額外資訊的長度 (例如*文字*或 #*文字*) 從 URL 擷取。|  
|[CUrl::GetHostName](#gethostname)|呼叫此方法以從 URL 取得主機名稱。|  
|[CUrl::GetHostNameLength](#gethostnamelength)|呼叫這個方法，以取得主機名稱的長度。|  
|[CUrl::GetPassword](#getpassword)|呼叫此方法以從 URL 取得密碼。|  
|[CUrl::GetPasswordLength](#getpasswordlength)|呼叫這個方法，以取得密碼的長度。|  
|[CUrl::GetPortNumber](#getportnumber)|呼叫這個方法來取得 ATL_URL_PORT 方面的連接埠號碼。|  
|[CUrl::GetScheme](#getscheme)|呼叫這個方法，以取得 URL 配置。|  
|[CUrl::GetSchemeName](#getschemename)|呼叫這個方法，以取得 URL 的配置名稱。|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|呼叫這個方法，以取得 URL 的配置名稱的長度。|  
|[CUrl::GetUrlLength](#geturllength)|呼叫這個方法，以取得 URL 的長度。|  
|[CUrl::GetUrlPath](#geturlpath)|呼叫這個方法來取得的 URL 路徑。|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|呼叫這個方法，以取得 URL 路徑長度。|  
|[CUrl::GetUserName](#getusername)|呼叫此方法以從 URL 取得使用者名稱。|  
|[CUrl::GetUserNameLength](#getusernamelength)|呼叫這個方法來取得使用者名稱的長度。|  
|[CUrl::SetExtraInfo](#setextrainfo)|呼叫這個方法來設定額外的資訊 (例如*文字*或 #*文字*) 的 url。|  
|[CUrl::SetHostName](#sethostname)|呼叫這個方法來設定主機名稱。|  
|[CUrl::SetPassword](#setpassword)|呼叫這個方法來設定密碼。|  
|[CUrl::SetPortNumber](#setportnumber)|呼叫這個方法來設定 ATL_URL_PORT 方面的連接埠號碼。|  
|[CUrl::SetScheme](#setscheme)|呼叫這個方法來設定 URL 配置。|  
|[CUrl::SetSchemeName](#setschemename)|呼叫這個方法來設定 URL 配置名稱。|  
|[CUrl::SetUrlPath](#seturlpath)|呼叫這個方法來設定的 URL 路徑。|  
|[CUrl::SetUserName](#setusername)|呼叫這個方法來設定使用者名稱。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|指派指定`CUrl`物件與目前`CUrl`物件。|  
  
## <a name="remarks"></a>備註  
 `CUrl`可讓您操作的 URL，例如路徑或連接埠的數字欄位。 `CUrl`了解下列形式的 Url:  
  
 \<配置 >: / /\<UserName >:\<密碼 > @\<主機名稱 >:\<通訊埠編號 > /\<UrlPath >\<ExtraInfo >  
  
 （某些欄位是選擇性的）。此 URL 為例︰  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl)剖析它，如下所示︰  
  
-   配置:"http"或[ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   使用者名稱:"someone"  
  
-   密碼: 「 密碼 」  
  
-   主機名稱:"www.microsoft.com"  
  
-   通訊埠編號︰ 80  
  
-   UrlPath: 「 visualc/stuff.htm 」  
  
-   ExtraInfo: 「 #contents 」  
  
 若要操作 UrlPath 欄位 （例如），您可以使用[GetUrlPath](#geturlpath)， [GetUrlPathLength](#geturlpathlength)，和[SetUrlPath](#seturlpath)。 您可以使用[CreateUrl](#createurl)建立完整的 URL 字串。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="canonicalize"></a>CUrl::Canonicalize  
 呼叫這個方法，將 URL 字串轉換成標準格式。  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 控制規範化旗標。 如果未不指定任何旗標 ( `dwFlags` = 0)，方法會將所有 unsafe 字元和中繼順序 (例如\\。，\...，和\\...) 來逸出序列。 `dwFlags`可以是下列值之一︰  
  
-   ATL_URL_BROWSER_MODE︰ 不會編碼或解碼字元之後"#"或"」 並不會移除尾端空白之後"」。 如果未指定此值，整個 URL 編碼，並移除尾端空白字元。  
  
-   ATL_URL _DECODE︰ 將所有 %xx 序列都轉換成字元之前在剖析 URL,，包括逸出序列。  
  
-   ATL_URL _ENCODE_PERCENT︰ 編碼遇到任何百分比符號。 根據預設，不會編碼百分比符號。  
  
-   ATL_URL _ENCODE_SPACES_ONLY︰ 空間只會將編碼。  
  
-   ATL_URL _NO_ENCODE︰ 不會轉換成逸出序列不安全的字元。  
  
-   ATL_URL _NO_META︰ 不會移除中繼序列 (例如"。"和"..") 從 URL。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 轉換成標準格式，包括將 unsafe 字元和逸出序列的空格轉換。  
  
##  <a name="clear"></a>CUrl::Clear  
 呼叫此方法，以清除所有 URL 的欄位。  
  
```
inline void Clear() throw();
```  
  
##  <a name="crackurl"></a>CUrl::CrackUrl  
 呼叫這個方法來解碼並剖析 URL。  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszUrl`  
 URL。  
  
 `dwFlags`  
 指定要轉換中的所有逸出字元的 ATL_URL_DECODE 或 ATL_URL_ESCAPE`lpszUrl`設為實際值在剖析之後。 （在 Visual c + + 2005 之前, ATL_URL_DECODE 轉換所有逸出字元剖析之前）。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="createurl"></a>CUrl::CreateUrl  
 這個方法會建構從 CUrl 物件的元件欄位的 URL 字串。  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszUrl*  
 字串緩衝區，以保存完整的 URL 字串。  
  
 `pdwMaxLength`  
 最大長度*lpszUrl*字串緩衝區。  
  
 `dwFlags`  
 指定要轉換中的所有逸出字元 ATL_URL_ESCAPE *lpszUrl*為實際值。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會附加個別的欄位，才能建構完整的 URL 字串使用下列格式︰  
  
 **\<配置 >: / /\<使用者 >:\<傳遞 > @\<網域 >:\<連接埠 >\<路徑 >\<額外 >**  
  
 當呼叫這個方法，`pdwMaxLength`參數應該一開始包含所參考的字串緩衝區的最大長度*lpszUrl*參數。 值`pdwMaxLength`參數會以更新 URL 字串的實際長度。  
  
### <a name="example"></a>範例  
 這個範例會示範建立 CUrl 物件，並擷取其 URL 字串  
  
 [!code-cpp[NVC_ATL_Utilities #&133;](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="curl"></a>CUrl::CUrl  
 建構函式。  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>參數  
 `urlThat`  
 `CUrl`物件複製到建立 URL。  
  
##  <a name="dtor"></a>CUrl:: ~ CUrl  
 解構函式。  
  
```
~CUrl() throw();
```  
  
##  <a name="getextrainfo"></a>CUrl::GetExtraInfo  
 呼叫這個方法來取得額外資訊 (例如*文字*或 #*文字*) 從 URL。  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回字串，包含額外的資訊。  
  
##  <a name="getextrainfolength"></a>CUrl::GetExtraInfoLength  
 呼叫這個方法來取得額外資訊的長度 (例如*文字*或 #*文字*) 從 URL 擷取。  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回包含額外資訊的字串長度。  
  
##  <a name="gethostname"></a>CUrl::GetHostName  
 呼叫此方法以從 URL 取得主機名稱。  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回主機名稱。  
  
##  <a name="gethostnamelength"></a>CUrl::GetHostNameLength  
 呼叫這個方法，以取得主機名稱的長度。  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回主機名稱的長度。  
  
##  <a name="getpassword"></a>CUrl::GetPassword  
 呼叫此方法以從 URL 取得密碼。  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回密碼。  
  
##  <a name="getpasswordlength"></a>CUrl::GetPasswordLength  
 呼叫這個方法，以取得密碼的長度。  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的密碼長度。  
  
##  <a name="getportnumber"></a>CUrl::GetPortNumber  
 呼叫這個方法，以取得連接埠號碼。  
  
```
inline ATL_URL_PORT GetPortNumber() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的連接埠號碼。  
  
##  <a name="getscheme"></a>CUrl::GetScheme  
 呼叫這個方法，以取得 URL 配置。  
  
```
inline ATL_URL_SCHEME GetScheme() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回[ATL_URL_SCHEME](atl-url-scheme-enum.md)值，描述 URL 的配置。  
  
##  <a name="getschemename"></a>CUrl::GetSchemeName  
 呼叫這個方法，以取得 URL 的配置名稱。  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 URL 配置名稱 （例如"http"或"ftp"）。  
  
##  <a name="getschemenamelength"></a>CUrl::GetSchemeNameLength  
 呼叫這個方法，以取得 URL 的配置名稱的長度。  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 URL 結構描述名稱的長度。  
  
##  <a name="geturllength"></a>CUrl::GetUrlLength  
 呼叫這個方法，以取得 URL 的長度。  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 URL 長度。  
  
##  <a name="geturlpath"></a>CUrl::GetUrlPath  
 呼叫這個方法來取得的 URL 路徑。  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 URL 路徑。  
  
##  <a name="geturlpathlength"></a>CUrl::GetUrlPathLength  
 呼叫這個方法，以取得 URL 路徑長度。  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 URL 路徑長度。  
  
##  <a name="getusername"></a>CUrl::GetUserName  
 呼叫此方法以從 URL 取得使用者名稱。  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回使用者名稱。  
  
##  <a name="getusernamelength"></a>CUrl::GetUserNameLength  
 呼叫這個方法來取得使用者名稱的長度。  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回使用者名稱的長度。  
  
##  <a name="operator_eq"></a>CUrl::operator =  
 指派指定`CUrl`物件與目前`CUrl`物件。  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>參數  
 `urlThat`  
 `CUrl`物件複製到目前的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回目前物件的參考。  
  
##  <a name="setextrainfo"></a>CUrl::SetExtraInfo  
 呼叫這個方法來設定額外的資訊 (例如*文字*或 #*文字*) 的 url。  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszInfo*  
 字串，包含要在 URL 中包含額外的資訊。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="sethostname"></a>CUrl::SetHostName  
 呼叫這個方法來設定主機名稱。  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszHost`  
 主機名稱。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setpassword"></a>CUrl::SetPassword  
 呼叫這個方法來設定密碼。  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszPass*  
 密碼。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setportnumber"></a>CUrl::SetPortNumber  
 呼叫這個方法來設定連接埠號碼。  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>參數  
 *nPrt*  
 連接埠號碼。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setscheme"></a>CUrl::SetScheme  
 呼叫這個方法來設定 URL 配置。  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>參數  
 `nScheme`  
 其中一個[ATL_URL_SCHEME](atl-url-scheme-enum.md)配置的值。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您也可以依名稱設定配置 (請參閱[CUrl::SetSchemeName](#setschemename))。  
  
##  <a name="setschemename"></a>CUrl::SetSchemeName  
 呼叫這個方法來設定 URL 配置名稱。  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszSchm*  
 URL 配置名稱。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您也可以藉由設定配置[ATL_URL_SCHEME](atl-url-scheme-enum.md)常數 (請參閱[CUrl::SetScheme](#setscheme))。  
  
##  <a name="seturlpath"></a>CUrl::SetUrlPath  
 呼叫這個方法來設定的 URL 路徑。  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszPath`  
 URL 路徑。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="setusername"></a>CUrl::SetUserName  
 呼叫這個方法來設定使用者名稱。  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszUser*  
 使用者名稱。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)

