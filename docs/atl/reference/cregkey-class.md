---
title: CRegKey 類別
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: bce5a16dd8d6564b6a0d3fa0344fe5cb2303764f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915795"
---
# <a name="cregkey-class"></a>CRegKey 類別

這個類別會提供方法來作業系統註冊表中的專案。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CRegKey
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|建構函式。|
|[CRegKey:: ~ CRegKey](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRegKey::Attach](#attach)|呼叫這個方法, 藉由將[m_hKey](#m_hkey)成員`CRegKey`控制碼設定為`hKey`, 將 HKEY 附加至物件。|
|[CRegKey:: Close](#close)|呼叫這個方法以釋放[m_hKey](#m_hkey)成員控制碼, 並將它設定為 Null。|
|[CRegKey::Create](#create)|如果指定的索引鍵不是以的子`hKeyParent`機碼形式存在, 請呼叫這個方法來建立。|
|[CRegKey::DeleteSubKey](#deletesubkey)|呼叫這個方法, 從登錄中移除指定的機碼。|
|[CRegKey::DeleteValue](#deletevalue)|呼叫這個方法, 從[m_hKey](#m_hkey)中移除值欄位。|
|[CRegKey::Detach](#detach)|呼叫這個方法, 從`CRegKey`物件卸離[m_hKey](#m_hkey)成員控制碼, 並`m_hKey`將設定為 Null。|
|[CRegKey::EnumKey](#enumkey)|呼叫這個方法來列舉 open 登錄機碼的子機碼。|
|[CRegKey:: Flush](#flush)|呼叫這個方法, 將開啟的登錄機碼的所有屬性寫入登錄中。|
|[CRegKey::GetKeySecurity](#getkeysecurity)|呼叫這個方法來抓取保護開啟登錄機碼的安全描述項複本。|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|這個方法會通知呼叫者有關已開啟之登錄機碼的屬性或內容的變更。|
|[CRegKey::Open](#open)|呼叫這個方法來開啟指定的索引鍵, 並將[m_hKey](#m_hkey)設定為這個機碼的控制碼。|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|呼叫這個方法, 以取得指定值名稱的二進位資料。|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|呼叫這個方法, 以取得指定值名稱的 DWORD 資料。|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|呼叫這個方法, 以取得指定值名稱的 GUID 資料。|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|呼叫這個方法, 以取得指定值名稱的 multistring 資料。|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|呼叫這個方法, 以取得指定值名稱的 QWORD 資料。|
|[CRegKey::QueryStringValue](#querystringvalue)|呼叫這個方法, 以取得指定值名稱的字串資料。|
|[CRegKey::QueryValue](#queryvalue)|呼叫這個方法, 以取得[m_hKey](#m_hkey)之指定值欄位的資料。 已不再支援此方法的舊版, 並將其標示為 ATL_DEPRECATED。|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|呼叫這個方法, 從登錄中移除指定的索引鍵, 並明確移除任何子機碼。|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|呼叫這個方法以設定登錄機碼的二進位值。|
|[CRegKey::SetDWORDValue](#setdwordvalue)|呼叫這個方法來設定登錄機碼的 DWORD 值。|
|[CRegKey::SetGUIDValue](#setguidvalue)|呼叫這個方法來設定登錄機碼的 GUID 值。|
|[CRegKey::SetKeySecurity](#setkeysecurity)|呼叫這個方法來設定登錄機碼的安全性。|
|[CRegKey::SetKeyValue](#setkeyvalue)|呼叫這個方法, 將資料儲存在指定之索引鍵的指定值欄位中。|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|呼叫這個方法以設定登錄機碼的 multistring 值。|
|[CRegKey::SetQWORDValue](#setqwordvalue)|呼叫這個方法來設定登錄機碼的 QWORD 值。|
|[CRegKey::SetStringValue](#setstringvalue)|呼叫這個方法以設定登錄機碼的字串值。|
|[CRegKey::SetValue](#setvalue)|呼叫這個方法, 將資料儲存在[m_hKey](#m_hkey)的指定值欄位中。 已不再支援此方法的舊版, 並將其標示為 ATL_DEPRECATED。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRegKey:: operator HKEY](#operator_hkey)|`CRegKey`將物件轉換成 HKEY。|
|[CRegKey:: operator =](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|包含與`CRegKey`物件相關聯之登錄機碼的控制碼。|
|[CRegKey::m_pTM](#m_ptm)|物件的`CAtlTransactionManager`指標|

## <a name="remarks"></a>備註

`CRegKey`提供方法來建立和刪除系統登錄中的機碼和值。 登錄包含系統元件的一組安裝特定定義, 例如軟體版本號碼、已安裝硬體的邏輯對實體對應, 以及 COM 物件。

`CRegKey`為指定的電腦提供系統登錄的程式設計介面。 例如, 若要開啟特定登錄機碼, 請`CRegKey::Open`呼叫。 若要取出或修改資料值, 請`CRegKey::QueryValue`分別`CRegKey::SetValue`呼叫或。 若要關閉金鑰, 請`CRegKey::Close`呼叫。

當您關閉金鑰時, 其登錄資料會寫入 (排清) 至硬碟。 此程式可能需要幾秒鐘的時間。 如果您的應用程式必須明確地將登錄資料寫入硬碟, 您可以呼叫[RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) Win32 函數。 不過, `RegFlushKey`會使用多個系統資源, 而且只有在絕對必要時才應呼叫。

> [!IMPORTANT]
>  任何可讓呼叫者指定登錄位置的方法, 都有可能讀取不受信任的資料。 使用[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)的方法應考慮此函式不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

## <a name="requirements"></a>需求

**標頭:** atlbase.h。h

##  <a name="attach"></a>CRegKey:: Attach

呼叫這個方法, 藉由將[m_hKey](#m_hkey)成員`CRegKey`控制碼設定為*HKEY*, 將 HKEY 附加至物件。

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>參數

*hKey*<br/>
登錄機碼的控制碼。

### <a name="remarks"></a>備註

`Attach`如果為非`m_hKey` Null, 則會判斷提示。

##  <a name="close"></a>CRegKey:: Close

呼叫這個方法以釋放[m_hKey](#m_hkey)成員控制碼, 並將它設定為 Null。

```
LONG Close() throw();
```

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS;否則會傳回錯誤值。

##  <a name="create"></a>CRegKey:: Create

呼叫此方法以建立指定的索引鍵 (如果它不是*hKeyParent*的子機碼)。

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>參數

*hKeyParent*<br/>
Open 鍵的控制碼。

*lpszKeyName*<br/>
指定要建立或開啟之金鑰的名稱。 此名稱必須是*hKeyParent*的子機碼。

*lpszClass*<br/>
指定要建立或開啟之金鑰的類別。 預設值為 REG_NONE。

*dwOptions*<br/>
索引鍵的選項。 預設值為 REG_OPTION_NON_VOLATILE。 如需可能值和描述的清單, 請參閱 Windows SDK 中的[RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) 。

*samDesired*<br/>
金鑰的安全性存取權。 預設值為 KEY_READ &#124; KEY_WRITE。 如需可能值和描述的清單, 請`RegCreateKeyEx`參閱。

*lpSecAttr*<br/>
[Security attributes 這個](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標, 指出子進程是否可以繼承索引鍵的控制碼。 根據預設, 此參數為 Null (表示無法繼承控制碼)。

*lpdwDisposition*<br/>
脫銷如果不是 Null, 則會抓取 REG_CREATED_NEW_KEY (如果索引鍵不存在且已建立) 或 REG_OPENED_EXISTING_KEY (如果索引鍵存在且已開啟)。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS 並開啟金鑰。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

`Create`將[m_hKey](#m_hkey)成員設定為此索引鍵的控制碼。

##  <a name="cregkey"></a>CRegKey::CRegKey

建構函式。

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
對 `CRegKey` 物件的參考。

*hKey*<br/>
登錄機碼的控制碼。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

建立新的 `CRegKey` 物件。 物件可以從現有`CRegKey`的物件或登錄機碼的控制碼建立。

##  <a name="dtor"></a>CRegKey:: ~ CRegKey

解構函式。

```
~CRegKey() throw();
```

### <a name="remarks"></a>備註

此函式`m_hKey`會發行。

##  <a name="deletesubkey"></a>CRegKey::D eleteSubKey

呼叫這個方法, 從登錄中移除指定的機碼。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>參數

*lpszSubKey*<br/>
指定要刪除之金鑰的名稱。 此名稱必須是[m_hKey](#m_hkey)的子機碼。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

`DeleteSubKey`只能刪除沒有子機碼的索引鍵。 如果索引鍵有子機碼, 請改為呼叫[RecurseDeleteKey](#recursedeletekey) 。

##  <a name="deletevalue"></a>CRegKey::D eleteValue

呼叫這個方法, 從[m_hKey](#m_hkey)中移除值欄位。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>參數

*lpszValue*<br/>
指定要移除的值欄位。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

##  <a name="detach"></a>CRegKey::D etach

呼叫這個方法, 從`CRegKey`物件卸離[m_hKey](#m_hkey)成員控制碼, 並`m_hKey`將設定為 Null。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>傳回值

與`CRegKey`物件相關聯的 HKEY。

##  <a name="enumkey"></a>CRegKey::EnumKey

呼叫這個方法來列舉 open 登錄機碼的子機碼。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>參數

*iIndex*<br/>
子機碼索引。 第一次呼叫時, 此參數應為零, 然後針對後續呼叫遞增

*pszName*<br/>
接收子機碼名稱之緩衝區的指標, 包括終止的 null 字元。 只有子機碼的名稱會複製到緩衝區, 而不是完整的金鑰階層。

*pnNameLength*<br/>
變數的指標, 指定*pszName*參數所指定之緩衝區的大小 (以 TCHARs)。 此大小應包含終止的 null 字元。 當此方法傳回時, *pnNameLength*所指向的變數會包含儲存在緩衝區中的字元數。 傳回的計數不包含終止的 null 字元。

*pftLastWriteTime*<br/>
變數的指標, 該變數會接收列舉子機碼上次被寫入的時間。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

若要列舉子機碼`CRegKey::EnumKey` , 請呼叫索引為零的。 遞增索引值並重複執行, 直到方法傳回 ERROR_NO_MORE_ITEMS。 如需詳細資訊, 請參閱 Windows SDK 中的[RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) 。

##  <a name="flush"></a>CRegKey:: Flush

呼叫這個方法, 將開啟的登錄機碼的所有屬性寫入登錄中。

```
LONG Flush() throw();
```

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) 。

##  <a name="getkeysecurity"></a>CRegKey::GetKeySecurity

呼叫這個方法來抓取保護開啟登錄機碼的安全描述項複本。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)值, 表示所要求的安全性資訊。

*psd*<br/>
接收要求的安全描述項複本之緩衝區的指標。

*pnBytes*<br/>
*Psd*所指向之緩衝區的大小 (以位元組為單位)。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為非零的錯誤碼, 在 WINERROR.H 中定義。H.

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity)。

##  <a name="m_hkey"></a>CRegKey::m_hKey

包含與`CRegKey`物件相關聯之登錄機碼的控制碼。

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>CRegKey::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue

這個方法會通知呼叫者有關已開啟之登錄機碼的屬性或內容的變更。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>參數

*bWatchSubtree*<br/>
指定一個旗標, 指出是否要在指定的索引鍵及其所有子機碼中, 或只報告指定之索引鍵中的變更。 如果此參數為 TRUE, 則方法會報告索引鍵和其子機碼中的變更。 如果參數為 FALSE, 則方法只會報告索引鍵中的變更。

*dwNotifyFilter*<br/>
指定一組旗標, 以控制應回報的變更。 這個參數可以是下列值的組合:

|值|意義|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|如果已新增或刪除子機碼, 請通知呼叫者。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知呼叫者對索引鍵的屬性進行變更, 例如安全描述項資訊。|
|REG_NOTIFY_CHANGE_LAST_SET|通知呼叫者有金鑰值的變更。 這可能包括新增或刪除值, 或變更現有的值。|
|REG_NOTIFY_CHANGE_SECURITY|通知呼叫者對金鑰的安全描述項有變更。|

*hEvent*<br/>
事件的控制代碼。 如果*bAsync*參數為 TRUE, 則此方法會立即傳回, 並藉由發出此事件的信號來回報變更。 如果*bAsync*為 FALSE, 則會忽略*hEvent* 。

*bAsync*<br/>
指定表示方法如何報告變更的旗標。 如果此參數為 TRUE, 方法會立即傳回, 並藉由發出指定事件的信號來回報變更。 當此參數為 FALSE 時, 除非發生變更, 否則方法不會傳回。 如果*hEvent*未指定有效的事件, *bAsync*參數就不能為 TRUE。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

> [!NOTE]
>  如果刪除指定的索引鍵, 這個方法不會通知呼叫端。

如需更多詳細資料和範例程式, 請參閱[RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue)。

##  <a name="open"></a>CRegKey:: Open

呼叫這個方法來開啟指定的索引鍵, 並將[m_hKey](#m_hkey)設定為這個機碼的控制碼。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>參數

*hKeyParent*<br/>
Open 鍵的控制碼。

*lpszKeyName*<br/>
指定要建立或開啟之金鑰的名稱。 此名稱必須是*hKeyParent*的子機碼。

*samDesired*<br/>
金鑰的安全性存取權。 預設值為 KEY_ALL_ACCESS。 如需可能值和描述的清單, 請參閱 Windows SDK 中的[RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) 。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS;否則, 會在 WINERROR.H 中定義非零的錯誤值。H.

### <a name="remarks"></a>備註

如果*lpszKeyName*參數是 Null 或指向空字串, `Open`則會開啟*hKeyParent*所識別之索引鍵的新控制碼, 但不會關閉任何先前開啟的控制碼。

不同于[CRegKey:: Create](#create), 如果不存在, `Open`將不會建立指定的索引鍵。

##  <a name="operator_hkey"></a>CRegKey:: operator HKEY

`CRegKey`將物件轉換成 HKEY。

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: operator =

指派運算子。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
要複製的索引鍵。

### <a name="return-value"></a>傳回值

傳回新索引鍵的參考。

### <a name="remarks"></a>備註

這個運算子會從目前的物件卸離索引*鍵*, 並`CRegKey`改為將它指派給物件。

##  <a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue

呼叫這個方法, 以取得指定值名稱的二進位資料。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。

*pValue*<br/>
接收值資料之緩衝區的指標。

*pnBytes*<br/>
變數的指標, 指定*pValue*參數所指向的緩衝區大小 (以位元組為單位)。 當此方法傳回時, 這個變數會包含複製到緩衝區的資料大小。

### <a name="return-value"></a>傳回值

如果方法成功, 則會傳回 ERROR_SUCCESS。 如果方法無法讀取值, 則會傳回 WINERROR.H 中定義的非零錯誤碼。H. 如果參考的資料不是 REG_BINARY 類型, 則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會使用`RegQueryValueEx`並確認傳回正確的資料類型。 如需詳細資訊, 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) 。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。 此外, 這個方法所使用的[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)函式並不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

##  <a name="querydwordvalue"></a>CRegKey::QueryDWORDValue

呼叫這個方法, 以取得指定值名稱的 DWORD 資料。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。

*dwValue*<br/>
接收 DWORD 之緩衝區的指標。

### <a name="return-value"></a>傳回值

如果方法成功, 則會傳回 ERROR_SUCCESS。 如果方法無法讀取值, 則會傳回 WINERROR.H 中定義的非零錯誤碼。H. 如果參考的資料不是 REG_DWORD 類型, 則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會使用`RegQueryValueEx`並確認傳回正確的資料類型。 如需詳細資訊, 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) 。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。 此外, 這個方法所使用的[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)函式並不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

##  <a name="queryguidvalue"></a>CRegKey::QueryGUIDValue

呼叫這個方法, 以取得指定值名稱的 GUID 資料。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。

*guidValue*<br/>
接收 GUID 之變數的指標。

### <a name="return-value"></a>傳回值

如果方法成功, 則會傳回 ERROR_SUCCESS。 如果方法無法讀取值, 則會傳回 WINERROR.H 中定義的非零錯誤碼。H. 如果參考的資料不是有效的 GUID, 則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會使用`CRegKey::QueryStringValue` , 並使用[CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring)將字串轉換成 GUID。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。

##  <a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue

呼叫這個方法, 以取得指定值名稱的 multistring 資料。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。

*pszValue*<br/>
接收 multistring 資料之緩衝區的指標。 Multistring 是以 null 結束的字串陣列, 以兩個 null 字元結束。

*pnChars*<br/>
*PszValue*所指向之緩衝區的大小 (以 TCHARs)。 當此方法傳回時, *pnChars*會包含所抓取 multistring 的大小 (以 TCHARs 為限), 包括終止的 null 字元。

### <a name="return-value"></a>傳回值

如果方法成功, 則會傳回 ERROR_SUCCESS。 如果方法無法讀取值, 則會傳回 WINERROR.H 中定義的非零錯誤碼。H. 如果參考的資料不是 REG_MULTI_SZ 類型, 則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會使用`RegQueryValueEx`並確認傳回正確的資料類型。 如需詳細資訊, 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) 。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。 此外, 這個方法所使用的[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)函式並不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

##  <a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

呼叫這個方法, 以取得指定值名稱的 QWORD 資料。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。

*qwValue*<br/>
接收 QWORD 之緩衝區的指標。

### <a name="return-value"></a>傳回值

如果方法成功, 則會傳回 ERROR_SUCCESS。 如果方法無法讀取值, 則會傳回 WINERROR.H 中定義的非零錯誤碼。H. 如果參考的資料不是 REG_QWORD 類型, 則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會使用`RegQueryValueEx`並確認傳回正確的資料類型。 如需詳細資訊, 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) 。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。 此外, 這個方法所使用的[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)函式並不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

##  <a name="querystringvalue"></a>CRegKey::QueryStringValue

呼叫這個方法, 以取得指定值名稱的字串資料。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。

*pszValue*<br/>
接收字串資料的緩衝區指標。

*pnChars*<br/>
*PszValue*所指向之緩衝區的大小 (以 TCHARs)。 當此方法傳回時, *pnChars*會包含所抓取字串的大小 (以 TCHARs 為結尾), 包括結束的 null 字元。

### <a name="return-value"></a>傳回值

如果方法成功, 則會傳回 ERROR_SUCCESS。 如果方法無法讀取值, 則會傳回 WINERROR.H 中定義的非零錯誤碼。H. 如果參考的資料不是 REG_SZ 類型, 則會傳回 ERROR_INVALID_DATA。 如果方法傳回 ERROR_MORE_DATA, 則*pnChars*等於零, 而不是所需的緩衝區大小 (以位元組為單位)。

### <a name="remarks"></a>備註

這個方法會使用`RegQueryValueEx`並確認傳回正確的資料類型。 如需詳細資訊, 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) 。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。 此外, 這個方法所使用的[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)函式並不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

##  <a name="queryvalue"></a>CRegKey::QueryValue

呼叫這個方法, 以取得[m_hKey](#m_hkey)之指定值欄位的資料。 已不再支援此方法的舊版, 並將其標示為 ATL_DEPRECATED。

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串指標, 其中包含要查詢之值的名稱。 如果*pszValueName*為 Null 或空字串 "", 則方法會針對索引鍵的未命名或預設值 (如果有的話), 抓取類型和資料。

*pdwType*<br/>
變數的指標, 該變數會接收程式碼, 指出儲存在指定值中的資料類型。 如果不需要型別程式碼, *pdwType*參數可以是 Null。

*pData*<br/>
接收值資料之緩衝區的指標。 如果資料不是必要的, 這個參數可以是 Null。

*pnBytes*<br/>
變數的指標, 指定*pData*參數所指向的緩衝區大小 (以位元組為單位)。 當此方法傳回時, 這個變數會包含複製到 PData 的資料大小 *。*

*dwValue*<br/>
值欄位的數值資料。

*lpszValueName*<br/>
指定要查詢的值欄位。

*szValue*<br/>
值欄位的字串資料。

*pdwCount*<br/>
字串資料的大小。 其值最初會設定為*szValue*緩衝區的大小。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS;否則, 會在 WINERROR.H 中定義非零的錯誤碼。H.

### <a name="remarks"></a>備註

`QueryValue`已不再支援的兩個原始版本, 並將其標示為 ATL_DEPRECATED。 如果使用這些表單, 編譯器會發出警告。

其餘的方法會呼叫 RegQueryValueEx。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置, 可能會讀取不受信任的資料。 此外, 這個方法所使用的 RegQueryValueEx 函式並不會明確處理 Null 終止的字串。 呼叫程式碼應檢查這兩個條件。

##  <a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

呼叫這個方法, 從登錄中移除指定的索引鍵, 並明確移除任何子機碼。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>參數

*lpszKey*<br/>
指定要刪除之金鑰的名稱。 此名稱必須是[m_hKey](#m_hkey)的子機碼。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS;否則, 會在 WINERROR.H 中定義非零的錯誤值。H.

### <a name="remarks"></a>備註

如果金鑰具有子機碼, 您必須呼叫這個方法來刪除金鑰。

##  <a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

呼叫這個方法以設定登錄機碼的二進位值。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未存在, 則方法會將它新增至索引鍵。

*pValue*<br/>
包含要以指定的值名稱儲存之資料的緩衝區指標。

*nBytes*<br/>
指定*pValue*參數所指向的資訊大小 (以位元組為單位)。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)將值寫入登錄。

##  <a name="setdwordvalue"></a>CRegKey:: SetDWORDValue

呼叫這個方法來設定登錄機碼的 DWORD 值。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未存在, 則方法會將它新增至索引鍵。

*dwValue*<br/>
要以指定的值名稱儲存的 DWORD 資料。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)將值寫入登錄。

##  <a name="setguidvalue"></a>CRegKey::SetGUIDValue

呼叫這個方法來設定登錄機碼的 GUID 值。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未存在, 則方法會將它新增至索引鍵。

*guidValue*<br/>
要以指定的值名稱儲存之 GUID 的參考。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用`CRegKey::SetStringValue` , 並使用[StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2)將 GUID 轉換成字串。

##  <a name="setkeyvalue"></a>CRegKey::SetKeyValue

呼叫這個方法, 將資料儲存在指定之索引鍵的指定值欄位中。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszKeyName*<br/>
指定要建立或開啟之金鑰的名稱。 此名稱必須是[m_hKey](#m_hkey)的子機碼。

*lpszValue*<br/>
指定要儲存的資料。 此參數必須為非 Null。

*lpszValueName*<br/>
指定要設定的值欄位。 如果具有此名稱的值欄位尚未存在於索引鍵中, 則會加入。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS;否則, 會在 WINERROR.H 中定義非零的錯誤碼。H.

### <a name="remarks"></a>備註

呼叫這個方法來建立或開啟*lpszKeyName*索引鍵, 並將*lpszValue*資料儲存在*lpszValueName*值欄位中。

##  <a name="setkeysecurity"></a>CRegKey::SetKeySecurity

呼叫這個方法來設定登錄機碼的安全性。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
指定要設定之安全描述項的元件。 此值可以是下列值的組合:

|值|意義|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|設定金鑰的任意存取控制清單 (DACL)。 金鑰必須具有 WRITE_DAC 存取權, 或者呼叫進程必須是物件的擁有者。|
|GROUP_SECURITY_INFORMATION|設定金鑰的主要群組安全識別碼 (SID)。 金鑰必須具有 WRITE_OWNER 存取權, 或者呼叫進程必須是物件的擁有者。|
|OWNER_SECURITY_INFORMATION|設定金鑰的擁有者 SID。 金鑰必須具有 WRITE_OWNER 存取權, 或呼叫進程必須是物件的擁有者, 或已啟用 SE_TAKE_OWNERSHIP_NAME 許可權。|
|SACL_SECURITY_INFORMATION|設定金鑰的系統存取控制清單 (SACL)。 金鑰必須具有 ACCESS_SYSTEM_SECURITY 存取權。 取得此存取權的正確方式是在呼叫端的目前存取權杖中啟用 SE_SECURITY_NAME[許可權](/windows/desktop/secauthz/privileges)、開啟 ACCESS_SYSTEM_SECURITY 存取的控制碼, 然後停用許可權。|

*psd*<br/>
[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor)結構的指標, 指定要針對指定的索引鍵設定的安全性屬性。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

設定金鑰的安全性屬性。 如需詳細資訊, 請參閱[RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity) 。

##  <a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue

呼叫這個方法以設定登錄機碼的 multistring 值。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未存在, 則方法會將它新增至索引鍵。

*pszValue*<br/>
要以指定的值名稱儲存的 multistring 資料指標。 Multistring 是以 null 結束的字串陣列, 以兩個 null 字元結束。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)將值寫入登錄。

##  <a name="setqwordvalue"></a>CRegKey::SetQWORDValue

呼叫這個方法來設定登錄機碼的 QWORD 值。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未存在, 則方法會將它新增至索引鍵。

*qwValue*<br/>
要以指定的值名稱儲存的 QWORD 資料。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)將值寫入登錄。

##  <a name="setstringvalue"></a>CRegKey:: SetStringValue

呼叫這個方法以設定登錄機碼的字串值。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未存在, 則方法會將它新增至索引鍵。

*pszValue*<br/>
要以指定的值名稱儲存之字串資料的指標。

*dwType*<br/>
要寫入登錄的字串類型: REG_SZ (預設值) 或 REG_EXPAND_SZ (適用于 multistring)。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 ERROR_SUCCESS。 如果方法失敗, 則傳回值為 WINERROR.H 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)將值寫入登錄。

##  <a name="setvalue"></a>CRegKey:: SetValue

呼叫這個方法, 將資料儲存在[m_hKey](#m_hkey)的指定值欄位中。 已不再支援此方法的舊版, 並將其標示為 ATL_DEPRECATED。

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串的指標, 包含要設定之值的名稱。 如果具有此名稱的值尚未出現在索引鍵中, 則方法會將它新增至索引鍵。 如果*pszValueName*為 Null 或空字串 "", 則方法會針對索引鍵的未命名或預設值設定類型和資料。

*dwType*<br/>
指定程式碼, 指出*pValue*參數所指向的資料類型。

*pValue*<br/>
包含要以指定的值名稱儲存之資料的緩衝區指標。

*nBytes*<br/>
指定*pValue*參數所指向的資訊大小 (以位元組為單位)。 如果資料屬於 REG_SZ、REG_EXPAND_SZ 或 REG_MULTI_SZ 類型, *nBytes*必須包含結束的 null 字元的大小。

*hKeyParent*<br/>
Open 鍵的控制碼。

*lpszKeyName*<br/>
指定要建立或開啟之金鑰的名稱。 此名稱必須是*hKeyParent*的子機碼。

*lpszValue*<br/>
指定要儲存的資料。 此參數必須為非 Null。

*lpszValueName*<br/>
指定要設定的值欄位。 如果具有此名稱的值欄位尚未存在於索引鍵中, 則會加入。

*dwValue*<br/>
指定要儲存的資料。

*bMulti*<br/>
如果為 false, 表示字串為 REG_SZ 類型。 若為 true, 表示字串為 REG_MULTI_SZ 類型的 multistring。

*nValueLen*<br/>
如果*bMulti*為 true, 則*nValueLen*是*lpszValue*字串的長度 (以字元為單位)。 如果*bMulti*為 false, 則-1 的值表示方法會自動計算長度。

### <a name="return-value"></a>傳回值

如果成功, 會傳回 ERROR_SUCCESS;否則, 會在 WINERROR.H 中定義非零的錯誤碼。H.

### <a name="remarks"></a>備註

的兩個原始版本`SetValue`會標示為 ATL_DEPRECATED, 且不應再使用。 如果使用這些表單, 編譯器會發出警告。

第三個方法會呼叫[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)。

## <a name="see-also"></a>另請參閱

[DCOM 範例](../../overview/visual-cpp-samples.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
