---
title: 庫爾類
ms.date: 05/06/2019
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
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330477"
---
# <a name="curl-class"></a>庫爾類

此類表示 URL。 它允許您獨立於其他元素操作 URL 的每個元素,無論是分析現有 URL 字串還是從頭開始構建字串。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CUrl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[網址::C網址](#curl)|建構函式。|
|[網址:_CUrl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[庫爾::規範化](#canonicalize)|呼叫此方法將網址字串轉換為規範形式。|
|[網址::清除](#clear)|呼叫此方法以清除所有 URL 欄位。|
|[網址::裂紋](#crackurl)|呼叫此方法來解碼和分析 URL。|
|[網址::建立網址](#createurl)|呼叫此方法以創建 URL。|
|[網址:取得額外資訊](#getextrainfo)|呼叫此方法從網址取得額外資訊(如*文字*或 +*文字*)。|
|[網址:取得額外資訊長度](#getextrainfolength)|呼叫此方法取得從網址檢索的額外資訊(如*文字*或 #*文字*)的長度。|
|[網址:取得主機名稱](#gethostname)|調用此方法從 URL 獲取主機名。|
|[網址:取得主機名稱長度](#gethostnamelength)|調用此方法以獲取主機名的長度。|
|[網址:抓取密碼](#getpassword)|呼叫此方法從網址獲取密碼。|
|[網址:抓取密碼長度](#getpasswordlength)|調用此方法獲取密碼的長度。|
|[網址:抓取連接埠號](#getportnumber)|調用此方法以獲取埠號ATL_URL_PORT。|
|[網址:抓取機制](#getscheme)|呼叫此方法獲取 URL 方案。|
|[網址:抓取計畫名稱](#getschemename)|呼叫此方法取得網址方案名稱。|
|[網址:抓取方案名稱長度](#getschemenamelength)|呼叫此方法獲取 URL 方案名稱的長度。|
|[網址:抓取網址](#geturllength)|呼叫此方法以獲取 URL 長度。|
|[網址:抓取網址Path](#geturlpath)|呼叫此方法以獲取 URL 路徑。|
|[網址:抓取網址路徑長度](#geturlpathlength)|呼叫此方法以獲取 URL 路徑長度。|
|[網址:抓取使用者名稱](#getusername)|呼叫此方法從網址獲取使用者名。|
|[網址:抓取使用者名稱長度](#getusernamelength)|調用此方法以獲取使用者名的長度。|
|[網址::設定額外資訊](#setextrainfo)|呼叫此方法以設定網址的額外資訊(如*文字*或 #*文字*)。|
|[網址::設定主機名稱](#sethostname)|調用此方法以設置主機名。|
|[網址::設定密碼](#setpassword)|呼叫此方法以設定密碼。|
|[網址::設定連接埠號](#setportnumber)|調用此方法以按ATL_URL_PORT設置埠號。|
|[網址::設定機制](#setscheme)|呼叫此方法以設置網址方案。|
|[網址::設定機制名稱](#setschemename)|呼叫此方法以設定網址方案名稱。|
|[網址::設定網址路徑](#seturlpath)|呼叫此方法以設定網址 路徑。|
|[網址::設定使用者名稱](#setusername)|調用此方法以設置使用者名。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[網址::運算符 |](#operator_eq)|將指定`CUrl`物件分配給`CUrl`當前 物件。|

## <a name="remarks"></a>備註

`CUrl`允許您操作 URL 的欄位,如路徑或埠號。 `CUrl`瞭解以下形式的網址:

\<方案>://\<\<使用者名>:\@\<密碼>主機名>:\<連接埠號>/UrlPath\< \<>附加信息>

(某些欄位是可選的。例如,請考慮以下網址:

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[網址::Clack網址](#crackurl)解析它如下:

- 方案:「HTTP」或[ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- 使用者名:"某人"

- 密碼:"機密"

- 主機名:"`www.microsoft.com`"

- 連接埠號: 80

- UrlPath:"visualc/stuff.htm"

- 附加資訊:"#contents"

要操作網址Path 欄位(例如),可以使用[GetUrlPath、GetUrlPath](#geturlpath)[長度](#geturlpathlength)和[SetUrlPath](#seturlpath)。 您可以使用[CreateUrl](#createurl)建立完整的 URL 字串。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>庫爾::規範化

呼叫此方法將網址字串轉換為規範形式。

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
控制規範化的標誌。 如果未指定標誌 *(dwFlags* = 0),該方法將所有不安全的字元和元\\序列(如 .、* . 和\\.) 轉換為轉義序列。 *dwFlags*可以是以下值之一:

- ATL_URL_BROWSER_MODE:在"+"或""之後不編碼或解碼字元,也不會刪除""之後的尾隨空格。 如果未指定此值,則對整個 URL 進行編碼並刪除尾隨空格。

- ATL_URL_DECODE:在解析 URL 之前,將所有 %XX 序列轉換為字元,包括轉義序列。

- ATL_URL_ENCODE_PERCENT:對遇到的任何百分比符號進行編碼。 預設情況下,百分比符號未編碼。

- ATL_URL_ENCODE_SPACES_ONLY:僅對空格進行編碼。

- ATL_URL_NO_ENCODE:不將不安全的字元轉換為轉義序列。

- ATL_URL_NO_META:不從 URL 中刪除元序列(如"."和"..")。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

轉換為規範形式涉及將不安全的字元和空格轉換為轉義序列。

## <a name="curlclear"></a><a name="clear"></a>網址::清除

呼叫此方法以清除所有 URL 欄位。

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>網址::裂紋

呼叫此方法來解碼和分析 URL。

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*lpszUrl*<br/>
URL。

*dwFlags*<br/>
指定ATL_URL_DECODE或ATL_URL_ESCAPE,用於在分析後將*lpszUrl*中的所有轉義字元轉換為其實際值。 (在 Visual C++ 2005 之前,ATL_URL_DECODE在分析之前轉換了所有轉義字元。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="curlcreateurl"></a><a name="createurl"></a>網址::建立網址

此方法從 CUrl 物件的元件欄位建構 URL 字串。

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>參數

*lpszUrl*<br/>
用於保存完整 URL 字串的字串緩衝區。

*pdwMax 長度*<br/>
*lpszUrl*字串緩衝區的最大長度。

*dwFlags*<br/>
指定ATL_URL_ESCAPE將*lpszUrl*中的所有轉義字元轉換為其實際值。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此方法附加其單個字段,以便使用以下格式建構完整的 URL 字串:

**\<方案>://\<\<使用者>:\@\<通過>域>:\<連接\<埠>\<路徑>額外的>**

呼叫此方法時 *,pdwMaxLength 參數*最初應包含*lpszUrl*參數引用的字串緩衝區的最大長度。 *pdwMaxLength 參數*的值將隨 URL 字串的實際長度更新。

### <a name="example"></a>範例

此範例展示建立 CUrl 物件並檢索網址字串

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>網址::C網址

建構函式。

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>參數

*url*<br/>
要`CUrl`複製以創建 URL 的物件。

## <a name="curlcurl"></a><a name="dtor"></a>網址:_CUrl

解構函式。

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>網址:取得額外資訊

呼叫此方法從網址取得額外資訊(如*文字*或 +*文字*)。

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>傳回值

返回包含額外資訊的字串。

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>網址:取得額外資訊長度

呼叫此方法取得從網址檢索的額外資訊(如*文字*或 #*文字*)的長度。

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>傳回值

返回包含額外資訊的字串的長度。

## <a name="curlgethostname"></a><a name="gethostname"></a>網址:取得主機名稱

調用此方法從 URL 獲取主機名。

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>傳回值

返回主機名。

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>網址:取得主機名稱長度

調用此方法以獲取主機名的長度。

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>傳回值

返回主機名長度。

## <a name="curlgetpassword"></a><a name="getpassword"></a>網址:抓取密碼

呼叫此方法從網址獲取密碼。

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>傳回值

返回密碼。

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>網址:抓取密碼長度

調用此方法獲取密碼的長度。

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>傳回值

返回密碼長度。

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>網址:抓取連接埠號

調用此方法獲取埠號。

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>傳回值

返回埠號。

## <a name="curlgetscheme"></a><a name="getscheme"></a>網址:抓取機制

呼叫此方法獲取 URL 方案。

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>傳回值

傳回描述 URL 方案[的ATL_URL_SCHEME](atl-url-scheme-enum.md)值。

## <a name="curlgetschemename"></a><a name="getschemename"></a>網址:抓取計畫名稱

呼叫此方法取得網址方案名稱。

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>傳回值

返回 URL 方案名稱(如"HTTP" 或"ftp"

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>網址:抓取方案名稱長度

呼叫此方法獲取 URL 方案名稱的長度。

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>傳回值

返回 URL 方案名稱長度。

## <a name="curlgeturllength"></a><a name="geturllength"></a>網址:抓取網址

呼叫此方法以獲取 URL 長度。

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>傳回值

返回 URL 長度。

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>網址:抓取網址Path

呼叫此方法以獲取 URL 路徑。

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>傳回值

返回URL路徑。

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>網址:抓取網址路徑長度

呼叫此方法以獲取 URL 路徑長度。

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>傳回值

返回URL路徑長度。

## <a name="curlgetusername"></a><a name="getusername"></a>網址:抓取使用者名稱

呼叫此方法從網址獲取使用者名。

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>傳回值

返回使用者名。

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>網址:抓取使用者名稱長度

調用此方法以獲取使用者名的長度。

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>傳回值

返回使用者名長度。

## <a name="curloperator-"></a><a name="operator_eq"></a>網址::運算符 |

將指定`CUrl`物件分配給`CUrl`當前 物件。

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>參數

*url*<br/>
要`CUrl`複製到當前物件的物件。

### <a name="return-value"></a>傳回值

返回對當前物件的引用。

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>網址::設定額外資訊

呼叫此方法以設定網址的額外資訊(如*文字*或 #*文字*)。

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>參數

*lpszInfo*<br/>
包含要包含在網址中的額外資訊的字串。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="curlsethostname"></a><a name="sethostname"></a>網址::設定主機名稱

調用此方法以設置主機名。

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>參數

*lpszHost*<br/>
主機名稱。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="curlsetpassword"></a><a name="setpassword"></a>網址::設定密碼

呼叫此方法以設定密碼。

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>參數

*lpszPass*<br/>
密碼。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>網址::設定連接埠號

調用此方法以設置埠號。

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>參數

*nPrt*<br/>
連接埠號碼。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="curlsetscheme"></a><a name="setscheme"></a>網址::設定機制

呼叫此方法以設置網址方案。

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>參數

*NScheme*<br/>
方案[ATL_URL_SCHEME](atl-url-scheme-enum.md)值之一。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

您還可以按名稱設定方案(請參閱[Url::SetSchemeName)。](#setschemename)

## <a name="curlsetschemename"></a><a name="setschemename"></a>網址::設定機制名稱

呼叫此方法以設定網址方案名稱。

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>參數

*lpszSchm*<br/>
URL 方案名稱。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

您還可以使用[ATL_URL_SCHEME](atl-url-scheme-enum.md)常量來設置方案(請參閱[CUrl::SetScheme)。](#setscheme)

## <a name="curlseturlpath"></a><a name="seturlpath"></a>網址::設定網址路徑

呼叫此方法以設定網址 路徑。

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
URL 路徑。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="curlsetusername"></a><a name="setusername"></a>網址::設定使用者名稱

調用此方法以設置使用者名。

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>參數

*lpszUser*<br/>
使用者名稱。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)
