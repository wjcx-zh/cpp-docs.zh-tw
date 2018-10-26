---
title: CRegKey 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26861b11aafd4bfcd4f1d5a7cc618ed27b60e6b8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071176"
---
# <a name="cregkey-class"></a>CRegKey 類別

這個類別提供方法，以操作系統登錄中的項目。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

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
|[CRegKey::Attach](#attach)|呼叫這個方法來附加 HKEY`CRegKey`藉由設定物件[m_hKey](#m_hkey)成員的控制代碼`hKey`。|
|[CRegKey::Close](#close)|呼叫這個方法來釋放[m_hKey](#m_hkey)成員處理，並將它設定為 NULL。|
|[CRegKey::Create](#create)|呼叫這個方法來建立指定之索引鍵，如果它不存在的子機碼為`hKeyParent`。|
|[CRegKey::DeleteSubKey](#deletesubkey)|呼叫這個方法來移除登錄中指定的索引鍵。|
|[CRegKey::DeleteValue](#deletevalue)|呼叫這個方法來移除值欄位從[m_hKey](#m_hkey)。|
|[CRegKey::Detach](#detach)|呼叫這個方法來卸離[m_hKey](#m_hkey)成員控制代碼，從`CRegKey`物件，並設定`m_hKey`為 NULL。|
|[CRegKey::EnumKey](#enumkey)|呼叫這個方法來列舉開啟的登錄機碼的子機碼。|
|[CRegKey::Flush](#flush)|呼叫這個方法將所有開啟的登錄機碼的屬性寫入至登錄。|
|[CRegKey::GetKeySecurity](#getkeysecurity)|呼叫這個方法來擷取一份保護開啟登錄機碼的安全性描述元。|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|這個方法會通知呼叫端相關變更的屬性或開啟登錄機碼的內容。|
|[CRegKey::Open](#open)|呼叫這個方法來開啟指定的索引鍵，並設定[m_hKey](#m_hkey)這個機碼的控制代碼。|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|呼叫這個方法來擷取指定的值名稱的二進位資料。|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|呼叫這個方法來擷取指定的值名稱的 DWORD 資料。|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|呼叫這個方法來擷取指定的值名稱的 GUID 資料。|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|呼叫這個方法來擷取指定的值名稱的 multistring 資料。|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|呼叫這個方法來擷取指定的值名稱的 QWORD 資料。|
|[CRegKey::QueryStringValue](#querystringvalue)|呼叫這個方法來擷取指定的值名稱的字串資料。|
|[CRegKey::QueryValue](#queryvalue)|呼叫這個方法來擷取指定的值欄位的資料[m_hKey](#m_hkey)。 舊版的這個方法不受支援，並會標示為 ATL_DEPRECATED。|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|呼叫此方法以移除登錄中指定的索引鍵，並明確地移除任何子機碼。|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|呼叫此方法以設定登錄機碼的二進位值。|
|[CRegKey::SetDWORDValue](#setdwordvalue)|呼叫此方法以設定登錄機碼 DWORD 值。|
|[CRegKey::SetGUIDValue](#setguidvalue)|呼叫此方法以設定登錄機碼的 GUID 值。|
|[CRegKey::SetKeySecurity](#setkeysecurity)|呼叫此方法以設定登錄機碼的安全性。|
|[CRegKey::SetKeyValue](#setkeyvalue)|呼叫這個方法，以將資料儲存在指定的值欄位的指定索引鍵。|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|呼叫此方法以設定登錄機碼的 multistring 的值。|
|[CRegKey::SetQWORDValue](#setqwordvalue)|呼叫此方法以設定登錄機碼的 QWORD 值。|
|[CRegKey::SetStringValue](#setstringvalue)|呼叫此方法以設定登錄機碼的字串值。|
|[CRegKey::SetValue](#setvalue)|呼叫這個方法來將資料儲存在指定的值欄位[m_hKey](#m_hkey)。 舊版的這個方法不受支援，並會標示為 ATL_DEPRECATED。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|將轉換`CRegKey`HKEY 的物件。|
|[CRegKey::operator =](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|包含與相關聯的登錄機碼的控制代碼`CRegKey`物件。|
|[CRegKey::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件|

## <a name="remarks"></a>備註

`CRegKey` 提供方法來建立和刪除索引鍵和系統登錄中的值。 登錄包含的系統元件，例如軟體版本號碼、 安裝的硬體和 COM 物件的邏輯實體對應定義的安裝特定集合。

`CRegKey` 提供指定的電腦系統登錄的程式設計介面。 例如，若要開啟特定的登錄機碼，呼叫`CRegKey::Open`。 若要擷取或修改的資料值，呼叫`CRegKey::QueryValue`或`CRegKey::SetValue`分別。 若要關閉的機碼，請呼叫`CRegKey::Close`。

當您關閉的機碼時，其登錄資料會寫入 （清除） 的硬碟。 此程序可能需要幾秒鐘的時間。 如果您的應用程式必須明確登錄資料寫入硬碟，您可以呼叫[RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) Win32 函式。 不過，`RegFlushKey`使用多系統資源，並只在絕對必要時，應該呼叫。

> [!IMPORTANT]
>  任何方法，可讓呼叫端指定的登錄位置可能會讀取不可為受信任的資料。 使用方法，讓[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)應該列入考量，此函式不會明確處理都是 NULL 終止的字串。 這兩個條件應檢查呼叫程式碼。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="attach"></a>  CRegKey::Attach

呼叫這個方法來附加 HKEY`CRegKey`藉由設定物件[m_hKey](#m_hkey)成員的控制代碼*hKey*。

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>參數

*hKey*<br/>
登錄機碼的控制代碼。

### <a name="remarks"></a>備註

`Attach` 如果會判斷提示`m_hKey`為非 NULL。

##  <a name="close"></a>  CRegKey::Close

呼叫這個方法來釋放[m_hKey](#m_hkey)成員處理，並將它設定為 NULL。

```
LONG Close() throw();
```

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS;否則會傳回錯誤值。

##  <a name="create"></a>  CRegKey::Create

如果沒有為的子機碼，呼叫這個方法來建立指定之索引鍵*hKeyParent*。

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
開啟金鑰的控制代碼。

*lpszKeyName*<br/>
指定要建立或開啟金鑰的名稱。 此名稱必須是子機碼*hKeyParent*。

*lpszClass*<br/>
指定要建立或開啟的索引鍵類別。 REG_NONE 為預設值。

*dwOptions*<br/>
索引鍵的選項。 預設值是 REG_OPTION_NON_VOLATILE。 如需可能的值和描述的清單，請參閱 < [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) Windows SDK 中。

*samDesired*<br/>
金鑰安全性存取權。 預設值是 KEY_READ &#124; KEY_WRITE。 如需可能的值和描述的清單，請參閱`RegCreateKeyEx`。

*lpSecAttr*<br/>
指標[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)結構，表示金鑰的控制代碼是否可以由子處理序繼承。 根據預設，此參數為 NULL （亦即無法繼承控制代碼）。

*lpdwDisposition*<br/>
[out]如果不是 NULL，擷取 REG_CREATED_NEW_KEY （如果金鑰不存在，且已建立） 或 REG_OPENED_EXISTING_KEY （如果金鑰存在，且已開啟）。

### <a name="return-value"></a>傳回值

如果成功，傳回 ERROR_SUCCESS，並開啟金鑰。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

`Create` 設定[m_hKey](#m_hkey)這個機碼的控制代碼的成員。

##  <a name="cregkey"></a>  CRegKey::CRegKey

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
登錄機碼控制代碼。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

建立新的 `CRegKey` 物件。 物件可由從現有`CRegKey`物件，或從登錄機碼的控制代碼。

##  <a name="dtor"></a>  CRegKey:: ~ CRegKey

解構函式。

```
~CRegKey() throw();
```

### <a name="remarks"></a>備註

解構函式版本`m_hKey`。

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

呼叫這個方法來移除登錄中指定的索引鍵。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>參數

*lpszSubKey*<br/>
指定要刪除之索引鍵的名稱。 此名稱必須是子機碼[m_hKey](#m_hkey)。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

`DeleteSubKey` 只能刪除包含任何子機碼的機碼。 如果索引鍵有子機碼，呼叫[RecurseDeleteKey](#recursedeletekey)改。

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

呼叫這個方法來移除值欄位從[m_hKey](#m_hkey)。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>參數

*lpszValue*<br/>
指定要移除的值欄位。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

##  <a name="detach"></a>  CRegKey::Detach

呼叫這個方法來卸離[m_hKey](#m_hkey)成員控制代碼，從`CRegKey`物件，並設定`m_hKey`為 NULL。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>傳回值

與相關聯的 HKEY`CRegKey`物件。

##  <a name="enumkey"></a>  CRegKey::EnumKey

呼叫這個方法來列舉開啟的登錄機碼的子機碼。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>參數

*iIndex*<br/>
子機碼的索引。 這個參數應為零的第一次呼叫，然後會遞增以在後續呼叫

*pszName*<br/>
接收子機碼，包括結束的 null 字元的名稱之緩衝區的指標。 只有名稱的子機碼會複製到緩衝區，而不是完整金鑰階層。

*pnNameLength*<br/>
指標，TCHARs，所指定的緩衝區中指定的大小，而變數*pszName*參數。 這個大小應該包含結束的 null 字元。 此方法傳回時，所指向的變數*pnNameLength*包含儲存在緩衝區中的字元數。 傳回的計數不包含結束的 null 字元。

*pftLastWriteTime*<br/>
接收時間變數指標列舉子機碼上次被寫入。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

若要列舉子機碼，請呼叫`CRegKey::EnumKey`索引為零。 遞增的索引值，並重複，直到此方法會傳回 ERROR_NO_MORE_ITEMS 為止。 如需詳細資訊，請參閱 < [RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) Windows SDK 中。

##  <a name="flush"></a>  CRegKey::Flush

呼叫這個方法將所有開啟的登錄機碼的屬性寫入至登錄。

```
LONG Flush() throw();
```

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) Windows SDK 中。

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

呼叫這個方法來擷取一份保護開啟登錄機碼的安全性描述元。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)值，指出要求的安全性資訊。

*psd*<br/>
接收一份要求的安全性描述元的緩衝區指標。

*pnBytes*<br/>
大小，以位元組為單位所指向的緩衝區*psd*。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，傳回的值會是 WINERROR 中定義的非零錯誤碼。H.

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity)。

##  <a name="m_hkey"></a>  CRegKey::m_hKey

包含與相關聯的登錄機碼的控制代碼`CRegKey`物件。

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue

這個方法會通知呼叫端相關變更的屬性或開啟登錄機碼的內容。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>參數

*bWatchSubtree*<br/>
指定旗標，指出是否要在報告中指定的機碼及其所有子機碼，或只在指定的索引鍵中的變更。 如果此參數為 TRUE，則方法會報告機碼和其子機碼中的變更。 如果參數為 FALSE，則方法會報告變更只存在於索引鍵。

*dwNotifyFilter*<br/>
指定應該報告一組旗標，以控制哪些變更。 這個參數可以是下列值的組合：

|值|意義|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|如果新增或刪除子機碼時，請告知呼叫端。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知呼叫端的金鑰，例如安全性描述元資訊屬性的變更。|
|REG_NOTIFY_CHANGE_LAST_SET|通知呼叫端的索引鍵的值變更。 這可以包括新增或刪除某個值，或變更現有的值。|
|REG_NOTIFY_CHANGE_SECURITY|通知呼叫端的索引鍵的安全性描述元變更。|

*hEvent*<br/>
事件的控制代碼。 如果*bAsync*參數為 TRUE，則方法會立即傳回，並藉由發出訊號此事件報告變更。 如果*bAsync*為 FALSE 時， *hEvent*會被忽略。

*bAsync*<br/>
指定旗標，指出方法報告變更的方式。 如果此參數為 TRUE，此方法會立即傳回，並藉由發出訊號指定的事件會報告變更。 當此參數為 FALSE 時，已發生變更之前，不會傳回方法。 如果*hEvent*未指定有效的事件， *bAsync*參數不能是 TRUE。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

> [!NOTE]
>  這個方法不會通知呼叫端，如果刪除指定的索引鍵。

如需詳細資訊和範例程式，請參閱 < [RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue)。

##  <a name="open"></a>  CRegKey::Open

呼叫這個方法來開啟指定的索引鍵，並設定[m_hKey](#m_hkey)這個機碼的控制代碼。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>參數

*hKeyParent*<br/>
開啟金鑰的控制代碼。

*lpszKeyName*<br/>
指定要建立或開啟金鑰的名稱。 此名稱必須是子機碼*hKeyParent*。

*samDesired*<br/>
金鑰安全性存取權。 預設值是 KEY_ALL_ACCESS。 如需可能的值和描述的清單，請參閱 < [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) Windows SDK 中。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS;否則，WINERROR 中定義的非零的錯誤值。H.

### <a name="remarks"></a>備註

如果*lpszKeyName*參數為 NULL 或點為空字串，`Open`便會開啟新的控制代碼所識別的金鑰*hKeyParent*，但不會關閉任何先前開啟的控制代碼。

不同於[CRegKey::Create](#create)，`Open`如果不存在，則不會建立指定之索引鍵。

##  <a name="operator_hkey"></a>  CRegKey::operator HKEY

將轉換`CRegKey`HKEY 的物件。

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>  CRegKey::operator =

指派運算子。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
要複製的索引鍵。

### <a name="return-value"></a>傳回值

傳回新的索引鍵的參考。

### <a name="remarks"></a>備註

這個運算子會卸離*金鑰*從其目前的物件並將其指派給`CRegKey`物件。

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

呼叫這個方法來擷取指定的值名稱的二進位資料。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串，包含要查詢之值的名稱的指標。

*pValue*<br/>
接收值的資料緩衝區的指標。

*pnBytes*<br/>
變數所指定的大小，以位元組為單位的緩衝區指標所指向*pValue*參數。 方法傳回時，此變數包含資料複製到緩衝區的大小。

### <a name="return-value"></a>傳回值

如果方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取值，它會傳回 WINERROR 中定義的非零的錯誤碼。H. 如果參考資料不是 REG_BINARY 類型，則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會利用`RegQueryValueEx`，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)如需詳細資訊。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)這個方法所使用的函式不會明確處理都是 NULL 終止的字串。 這兩個條件應檢查呼叫程式碼。

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

呼叫這個方法來擷取指定的值名稱的 DWORD 資料。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串，包含要查詢之值的名稱的指標。

*dwValue*<br/>
接收 DWORD 的緩衝區指標。

### <a name="return-value"></a>傳回值

如果方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取值，它會傳回 WINERROR 中定義的非零的錯誤碼。H. 如果參考資料不是類型 REG_DWORD，則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會利用`RegQueryValueEx`，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)如需詳細資訊。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)這個方法所使用的函式不會明確處理都是 NULL 終止的字串。 這兩個條件應檢查呼叫程式碼。

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

呼叫這個方法來擷取指定的值名稱的 GUID 資料。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串，包含要查詢之值的名稱的指標。

*guidValue*<br/>
此變數會接收 GUID 的指標。

### <a name="return-value"></a>傳回值

如果方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取值，它會傳回 WINERROR 中定義的非零的錯誤碼。H. 如果參考資料不是有效的 GUID，則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會利用`CRegKey::QueryStringValue`並將字串轉換成 GUID，使用[CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring)。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

呼叫這個方法來擷取指定的值名稱的 multistring 資料。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串，包含要查詢之值的名稱的指標。

*pszValue*<br/>
接收 multistring 資料緩衝區的指標。 Multistring 是以 null 結尾的字串，由兩個 null 字元結束的陣列。

*pnChars*<br/>
大小，以 TCHARs，所指向的緩衝區*pszValue*。 方法傳回時， *pnChars*包含大小，以 TCHARs 的 multistring 擷取，包括結束的 null 字元。

### <a name="return-value"></a>傳回值

如果方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取值，它會傳回 WINERROR 中定義的非零的錯誤碼。H. 如果參考資料不是類型 REG_MULTI_SZ，則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會利用`RegQueryValueEx`，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)如需詳細資訊。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)這個方法所使用的函式不會明確處理都是 NULL 終止的字串。 這兩個條件應檢查呼叫程式碼。

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

呼叫這個方法來擷取指定的值名稱的 QWORD 資料。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串，包含要查詢之值的名稱的指標。

*qwValue*<br/>
接收 QWORD 的緩衝區指標。

### <a name="return-value"></a>傳回值

如果方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取值，它會傳回 WINERROR 中定義的非零的錯誤碼。H. 如果參考資料不是類型 REG_QWORD，則會傳回 ERROR_INVALID_DATA。

### <a name="remarks"></a>備註

這個方法會利用`RegQueryValueEx`，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)如需詳細資訊。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)這個方法所使用的函式不會明確處理都是 NULL 終止的字串。 這兩個條件應檢查呼叫程式碼。

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

呼叫這個方法來擷取指定的值名稱的字串資料。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
以 null 終止的字串，包含要查詢之值的名稱的指標。

*pszValue*<br/>
接收的字串資料的緩衝區指標。

*pnChars*<br/>
大小，以 TCHARs，所指向的緩衝區*pszValue*。 方法傳回時， *pnChars*包含大小，以 TCHARs，擷取，包括結束的 null 字元的字串。

### <a name="return-value"></a>傳回值

如果方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取值，它會傳回 WINERROR 中定義的非零的錯誤碼。H. 如果參考資料不是類型 REG_SZ，則會傳回 ERROR_INVALID_DATA。 如果此方法會傳回 ERROR_MORE_DATA， *pnChars*等於零，不是以位元組為單位的所需的緩衝區大小。

### <a name="remarks"></a>備註

這個方法會利用`RegQueryValueEx`，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)如需詳細資訊。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa)這個方法所使用的函式不會明確處理都是 NULL 終止的字串。 這兩個條件應檢查呼叫程式碼。

##  <a name="queryvalue"></a>  CRegKey::QueryValue

呼叫這個方法來擷取指定的值欄位的資料[m_hKey](#m_hkey)。 舊版的這個方法不受支援，並會標示為 ATL_DEPRECATED。

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
以 null 終止的字串，包含要查詢之值的名稱的指標。 如果*pszValueName*為 NULL 或空字串，""、 方法擷取的型別和索引鍵資料的未具名或預設值，如果有的話。

*pdwType*<br/>
此變數會接收代碼，表示指定的值中儲存的資料類型的指標。 *PdwType*參數可以是 NULL，如果不需要型別程式碼。

*pData*<br/>
接收值的資料緩衝區的指標。 這個參數可以是 NULL，如果不需要的資料。

*pnBytes*<br/>
變數所指定的大小，以位元組為單位的緩衝區指標所指向*pData*參數。 方法傳回時，此變數包含要複製的資料大小*pData。*

*dwValue*<br/>
[值] 欄位的數值資料。

*lpszValueName*<br/>
指定要查詢的 [值] 欄位。

*szValue*<br/>
[值] 欄位的字串資料。

*pdwCount*<br/>
字串資料的大小。 它的值一開始設定的大小*szValue*緩衝區。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS;否則，傳回非零的錯誤碼 WINERROR 中定義。H.

### <a name="remarks"></a>備註

兩個原始版本`QueryValue`不受支援，並會標示為 ATL_DEPRECATED。 如果這些表單的使用，編譯器會發出警告。

其餘的方法會呼叫 RegQueryValueEx。

> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外，這個方法所用的 RegQueryValueEx 函式不會明確處理字串，其為終止的 NULL。 這兩個條件應檢查呼叫程式碼。

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

呼叫此方法以移除登錄中指定的索引鍵，並明確地移除任何子機碼。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>參數

*lpszKey*<br/>
指定要刪除之索引鍵的名稱。 此名稱必須是子機碼[m_hKey](#m_hkey)。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS;否則，WINERROR 中定義的非零的錯誤值。H.

### <a name="remarks"></a>備註

如果索引鍵有子機碼，您必須呼叫這個方法，以刪除機碼。

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

呼叫此方法以設定登錄機碼的二進位值。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串，包含要設定的值名稱的指標。 如果具有此名稱的值尚未存在，則方法會將它新增至機碼。

*pValue*<br/>
包含具有指定的值名稱儲存資料之緩衝區的指標。

*nBytes*<br/>
指定的大小，以位元組為單位所指向的資訊*pValue*參數。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)寫入登錄值。

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

呼叫此方法以設定登錄機碼 DWORD 值。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串，包含要設定的值名稱的指標。 如果具有此名稱的值尚未存在，則方法會將它新增至機碼。

*dwValue*<br/>
要儲存指定的值名稱的 DWORD 資料。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)寫入登錄值。

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

呼叫此方法以設定登錄機碼的 GUID 值。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串，包含要設定的值名稱的指標。 如果具有此名稱的值尚未存在，則方法會將它新增至機碼。

*guidValue*<br/>
使用指定的值名稱儲存的 GUID 參考。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會利用`CRegKey::SetStringValue`並將 GUID 轉換為字串，使用[StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2)。

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

呼叫這個方法，以將資料儲存在指定的值欄位的指定索引鍵。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszKeyName*<br/>
指定要建立或開啟的索引鍵名稱。 此名稱必須是子機碼[m_hKey](#m_hkey)。

*lpszValue*<br/>
指定要儲存的資料。 這個參數必須為非 NULL。

*lpszValueName*<br/>
指定要設定的 [值] 欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS;否則，傳回非零的錯誤碼 WINERROR 中定義。H.

### <a name="remarks"></a>備註

呼叫這個方法來建立或開啟*lpszKeyName*鍵，並儲存*lpszValue*中的資料*lpszValueName*值欄位。

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

呼叫此方法以設定登錄機碼的安全性。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
指定的元件設定的安全性描述元。 值可以是下列值的組合：

|值|意義|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|設定索引鍵的判別存取控制清單 (DACL)。 此金鑰必須具備 WRITE_DAC 存取權，或呼叫的處理序必須是物件的擁有者。|
|GROUP_SECURITY_INFORMATION|設定索引鍵的主要群組安全性識別碼 (SID)。 此金鑰必須具備 WRITE_OWNER 存取，或呼叫的處理序必須是物件的擁有者。|
|OWNER_SECURITY_INFORMATION|設定金鑰的擁有者 SID。 此金鑰必須具備 WRITE_OWNER 存取，或呼叫的處理序必須是物件的擁有者或具有已啟用的 SE_TAKE_OWNERSHIP_NAME 權限。|
|SACL_SECURITY_INFORMATION|設定索引鍵的系統存取控制清單 (SACL)。 此金鑰必須具備 ACCESS_SYSTEM_SECURITY 存取。 若要取得此存取權的正確方式是啟用 SE_SECURITY_NAME[權限](https://msdn.microsoft.com/library/windows/desktop/aa379306)中呼叫端的目前的存取權杖，請在開啟 ACCESS_SYSTEM_SECURITY 存取的控制代碼，然後再停用的權限。|

*psd*<br/>
指標[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)結構，指定安全性屬性，設定指定之索引鍵。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

設定金鑰的安全性屬性。 請參閱[RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity)如需詳細資訊。

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

呼叫此方法以設定登錄機碼的 multistring 的值。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串，包含要設定的值名稱的指標。 如果具有此名稱的值尚未存在，則方法會將它新增至機碼。

*pszValue*<br/>
使用指定的值名稱儲存的 multistring 資料指標。 Multistring 是以 null 結尾的字串，由兩個 null 字元結束的陣列。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)寫入登錄值。

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

呼叫此方法以設定登錄機碼的 QWORD 值。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串，包含要設定的值名稱的指標。 如果具有此名稱的值尚未存在，則方法會將它新增至機碼。

*qwValue*<br/>
QWORD 来儲存的資料與指定之值名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)寫入登錄值。

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

呼叫此方法以設定登錄機碼的字串值。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>參數

*pszValueName*<br/>
字串，包含要設定的值名稱的指標。 如果具有此名稱的值尚未存在，則方法會將它新增至機碼。

*pszValue*<br/>
要儲存指定的值名稱的字串資料的指標。

*dwType*<br/>
要寫入登錄的字串類型： REG_SZ （預設值） 或 REG_EXPAND_SZ (multistring)。

### <a name="return-value"></a>傳回值

如果方法成功，則傳回的值會是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤碼。H.

### <a name="remarks"></a>備註

這個方法會使用[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)寫入登錄值。

##  <a name="setvalue"></a>  CRegKey::SetValue

呼叫這個方法來將資料儲存在指定的值欄位[m_hKey](#m_hkey)。 舊版的這個方法不受支援，並會標示為 ATL_DEPRECATED。

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
字串，包含要設定的值名稱的指標。 如果尚未存在的索引鍵中具有此名稱的值，此方法會將其加入索引鍵。 如果*pszValueName*為 NULL 或空字串，""、 方法設定的型別和索引鍵資料的未具名或預設值。

*dwType*<br/>
指定表示所指向的資料類型的代碼*pValue*參數。

*pValue*<br/>
包含具有指定的值名稱儲存資料之緩衝區的指標。

*nBytes*<br/>
指定的大小，以位元組為單位所指向的資訊*pValue*參數。 如果資料類型為 REG_SZ，REG_EXPAND_SZ 或 REG_MULTI_SZ， *nBytes*必須包含結束的 null 字元的大小。

*hKeyParent*<br/>
開啟金鑰的控制代碼。

*lpszKeyName*<br/>
指定要建立或開啟金鑰的名稱。 此名稱必須是子機碼*hKeyParent*。

*lpszValue*<br/>
指定要儲存的資料。 這個參數必須為非 NULL。

*lpszValueName*<br/>
指定要設定的 [值] 欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。

*dwValue*<br/>
指定要儲存的資料。

*bMulti*<br/>
如果為 false，指出字串型別的 REG_SZ。 如果為 true，指出字串型別的 REG_MULTI_SZ multistring。

*nValueLen*<br/>
如果*bMulti*為 true， *nValueLen*長度*lpszValue*以字元為單位的字串。 如果*bMulti*為 false，-1 值表示此方法會自動計算長度。

### <a name="return-value"></a>傳回值

如果成功，則傳回 ERROR_SUCCESS;否則，傳回非零的錯誤碼 WINERROR 中定義。H.

### <a name="remarks"></a>備註

兩個原始版本`SetValue`會標示為 ATL_DEPRECATED 且無法再使用。 如果這些表單的使用，編譯器會發出警告。

第三個方法呼叫[RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa)。

## <a name="see-also"></a>另請參閱

[DCOM 範例](../../visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
