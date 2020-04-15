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
ms.openlocfilehash: 01810c16ff3e7fbc930983b9a52dc3a80f779f14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331031"
---
# <a name="cregkey-class"></a>CRegKey 類別

此類提供用於操作系統註冊表中的條目的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CRegKey
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRegKey:CRegKey](#cregkey)|建構函式。|
|[CRegKey:*CRegKey](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRegKey::附加](#attach)|呼叫此方法[透過m_hKey成員](#m_hkey)句柄設定為將`hKey``CRegKey`HKEY附加到物件。|
|[CRegKey:關閉](#close)|呼叫此方法以釋放[m_hKey](#m_hkey)成員句柄並將其設定為 NULL。|
|[CRegKey:建立](#create)|呼叫此方法以建立指定的密鑰(如果該鍵不存在為`hKeyParent`的子鍵)。|
|[CRegKey::DeleteSubKey](#deletesubkey)|呼叫此方法從註冊表中刪除指定的密鑰。|
|[CRegKey::Delete價值](#deletevalue)|呼叫此方法從[m_hKey](#m_hkey)中刪除值欄位。|
|[CRegKey::D埃塔奇](#detach)|呼叫此方法以將[m_hKey](#m_hkey)成員句柄從物件中分離`CRegKey`出來,`m_hKey`並設定為 NULL。|
|[CregKey::枚舉鍵](#enumkey)|調用此方法以枚舉打開註冊表項的子鍵。|
|[CRegKey::沖洗](#flush)|調用此方法將打開註冊表項的所有屬性寫入註冊表。|
|[CRegKey:抓取金鑰安全](#getkeysecurity)|呼叫此方法以檢索保護打開註冊表項的安全描述符的副本。|
|[CRegKey::通知更改鍵值](#notifychangekeyvalue)|此方法通知調用方對打開註冊表項的屬性或內容的更改。|
|[CRegKey::開啟](#open)|呼叫此方法以開啟指定的金鑰並將[m_hKey](#m_hkey)設定為此金鑰的句柄。|
|[CRegKey::查詢二元值](#querybinaryvalue)|調用此方法以檢索指定值名稱的二進位數據。|
|[CregKey::查詢DWORD值](#querydwordvalue)|調用此方法以檢索指定值名稱的 DWORD 資料。|
|[CregKey::查詢GUID值](#queryguidvalue)|呼叫此方法以檢索指定值名稱的 GUID 資料。|
|[CregKey::查詢多字串值](#querymultistringvalue)|呼叫此方法以檢索指定值名稱的多字串資料。|
|[CregKey::查詢QWORD值](#queryqwordvalue)|調用此方法以檢索指定值名稱的 QWORD 資料。|
|[CRegKey::查詢字串值](#querystringvalue)|呼叫此方法以檢索指定值名稱的字串資料。|
|[CRegKey::查詢值](#queryvalue)|調用此方法以檢索[m_hKey](#m_hkey)的指定值欄位的數據。 此方法的早期版本不再受支援,並標記為ATL_DEPRECATED。|
|[CRegKey::重新詛咒刪除金鑰](#recursedeletekey)|呼叫此方法從註冊表中刪除指定的密鑰,並顯式刪除任何子鍵。|
|[CRegKey::設定Binary值](#setbinaryvalue)|調用此方法以設置註冊表項的二進位值。|
|[CregKey::設定DWORD值](#setdwordvalue)|調用此方法以設置註冊表項的 DWORD 值。|
|[CRegKey::SetGUID值](#setguidvalue)|調用此方法以設置註冊表項的 GUID 值。|
|[CRegKey::設定金鑰安全性](#setkeysecurity)|調用此方法以設置註冊表項的安全性。|
|[CRegKey::設定鍵值](#setkeyvalue)|呼叫此方法將資料儲存在指定金鑰的指定值欄位中。|
|[CRegKey::設定多字串值](#setmultistringvalue)|呼叫此方法以設定註冊表項的多字串值。|
|[CRegKey::設定QWORD值](#setqwordvalue)|調用此方法以設置註冊表項的 QWORD 值。|
|[CRegKey::設定字串值](#setstringvalue)|呼叫此方法以設定註冊表項的字串值。|
|[CRegKey::設定價值](#setvalue)|呼叫此方法將資料儲存在指定的值欄位中[m_hKey](#m_hkey)。 此方法的早期版本不再受支援,並標記為ATL_DEPRECATED。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRegKey::管理員HKEY](#operator_hkey)|將`CRegKey`物件轉換為 HKEY。|
|[CRegKey::運算符 |](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRegKey:m_hKey](#m_hkey)|包含與對象關聯的註冊表項`CRegKey`的句柄。|
|[CRegKey:m_pTM](#m_ptm)|指向`CAtlTransactionManager`物件的指標|

## <a name="remarks"></a>備註

`CRegKey`提供了在系統註冊表中創建和刪除鍵和值的方法。 註冊表包含系統元件的特定於安裝的定義集,例如軟體版本號、已安裝硬體的邏輯到物理映射以及 COM 物件。

`CRegKey`為給定的計算機提供到系統註冊表的程式設計介面。 例如,要打開特定的註冊表項,請呼叫`CRegKey::Open`。 要檢查或修改資料值,請分別`CRegKey::QueryValue`呼叫`CRegKey::SetValue`或 。 要關閉金鑰,請呼叫`CRegKey::Close`。

關閉金鑰時,其註冊表數據將寫入(刷新)到硬碟。 這個程序可能需要幾秒鐘。 如果應用程式必須顯式將註冊表數據寫入硬碟,則可以調用[RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32 函數。 但是,`RegFlushKey`使用許多系統資源,並且僅在絕對必要時才應調用。

> [!IMPORTANT]
> 允許調用方指定註冊表位置的任何方法都有可能讀取無法信任的數據。 使用[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)的方法應考慮此函數不顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CRegKey::附加

呼叫此方法透過`CRegKey`[m_hKey](#m_hkey)成員句柄設定為*hKey*將 HKEY 附加到物件。

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>參數

*h鍵*<br/>
註冊表項的句柄。

### <a name="remarks"></a>備註

`Attach`將斷言如果`m_hKey`為非 NULL。

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey:關閉

呼叫此方法以釋放[m_hKey](#m_hkey)成員句柄並將其設定為 NULL。

```
LONG Close() throw();
```

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS;否則返回錯誤值。

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey:建立

呼叫此方法以建立指定的密鑰(如果它不存在為*hKeyParent*的子鍵)。

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

*hKey父*<br/>
打開鍵的句柄。

*lpszKey名稱*<br/>
指定要建立或打開的鍵的名稱。 此名稱必須是*hKeyParent*的子鍵。

*lpszClass*<br/>
指定要建立或打開的鍵的類。 默認值為REG_NONE。

*dwOptions*<br/>
鍵的選項。 默認值為REG_OPTION_NON_VOLATILE。 有關可能的值和說明的清單,請參閱 Windows SDK 中的[RegCreateKeyEx。](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw)

*薩姆·阿喬*<br/>
密鑰的安全訪問。 默認值為KEY_READ&#124;KEY_WRITE。 有關可能的值和說明的清單,請參閱`RegCreateKeyEx`。

*lpSecattr*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標,指示密鑰的句柄是否可以由子進程繼承。 預設情況下,此參數為 NULL(表示無法繼承句柄)。

*lpdw 處理*<br/>
[出]如果非 NULL,則檢索REG_CREATED_NEW_KEY(如果金鑰不存在並創建)或REG_OPENED_EXISTING_KEY(如果金鑰存在且已打開)。

### <a name="return-value"></a>傳回值

如果成功,返回ERROR_SUCCESS並打開密鑰。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

`Create`將[m_hKey](#m_hkey)成員設置為此鍵的句柄。

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey:CRegKey

建構函式。

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
`CRegKey` 物件的參考。

*h鍵*<br/>
註冊表項的句柄。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

建立新 `CRegKey` 物件。 可以從現有`CRegKey`物件或從句柄創建物件,也可以從註冊表項創建物件。

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey:*CRegKey

解構函式。

```
~CRegKey() throw();
```

### <a name="remarks"></a>備註

析構函數釋放`m_hKey`。

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey::DeleteSubKey

呼叫此方法從註冊表中刪除指定的密鑰。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>參數

*lpszSubkey*<br/>
指定要刪除的鍵的名稱。 此名稱必須是[m_hKey](#m_hkey)的子鍵。

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

`DeleteSubKey`只能刪除沒有子鍵的金鑰。 如果金鑰具有子鍵,請改為調用[「重新詛咒刪除密鑰](#recursedeletekey)」。

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey::Delete價值

呼叫此方法從[m_hKey](#m_hkey)中刪除值欄位。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>參數

*lpszValue*<br/>
指定要刪除的值欄位。

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey::D埃塔奇

呼叫此方法以將[m_hKey](#m_hkey)成員句柄從物件中分離`CRegKey`出來,`m_hKey`並設定為 NULL。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>傳回值

與`CRegKey`物件關聯的 HKEY。

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CregKey::枚舉鍵

調用此方法以枚舉打開註冊表項的子鍵。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>參數

*iIndex*<br/>
子鍵索引。 此參數對於第一個調用應為零,然後為後續調用遞增

*pszName*<br/>
指向接收子鍵名稱(包括終止空字元)的緩衝區的指標。 只有子鍵的名稱複製到緩衝區,而不是完整鍵層次結構。

*pn名稱長度*<br/>
指定*pszName*參數指定的緩衝區的大小(在 TCHAR 中)的變數的指標。 此大小應包括終止空字元。 當方法返回時 *,pnNameLength*指向的變數包含存儲在緩衝區中的字元數。 返回的計數不包括終止空字元。

*pftLast 寫入時間*<br/>
指向接收上次寫入枚舉子鍵時間的變數的指標。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

要枚舉子鍵,請`CRegKey::EnumKey`調用索引為零。 增加索引值並重複,直到方法返回ERROR_NO_MORE_ITEMS。 有關詳細資訊,請參閱 Windows SDK 中的[RegEnumKeyEx。](/windows/win32/api/winreg/nf-winreg-regenumkeyexw)

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey::沖洗

調用此方法將打開註冊表項的所有屬性寫入註冊表。

```
LONG Flush() throw();
```

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[RegEnumFlush。](/windows/win32/api/winreg/nf-winreg-regflushkey)

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CRegKey:抓取金鑰安全

呼叫此方法以檢索保護打開註冊表項的安全描述符的副本。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
指示請求的安全資訊[的SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)值。

*Psd*<br/>
指向接收請求的安全描述符副本的緩衝區的指標。

*pn位元組*<br/>
以位元組為單位的緩衝區的大小(以位元組為單位)指向*sd*。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值為非零錯誤代碼,在 WINERROR 中定義。H。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[RegGetKey 安全](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity)。

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey:m_hKey

包含與對象關聯的註冊表項`CRegKey`的句柄。

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey:m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CRegKey::通知更改鍵值

此方法通知調用方對打開註冊表項的屬性或內容的更改。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>參數

*b觀察子樹*<br/>
指定指示是報告指定金鑰及其所有子鍵中的更改的標誌,還是僅在指定鍵中報告更改。 如果此參數為 TRUE,則該方法將報告鍵及其子鍵中的更改。 如果參數為 FALSE,則方法僅報告鍵中的更改。

*dwNotifyFilter*<br/>
指定一組標誌,用於控制應報告哪些更改。 這裡可以是以下值的組合:

|值|意義|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|如果添加或刪除子鍵,則通知呼叫方。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知呼叫方對金鑰屬性的更改,例如安全描述符資訊。|
|REG_NOTIFY_CHANGE_LAST_SET|通知呼叫方對金鑰值的更改。 這可能包括添加或刪除值,或更改現有值。|
|REG_NOTIFY_CHANGE_SECURITY|通知呼叫方金鑰的安全描述符的更改。|

*hEvent*<br/>
事件的控制代碼。 如果*bAsync*參數為 TRUE,則該方法會立即返回,並通過向此事件發出信號來報告更改。 如果*bAsync*為 FALSE,則忽略*hEvent。*

*bAsync*<br/>
指定指示方法報告方式更改的標誌。 如果此參數為 TRUE,則該方法會立即返回,並通過向指定事件發出信號來報告更改。 當此參數為 FALSE 時,該方法在發生更改之前不會返回。 如果*hEvent*未指定有效事件,*則 bAsync*參數不能為 TRUE。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果刪除了指定的密鑰,此方法不會通知呼叫方。

有關詳細資訊和範例程式,請參閱[RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue)。

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey::開啟

呼叫此方法以開啟指定的金鑰並將[m_hKey](#m_hkey)設定為此金鑰的句柄。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>參數

*hKey父*<br/>
打開鍵的句柄。

*lpszKey名稱*<br/>
指定要建立或打開的鍵的名稱。 此名稱必須是*hKeyParent*的子鍵。

*薩姆·阿喬*<br/>
密鑰的安全訪問。 默認值為KEY_ALL_ACCESS。 有關可能的值和說明的清單,請參閱 Windows SDK 中的[RegCreateKeyEx。](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw)

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS;否則,在 WINERROR 中定義的非零錯誤值。H。

### <a name="remarks"></a>備註

如果*lpszKeyName*參數為 NULL 或指向`Open`空字串 ,則打開*hKeyParent*識別的鍵的新句柄,但不會關閉任何以前打開的句柄。

與[CRegKey::create](#create)`Open`不同, 如果不存在,將不會創建指定的密鑰。

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey::管理員HKEY

將`CRegKey`物件轉換為 HKEY。

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey::運算符 |

指派運算子。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要複製的鍵。

### <a name="return-value"></a>傳回值

返回對新鍵的引用。

### <a name="remarks"></a>備註

此運算符從其當前物件分離*密鑰*,並將其分配給`CRegKey`物件。

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CRegKey::查詢二元值

調用此方法以檢索指定值名稱的二進位數據。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。

*pValue*<br/>
指向接收值數據的緩衝區的指標。

*pn位元組*<br/>
指向指定*pValue*參數指向的緩衝區的大小(以位元組為單位)的變數的指標。 當方法返回時,此變數包含複製到緩衝區的數據的大小。

### <a name="return-value"></a>傳回值

如果該方法成功,將返回ERROR_SUCCESS。 如果方法無法讀取值,它將返回在 WINERROR 中定義的非零錯誤代碼。H。 如果引用的數據不是REG_BINARY類型,則返回ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

此方法使用`RegQueryValueEx`並確認返回正確的數據類型。 有關詳細資訊[,請參閱 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。 此外,此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函數不會顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CregKey::查詢DWORD值

調用此方法以檢索指定值名稱的 DWORD 資料。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。

*dwValue*<br/>
指向接收 DWORD 的緩衝區的指標。

### <a name="return-value"></a>傳回值

如果該方法成功,將返回ERROR_SUCCESS。 如果方法無法讀取值,它將返回在 WINERROR 中定義的非零錯誤代碼。H。 如果引用的數據不是REG_DWORD類型,則返回ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

此方法使用`RegQueryValueEx`並確認返回正確的數據類型。 有關詳細資訊[,請參閱 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。 此外,此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函數不會顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>CregKey::查詢GUID值

呼叫此方法以檢索指定值名稱的 GUID 資料。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。

*吉德價值*<br/>
指向接收 GUID 的變數的指標。

### <a name="return-value"></a>傳回值

如果該方法成功,將返回ERROR_SUCCESS。 如果方法無法讀取值,它將返回在 WINERROR 中定義的非零錯誤代碼。H。 如果引用的數據不是有效的 GUID,則返回ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

此方法使用`CRegKey::QueryStringValue`[CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)使用字串並將其轉換為 GUID。

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CregKey::查詢多字串值

呼叫此方法以檢索指定值名稱的多字串資料。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。

*pszValue*<br/>
指向接收多字串數據的緩衝區的指標。 多字串是 null 終止字串的陣列,由兩個空字元終止。

*pnChars*<br/>
以 TCHAR 表示的緩衝區大小(以 TR 形式)指向*pszValue*。 當方法返回時 *,pnChars*包含檢索的多字串(包括終止空字元)的大小(在 TCHA 中)。

### <a name="return-value"></a>傳回值

如果該方法成功,將返回ERROR_SUCCESS。 如果方法無法讀取值,它將返回在 WINERROR 中定義的非零錯誤代碼。H。 如果引用的數據不是REG_MULTI_SZ類型,則返回ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

此方法使用`RegQueryValueEx`並確認返回正確的數據類型。 有關詳細資訊[,請參閱 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。 此外,此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函數不會顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CregKey::查詢QWORD值

調用此方法以檢索指定值名稱的 QWORD 資料。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。

*qwValue*<br/>
指向接收QWORD的緩衝區的指標。

### <a name="return-value"></a>傳回值

如果該方法成功,將返回ERROR_SUCCESS。 如果方法無法讀取值,它將返回在 WINERROR 中定義的非零錯誤代碼。H。 如果引用的數據不是REG_QWORD類型,則返回ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

此方法使用`RegQueryValueEx`並確認返回正確的數據類型。 有關詳細資訊[,請參閱 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。 此外,此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函數不會顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CRegKey::查詢字串值

呼叫此方法以檢索指定值名稱的字串資料。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。

*pszValue*<br/>
指向接收字串數據的緩衝區的指標。

*pnChars*<br/>
以 TCHAR 表示的緩衝區大小(以 TR 形式)指向*pszValue*。 當方法返回時 *,pnChars*包含檢索的字串的大小(TCHAR),包括終止空字元。

### <a name="return-value"></a>傳回值

如果該方法成功,將返回ERROR_SUCCESS。 如果方法無法讀取值,它將返回在 WINERROR 中定義的非零錯誤代碼。H。 如果引用的數據不是REG_SZ類型,則返回ERROR_INVALID_DATA。 如果方法返回*ERROR_MORE_DATA,pnChars*等於零,而不是所需的緩衝區大小(以位元組為單位)。

### <a name="remarks"></a>備註

此方法使用`RegQueryValueEx`並確認返回正確的數據類型。 有關詳細資訊[,請參閱 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。 此外,此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函數不會顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey::查詢值

調用此方法以檢索[m_hKey](#m_hkey)的指定值欄位的數據。 此方法的早期版本不再受支援,並標記為ATL_DEPRECATED。

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

*pszValue名稱*<br/>
包含要查詢的值名稱的 null 連接端的字串的指標。 如果*pszValueName*為 NULL 或空字串" 則該方法將檢索金鑰未命名或預設值的類型和資料(如果有)。

*pdwType*<br/>
指向接收代碼的變數的指標,該代碼指示存儲在指定值中的數據類型。 如果不需要類型代碼,*則 pdwType*參數可以是 NULL。

*pData*<br/>
指向接收值數據的緩衝區的指標。 如果不需要資料,此參數可以是 NULL。

*pn位元組*<br/>
指向指定*pData*參數指向的緩衝區的大小(以位元組為單位)的變數的指標。 當方法返回時,此變數包含複製到*pData*的數據的大小。

*dwValue*<br/>
值欄位的數字數據。

*lpszValue名稱*<br/>
指定要查詢的值欄位。

*szValue*<br/>
值欄位的字串資料。

*pdw( A) Counts*<br/>
字串資料的大小。 其值最初設置為*szValue*緩衝區的大小。

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS;否則,在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

不再支援 的`QueryValue`兩 個原始版本,並標記為ATL_DEPRECATED。 如果使用這些窗體,編譯器將發出警告。

其餘方法稱為 RegQueryValueEx。

> [!IMPORTANT]
> 此方法允許調用方指定任何註冊表位置,可能讀取無法信任的數據。 此外,此方法使用的 RegQueryValueEx 函數不會顯式處理 NULL 終止的字串。 這兩個條件都應由調用代碼檢查。

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey::重新詛咒刪除金鑰

呼叫此方法從註冊表中刪除指定的密鑰,並顯式刪除任何子鍵。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>參數

*lpszKey*<br/>
指定要刪除的鍵的名稱。 此名稱必須是[m_hKey](#m_hkey)的子鍵。

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS;否則,在 WINERROR 中定義的非零錯誤值。H。

### <a name="remarks"></a>備註

如果金鑰具有子鍵,則必須調用此方法以刪除該密鑰。

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey::設定Binary值

調用此方法以設置註冊表項的二進位值。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果存在具有此名稱的值,則方法將其添加到鍵中。

*pValue*<br/>
指向包含要使用指定值名稱儲存的數據的緩衝區的指標。

*n 位元組*<br/>
指定*pValue*參數指向的資訊大小(以位元組為單位)。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)將值寫入註冊表。

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CregKey::設定DWORD值

調用此方法以設置註冊表項的 DWORD 值。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果存在具有此名稱的值,則方法將其添加到鍵中。

*dwValue*<br/>
要使用指定值名稱儲存的 DWORD 資料。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)將值寫入註冊表。

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>CRegKey::SetGUID值

調用此方法以設置註冊表項的 GUID 值。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果存在具有此名稱的值,則方法將其添加到鍵中。

*吉德價值*<br/>
引用要使用指定值名稱儲存的 GUID。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

此方法使用`CRegKey::SetStringValue` [StringFromGUID](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2)將 GUID 轉換為字串。

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CRegKey::設定鍵值

呼叫此方法將資料儲存在指定金鑰的指定值欄位中。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszKey名稱*<br/>
指定要建立或打開的鍵的名稱。 此名稱必須是[m_hKey](#m_hkey)的子鍵。

*lpszValue*<br/>
指定要存儲的數據。 此參數必須為非 NULL。

*lpszValue名稱*<br/>
指定要設定的值欄位。 如果鍵中不存在具有此名稱的值欄位,則添加該欄位。

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS;否則,在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

呼叫此方法以建立或開啟*lpszKeyName*金鑰,並將*lpszValue*資料儲存在*lpszValueName*值欄位中。

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey::設定金鑰安全性

調用此方法以設置註冊表項的安全性。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
指定要設置的安全描述符的元件。 該值可以是以下值的組合:

|值|意義|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|設置金鑰的任意存取控制清單 (DACL)。 金鑰必須具有WRITE_DAC訪問許可權,或者調用進程必須是物件的擁有者。|
|GROUP_SECURITY_INFORMATION|設置金鑰的主組安全識別碼 (SID)。 金鑰必須具有WRITE_OWNER訪問許可權,或者調用進程必須是物件的擁有者。|
|OWNER_SECURITY_INFORMATION|設置金鑰的所有者 SID。 密鑰必須具有WRITE_OWNER訪問許可權,或者調用進程必須是物件的所有者或啟用了SE_TAKE_OWNERSHIP_NAME許可權。|
|SACL_SECURITY_INFORMATION|設置金鑰的系統存取控制清單 (SACL)。 金鑰必須具有ACCESS_SYSTEM_SECURITY訪問許可權。 獲取此訪問許可權的正確方法是在調用方的當前訪問權杖中啟用SE_SECURITY_NAME[許可權](/windows/win32/secauthz/privileges),打開句柄以ACCESS_SYSTEM_SECURITY訪問,然後禁用該許可權。|

*Psd*<br/>
指向[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)結構的指標,該結構指定要為指定金鑰設置的安全屬性。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

設置金鑰的安全屬性。 有關詳細資訊[,請參閱 RegSetKey 安全](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity)。

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CRegKey::設定多字串值

呼叫此方法以設定註冊表項的多字串值。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果存在具有此名稱的值,則方法將其添加到鍵中。

*pszValue*<br/>
指向要使用指定值名稱儲存的多字串資料的指標。 多字串是 null 終止字串的陣列,由兩個空字元終止。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)將值寫入註冊表。

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey::設定QWORD值

調用此方法以設置註冊表項的 QWORD 值。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果存在具有此名稱的值,則方法將其添加到鍵中。

*qwValue*<br/>
要使用指定值名稱儲存的 QWORD 資料。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)將值寫入註冊表。

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey::設定字串值

呼叫此方法以設定註冊表項的字串值。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>參數

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果存在具有此名稱的值,則方法將其添加到鍵中。

*pszValue*<br/>
指向要使用指定值名稱儲存的字串資料的指標。

*dwType*<br/>
要寫入註冊表的字串的類型:REG_SZ(預設值)或REG_EXPAND_SZ(用於多字串)。

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值ERROR_SUCCESS。 如果方法失敗,返回值是在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)將值寫入註冊表。

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey::設定價值

呼叫此方法將資料儲存在指定的值欄位中[m_hKey](#m_hkey)。 此方法的早期版本不再受支援,並標記為ATL_DEPRECATED。

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

*pszValue名稱*<br/>
指向包含要設定的值名稱的字串的指標。 如果具有此名稱的值在鍵中不存在,則方法將其添加到鍵中。 如果*pszValueName*為 NULL 或空字串" 則該方法將設定鍵的未命名或預設值的類型和資料。

*dwType*<br/>
指定指示*pValue*參數指向的數據類型的代碼。

*pValue*<br/>
指向包含要使用指定值名稱儲存的數據的緩衝區的指標。

*n 位元組*<br/>
指定*pValue*參數指向的資訊大小(以位元組為單位)。 如果資料的類型為REG_SZ、REG_EXPAND_SZ或REG_MULTI_SZ,*則 nBytes*必須包括終止空字元的大小。

*hKey父*<br/>
打開鍵的句柄。

*lpszKey名稱*<br/>
指定要建立或打開的鍵的名稱。 此名稱必須是*hKeyParent*的子鍵。

*lpszValue*<br/>
指定要存儲的數據。 此參數必須為非 NULL。

*lpszValue名稱*<br/>
指定要設定的值欄位。 如果鍵中不存在具有此名稱的值欄位,則添加該欄位。

*dwValue*<br/>
指定要存儲的數據。

*b多*<br/>
如果為 false,則指示字串的類型為REG_SZ。 如果為 true,則指示該字串是類型REG_MULTI_SZ的多字串。

*nValueLen*<br/>
如果*bMulti*為 true,*則 nValueLen*是字元中的*lpszValue*字串的長度。 如果*bMulti*為 false,則值 -1 表示該方法將自動計算長度。

### <a name="return-value"></a>傳回值

如果成功,則返回ERROR_SUCCESS;否則,在 WINERROR 中定義的非零錯誤代碼。H。

### <a name="remarks"></a>備註

的兩個`SetValue`原始版本標記為ATL_DEPRECATED,不應再使用。 如果使用這些窗體,編譯器將發出警告。

第三種方法稱為[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)。

## <a name="see-also"></a>另請參閱

[DCOM 樣品](../../overview/visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
