---
title: CRegKey 類別 |Microsoft 文件
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
ms.openlocfilehash: b6daec3347aecaed3ba0aba5dec106d049a6a701
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366636"
---
# <a name="cregkey-class"></a>CRegKey 類別
這個類別會提供方法來操作系統登錄中的項目。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
|[CRegKey::Attach](#attach)|呼叫此方法以附加至 HKEY`CRegKey`物件藉由設定[m_hKey](#m_hkey)成員控制代碼`hKey`。|  
|[CRegKey::Close](#close)|呼叫此方法以釋放[m_hKey](#m_hkey)成員處理，並將它設定為 NULL。|  
|[CRegKey::Create](#create)|呼叫這個方法來建立指定之索引鍵，如果它不存在的子機碼為`hKeyParent`。|  
|[CRegKey::DeleteSubKey](#deletesubkey)|呼叫這個方法來移除登錄中指定之索引鍵。|  
|[CRegKey::DeleteValue](#deletevalue)|呼叫這個方法來移除值欄位從[m_hKey](#m_hkey)。|  
|[CRegKey::Detach](#detach)|呼叫這個方法來卸離[m_hKey](#m_hkey)成員控制代碼與`CRegKey`物件，並設定`m_hKey`為 NULL。|  
|[CRegKey::EnumKey](#enumkey)|呼叫這個方法來列舉子機碼的開啟登錄機碼。|  
|[CRegKey::Flush](#flush)|呼叫這個方法在登錄中寫入的所有開啟的登錄機碼的屬性。|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|呼叫此方法以擷取保護開啟登錄機碼的安全性描述元的複本。|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|這個方法會通知呼叫端相關變更的屬性或開啟登錄機碼的內容。|  
|[CRegKey::Open](#open)|呼叫這個方法來開啟指定的索引鍵，然後設定[m_hKey](#m_hkey)這個機碼的控制代碼。|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|呼叫此方法以擷取指定的值名稱的二進位資料。|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|呼叫此方法以擷取指定的值名稱的 DWORD 資料。|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|呼叫此方法以擷取指定的值名稱的 GUID 資料。|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|呼叫此方法以擷取指定的值名稱的 multistring 資料。|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|呼叫此方法以擷取指定的值名稱的 QWORD 資料。|  
|[CRegKey::QueryStringValue](#querystringvalue)|呼叫此方法以擷取指定的值名稱的字串資料。|  
|[CRegKey::QueryValue](#queryvalue)|呼叫此方法以擷取指定的值欄位的資料[m_hKey](#m_hkey)。 不再支援舊版的這個方法，並會標示為**ATL_DEPRECATED**。|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|呼叫這個方法來移除登錄中指定之索引鍵和任何子機碼，明確地移除。|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|呼叫此方法以設定登錄機碼的二進位值。|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|呼叫此方法以設定登錄機碼 DWORD 值。|  
|[CRegKey::SetGUIDValue](#setguidvalue)|呼叫此方法以設定登錄機碼的 GUID 值。|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|呼叫此方法以設定登錄機碼的安全性。|  
|[CRegKey::SetKeyValue](#setkeyvalue)|呼叫此方法以將資料儲存在指定的值欄位的指定索引鍵。|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|呼叫此方法以設定登錄機碼的 multistring 值。|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|呼叫此方法以設定登錄機碼 QWORD 值。|  
|[CRegKey::SetStringValue](#setstringvalue)|呼叫此方法以設定登錄機碼的字串值。|  
|[CRegKey::SetValue](#setvalue)|呼叫此方法以將資料儲存在指定的值欄位[m_hKey](#m_hkey)。 不再支援舊版的這個方法，並會標示為**ATL_DEPRECATED**。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CRegKey::operator HKEY](#operator_hkey)|將轉換`CRegKey`HKEY 的物件。|  
|[CRegKey::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CRegKey::m_hKey](#m_hkey)|包含相關聯的登錄機碼的控制代碼`CRegKey`物件。|  
|[CRegKey::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件|  
  
## <a name="remarks"></a>備註  
 `CRegKey` 提供方法來建立和刪除索引鍵和系統登錄中的值。 登錄包含安裝特定一組系統元件，例如軟體版本號碼、 已安裝的硬體和 COM 物件的邏輯實體對應的定義。  
  
 `CRegKey` 指定的機器提供系統登錄的程式設計介面。 例如，若要開啟特定的登錄機碼，呼叫`CRegKey::Open`。 若要擷取或修改資料值，呼叫`CRegKey::QueryValue`或`CRegKey::SetValue`分別。 若要關閉的索引鍵，請呼叫`CRegKey::Close`。  
  
 當您關閉的索引鍵時，其登錄資料會寫入 （清除） 的硬碟。 此程序可能需要幾秒鐘的時間。 如果您的應用程式必須明確登錄資料寫入硬碟，您可以呼叫[RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32 函式。 不過， **RegFlushKey**使用多系統資源，並只在絕對必要時，應該呼叫。  
  
> [!IMPORTANT]
>  任何方法可讓呼叫端指定的登錄位置可能會讀取不受信任的資料。 方法可讓使用[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)應該納入考量，此函式不會明確地處理都是 NULL 終止的字串。 這兩種條件必須檢查呼叫程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="attach"></a>  CRegKey::Attach  
 呼叫此方法以附加至 HKEY`CRegKey`物件藉由設定[m_hKey](#m_hkey)成員控制代碼`hKey`。  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 登錄機碼的控制代碼。  
  
### <a name="remarks"></a>備註  
 **附加**會判斷提示，如果`m_hKey`為非 NULL。  
  
##  <a name="close"></a>  CRegKey::Close  
 呼叫此方法以釋放[m_hKey](#m_hkey)成員處理，並將它設定為 NULL。  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則會傳回錯誤值。  
  
##  <a name="create"></a>  CRegKey::Create  
 呼叫這個方法來建立指定之索引鍵，如果它不存在的子機碼為`hKeyParent`。  
  
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
 `hKeyParent`  
 開放式金鑰控制代碼。  
  
 `lpszKeyName`  
 指定用來建立或開啟金鑰的名稱。 此名稱必須是子機碼的`hKeyParent`。  
  
 `lpszClass`  
 指定要建立或開啟之索引鍵的類別。 預設值是 REG_NONE。  
  
 `dwOptions`  
 索引鍵的選項。 預設值是 REG_OPTION_NON_VOLATILE。 如需可能的值和描述的清單，請參閱[RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) Windows SDK 中。  
  
 `samDesired`  
 安全性的存取金鑰。 預設值是 KEY_READ &#124; KEY_WRITE。 如需可能的值和描述的清單，請參閱**RegCreateKeyEx**。  
  
 *lpSecAttr*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，表示金鑰的控制代碼是否可以由子處理序繼承。 根據預設，這個參數是 NULL （表示無法繼承控制代碼）。  
  
 *lpdwDisposition*  
 [out]如果不是 NULL，擷取 REG_CREATED_NEW_KEY （如果索引鍵不存在，而且所建立） 或 REG_OPENED_EXISTING_KEY （如果索引鍵存在，但已開啟）。  
  
### <a name="return-value"></a>傳回值  
 如果成功，會傳回 ERROR_SUCCESS 並開啟金鑰。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 **建立**設定[m_hKey](#m_hkey)此機碼的控制代碼的成員。  
  
##  <a name="cregkey"></a>  CRegKey::CRegKey  
 建構函式。  
  
```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 對 `CRegKey` 物件的參考。  
  
 `hKey`  
 登錄機碼控制代碼。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 建立新的 `CRegKey` 物件。 物件可以建立從現有`CRegKey`物件，或從登錄機碼的控制代碼。  
  
##  <a name="dtor"></a>  CRegKey:: ~ CRegKey  
 解構函式。  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式版本`m_hKey`。  
  
##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey  
 呼叫這個方法來移除登錄中指定之索引鍵。  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszSubKey`  
 指定要刪除之索引鍵的名稱。 此名稱必須是子機碼的[m_hKey](#m_hkey)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 `DeleteSubKey` 只能刪除沒有子機碼的索引鍵。 如果機碼具有子機碼，呼叫[RecurseDeleteKey](#recursedeletekey)改為。  
  
##  <a name="deletevalue"></a>  CRegKey::DeleteValue  
 呼叫這個方法來移除值欄位從[m_hKey](#m_hkey)。  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszValue`  
 指定要移除的值欄位。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
##  <a name="detach"></a>  CRegKey::Detach  
 呼叫這個方法來卸離[m_hKey](#m_hkey)成員控制代碼與`CRegKey`物件，並設定`m_hKey`為 NULL。  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 與相關聯的 HKEY`CRegKey`物件。  
  
##  <a name="enumkey"></a>  CRegKey::EnumKey  
 呼叫這個方法來列舉子機碼的開啟登錄機碼。  
  
```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 子機碼的索引。 這個參數應為零的第一次呼叫，然後遞增的後續呼叫  
  
 `pszName`  
 接收子機碼，包括結束的 null 字元的名稱之緩衝區的指標。 子機碼名稱會複製到緩衝區，而不是完整金鑰階層。  
  
 *pnNameLength*  
 變數，指定的大小，以 TCHARs，所指定的緩衝區指標`pszName`參數。 這個大小應該包含結束的 null 字元。 此方法傳回時，所指向的變數*pnNameLength*包含儲存在緩衝區中的字元數。 傳回的計數不包括結束的 null 字元。  
  
 *pftLastWriteTime*  
 接收時間變數指標列舉子機碼上次被寫入。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 若要列舉子機碼，呼叫`CRegKey::EnumKey`索引為零。 遞增的索引值，並重複，直到該方法會傳回 ERROR_NO_MORE_ITEMS 為止。 如需詳細資訊，請參閱[RegEnumKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724862) Windows SDK 中。  
  
##  <a name="flush"></a>  CRegKey::Flush  
 呼叫這個方法在登錄中寫入的所有開啟的登錄機碼的屬性。  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[RegEnumFlush](http://msdn.microsoft.com/library/windows/desktop/ms724867) Windows SDK 中。  
  
##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity  
 呼叫此方法以擷取保護開啟登錄機碼的安全性描述元的複本。  
  
```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `si`  
 [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)值，指出要求的安全性資訊。  
  
 `psd`  
 收到要求的安全性描述元的複本緩衝區的指標。  
  
 `pnBytes`  
 以位元組為單位所指向之緩衝區的大小， `psd`。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回的值會是 WINERROR 中定義為非零的錯誤碼。H.  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[RegGetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379313)。  
  
##  <a name="m_hkey"></a>  CRegKey::m_hKey  
 包含相關聯的登錄機碼的控制代碼`CRegKey`物件。  
  
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
 *bWatchSubtree*  
 指定的旗標，指出是否要在報告中指定之索引鍵和所有子機碼，或只在指定的索引鍵中的變更。 如果此參數為 TRUE，則該方法會回報機碼及其子機碼中的變更。 如果參數是 FALSE，則該方法會回報變更只存在於索引鍵。  
  
 *dwNotifyFilter*  
 指定應該報告一組旗標，以控制哪些變更。 這個參數可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|如果新增或刪除子機碼時，通知呼叫端。|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|告知呼叫端的變更金鑰，例如安全性描述元資訊的屬性。|  
|REG_NOTIFY_CHANGE_LAST_SET|告知呼叫端的變更金鑰的值。 這可以包括新增或刪除某個值，或變更現有的值。|  
|REG_NOTIFY_CHANGE_SECURITY|告知呼叫端的變更金鑰的安全性描述元。|  
  
 `hEvent`  
 事件的控制代碼。 如果*bAsync*參數為 TRUE 時，此方法會立即傳回且變更會報告此事件的信號方式。 如果`bAsync`為 FALSE，`hEvent`會被忽略。  
  
 `bAsync`  
 指定旗標，指出該方法會如何回報變更。 如果此參數為 TRUE，方法會立即傳回，而且報告信號指定的事件的變更。 當此參數為 FALSE 時，此方法前不會傳回已發生變更。 如果`hEvent`未指定有效的事件，`bAsync`參數不可為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法不會通知呼叫端，如果刪除指定的索引鍵。  
  
 如需詳細資訊和範例程式，請參閱[RegNotifyChangeKeyValue](http://msdn.microsoft.com/library/windows/desktop/ms724892)。  
  
##  <a name="open"></a>  CRegKey::Open  
 呼叫這個方法來開啟指定的索引鍵，然後設定[m_hKey](#m_hkey)這個機碼的控制代碼。  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>參數  
 `hKeyParent`  
 開放式金鑰控制代碼。  
  
 `lpszKeyName`  
 指定用來建立或開啟金鑰的名稱。 此名稱必須是子機碼的`hKeyParent`。  
  
 `samDesired`  
 安全性的存取金鑰。 預設值是 KEY_ALL_ACCESS。 如需可能的值和描述的清單，請參閱[RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，WINERROR 中定義的非零的錯誤值。H.  
  
### <a name="remarks"></a>備註  
 如果`lpszKeyName`參數為 NULL 或點設為空字串，**開啟**會開啟新的控制代碼所識別的索引鍵的`hKeyParent`，但不會關閉任何先前開啟的控制代碼。  
  
 不同於[CRegKey::Create](#create)，**開啟**如果不存在，則不會建立指定之索引鍵。  
  
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
 `key`  
 要複製的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回新的索引鍵的參考。  
  
### <a name="remarks"></a>備註  
 這個運算子會卸離`key`從其目前的物件並將其指派給`CRegKey`改為物件。  
  
##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue  
 呼叫此方法以擷取指定的值名稱的二進位資料。  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。  
  
 `pValue`  
 接收值的資料緩衝區的指標。  
  
 `pnBytes`  
 所指向的變數，指定的大小，以位元組為單位的緩衝區指標`pValue`參數。 方法傳回時，此變數包含資料複製到緩衝區的大小。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是 REG_BINARY 類型，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會使用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)這個方法所使用的函式不會明確地處理都是 NULL 終止的字串。 這兩種條件必須檢查呼叫程式碼。  
  
##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue  
 呼叫此方法以擷取指定的值名稱的 DWORD 資料。  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。  
  
 `dwValue`  
 DWORD 的接收緩衝區的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是類型 REG_DWORD，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會使用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)這個方法所使用的函式不會明確地處理都是 NULL 終止的字串。 這兩種條件必須檢查呼叫程式碼。  
  
##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue  
 呼叫此方法以擷取指定的值名稱的 GUID 資料。  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。  
  
 `guidValue`  
 此變數會接收 GUID 的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是有效的 GUID，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會使用`CRegKey::QueryStringValue`將字串轉換成 GUID 使用[CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589)。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。  
  
##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue  
 呼叫此方法以擷取指定的值名稱的 multistring 資料。  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。  
  
 `pszValue`  
 接收 multistring 資料緩衝區的指標。 在 multistring 是陣列的以 null 結束的字串，以兩個 null 字元結束。  
  
 `pnChars`  
 TCHARs，所指向之緩衝區的大小， `pszValue`。 方法傳回時，`pnChars`包含以 TCHARs，multistring 擷取，包括結束的 null 字元的大小。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是類型 REG_MULTI_SZ，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會使用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)這個方法所使用的函式不會明確地處理都是 NULL 終止的字串。 這兩種條件必須檢查呼叫程式碼。  
  
##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue  
 呼叫此方法以擷取指定的值名稱的 QWORD 資料。  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。  
  
 `qwValue`  
 接收 QWORD 緩衝區的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是類型 REG_QWORD，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會使用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)這個方法所使用的函式不會明確地處理都是 NULL 終止的字串。 這兩種條件必須檢查呼叫程式碼。  
  
##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue  
 呼叫此方法以擷取指定的值名稱的字串資料。  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。  
  
 `pszValue`  
 收到的字串資料的緩衝區指標。  
  
 `pnChars`  
 TCHARs，所指向之緩衝區的大小， `pszValue`。 方法傳回時，`pnChars`包含的大小，以 TCHARs，擷取，包括結束的 null 字元的字串。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是類型為 REG_SZ，則會傳回 ERROR_INVALID_DATA。 如果此方法會傳回 ERROR_MORE_DATA，`pnChars`等於零，不必要的緩衝區大小 （位元組）。  
  
### <a name="remarks"></a>備註  
 這個方法會使用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)這個方法所使用的函式不會明確地處理都是 NULL 終止的字串。 這兩種條件必須檢查呼叫程式碼。  
  
##  <a name="queryvalue"></a>  CRegKey::QueryValue  
 呼叫此方法以擷取指定的值欄位的資料[m_hKey](#m_hkey)。 不再支援舊版的這個方法，並會標示為**ATL_DEPRECATED**。  
  
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
 `pszValueName`  
 指向以 null 結束的字串，包含要查詢之值的名稱。 如果`pszValueName`是 NULL 或空字串，""、 方法擷取的型別和索引鍵資料的未命名或預設值，如果有的話。  
  
 `pdwType`  
 此變數會接收代碼，表示儲存在指定的值中的資料類型的指標。 `pdwType`參數可以是 NULL，如果不需要的類型程式碼。  
  
 `pData`  
 接收值的資料緩衝區的指標。 如果資料不需要這個參數可以是 NULL。  
  
 `pnBytes`  
 所指向的變數，指定的大小，以位元組為單位的緩衝區指標`pData`參數。 方法傳回時，此變數包含要複製的資料大小*pData。*  
  
 `dwValue`  
 值欄位的數值資料。  
  
 `lpszValueName`  
 指定要查詢的 [值] 欄位。  
  
 `szValue`  
 值欄位的字串資料。  
  
 `pdwCount`  
 字串資料的大小。 其值的大小最初設定`szValue`緩衝區。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，則為非零的錯誤碼 WINERROR 中定義。H.  
  
### <a name="remarks"></a>備註  
 原始的兩個版本`QueryValue`不再支援，並會標示為**ATL_DEPRECATED**。 如果這些表單的使用，則編譯器會發出警告。  
  
 其餘的方法會呼叫 RegQueryValueEx。  
  
> [!IMPORTANT]
>  這個方法可讓呼叫端指定任何登錄位置中，可能讀取且不可以是受信任的資料。 此外，這個方法所使用的 RegQueryValueEx 函式不會明確地處理字串，其為`NULL`終止。 這兩種條件必須檢查呼叫程式碼。  
  
##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey  
 呼叫這個方法來移除登錄中指定之索引鍵和任何子機碼，明確地移除。  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszKey*  
 指定要刪除之索引鍵的名稱。 此名稱必須是子機碼的[m_hKey](#m_hkey)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，WINERROR 中定義的非零的錯誤值。H.  
  
### <a name="remarks"></a>備註  
 如果機碼具有子機碼，您必須呼叫這個方法，以刪除機碼。  
  
##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue  
 呼叫此方法以設定登錄機碼的二進位值。  
  
```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值還不存在，此方法會將其加入索引鍵。  
  
 `pValue`  
 包含要與指定的值名稱儲存在一起的資料緩衝區的指標。  
  
 `nBytes`  
 指定的大小，以位元組為單位的資訊指向`pValue`參數。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)寫入登錄值。  
  
##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue  
 呼叫此方法以設定登錄機碼 DWORD 值。  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值還不存在，此方法會將其加入索引鍵。  
  
 `dwValue`  
 要與指定的值名稱儲存在一起的 DWORD 資料。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)寫入登錄值。  
  
##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue  
 呼叫此方法以設定登錄機碼的 GUID 值。  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值還不存在，此方法會將其加入索引鍵。  
  
 `guidValue`  
 參考要與指定的值名稱儲存在一起的 GUID。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用`CRegKey::SetStringValue`，將 GUID 轉換成字串，使用[StringFromGUID2](http://msdn.microsoft.com/library/windows/desktop/ms683893)。  
  
##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue  
 呼叫此方法以將資料儲存在指定的值欄位的指定索引鍵。  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszKeyName`  
 指定要建立或開啟之索引鍵的名稱。 此名稱必須是子機碼的[m_hKey](#m_hkey)。  
  
 `lpszValue`  
 指定要儲存的資料。 這個參數必須為非 NULL。  
  
 `lpszValueName`  
 指定要設定的值欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，則為非零的錯誤碼 WINERROR 中定義。H.  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來建立或開啟`lpszKeyName`金鑰及儲存`lpszValue`中的資料`lpszValueName`值欄位。  
  
##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity  
 呼叫此方法以設定登錄機碼的安全性。  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>參數  
 `si`  
 指定要設定安全性描述元的元件。 值可以是下列值的組合：  
  
|值|意義|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|設定索引鍵的判別存取控制清單 (DACL)。 機碼必須具有 WRITE_DAC 存取，或呼叫程序必須是物件的擁有者。|  
|GROUP_SECURITY_INFORMATION|設定索引鍵的主要群組安全性識別碼 (SID)。 機碼必須具有 WRITE_OWNER 存取，或呼叫程序必須是物件的擁有者。|  
|OWNER_SECURITY_INFORMATION|設定金鑰的擁有者 SID。 機碼必須具有 WRITE_OWNER 存取，或呼叫程序必須是物件的擁有者或擁有已啟用 SE_TAKE_OWNERSHIP_NAME 權限。|  
|SACL_SECURITY_INFORMATION|設定索引鍵的系統存取控制清單 (SACL)。 索引鍵必須 ACCESS_SYSTEM_SECURITY 存取。 若要取得此存取權的正確方式是啟用 SE_SECURITY_NAME[權限](http://msdn.microsoft.com/library/windows/desktop/aa379306)在呼叫端的目前存取權杖中，開啟 ACCESS_SYSTEM_SECURITY 存取的控制代碼，然後再停用權限。|  
  
 `psd`  
 指標[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)結構，指定安全性屬性，設定指定之索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 設定機碼的安全性屬性。 請參閱[RegSetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379314)如需詳細資訊。  
  
##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue  
 呼叫此方法以設定登錄機碼的 multistring 值。  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值還不存在，此方法會將其加入索引鍵。  
  
 `pszValue`  
 要與指定的值名稱儲存在一起的 multistring 資料指標。 在 multistring 是陣列的以 null 結束的字串，以兩個 null 字元結束。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)寫入登錄值。  
  
##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue  
 呼叫此方法以設定登錄機碼 QWORD 值。  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值還不存在，此方法會將其加入索引鍵。  
  
 `qwValue`  
 要與指定的值名稱儲存在一起的 QWORD 資料。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)寫入登錄值。  
  
##  <a name="setstringvalue"></a>  CRegKey::SetStringValue  
 呼叫此方法以設定登錄機碼的字串值。  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值還不存在，此方法會將其加入索引鍵。  
  
 `pszValue`  
 要儲存指定的值名稱的字串資料的指標。  
  
 `dwType`  
 要寫入登錄的字串類型: （預設值） REG_SZ 或 REG_EXPAND_SZ （適用於 multistring)。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值會是 ERROR_SUCCESS。 如果方法失敗，傳回值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923\(v=vs.85\).aspx)寫入登錄值。  
  
##  <a name="setvalue"></a>  CRegKey::SetValue  
 呼叫此方法以將資料儲存在指定的值欄位[m_hKey](#m_hkey)。 不再支援舊版的這個方法，並會標示為**ATL_DEPRECATED**。  
  
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
 `pszValueName`  
 包含要設定之值的名稱的字串指標。 如果具有此名稱的值尚未存在機碼中，此方法會將其加入索引鍵。 如果`pszValueName`是 NULL 或空字串，""、 方法設定的類型和資料索引鍵的未命名或預設值。  
  
 `dwType`  
 指定表示所指向的資料類型的代碼`pValue`參數。  
  
 `pValue`  
 包含要與指定的值名稱儲存在一起的資料緩衝區的指標。  
  
 `nBytes`  
 指定的大小，以位元組為單位的資訊指向`pValue`參數。 如果資料類型為 REG_SZ、 REG_EXPAND_SZ 或 REG_MULTI_SZ，`nBytes`必須包含結束的 null 字元的大小。  
  
 `hKeyParent`  
 開放式金鑰控制代碼。  
  
 `lpszKeyName`  
 指定用來建立或開啟金鑰的名稱。 此名稱必須是子機碼的`hKeyParent`。  
  
 `lpszValue`  
 指定要儲存的資料。 這個參數必須為非 NULL。  
  
 `lpszValueName`  
 指定要設定的值欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。  
  
 `dwValue`  
 指定要儲存的資料。  
  
 `bMulti`  
 如果為 false，指出字串的類型為 REG_SZ。 如果為 true，指出字串型別 REG_MULTI_SZ multistring。  
  
 `nValueLen`  
 如果`bMulti`為 true，`nValueLen`段*lpszValue*以字元為單位的字串。 如果`bMulti`為 false，值為-1 表示方法將會自動計算長度。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，則為非零的錯誤碼 WINERROR 中定義。H.  
  
### <a name="remarks"></a>備註  
 原始的兩個版本`SetValue`標示為**ATL_DEPRECATED** ，應該不會再使用。 如果這些表單的使用，則編譯器會發出警告。  
  
 第三個方法呼叫[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)。  
  
## <a name="see-also"></a>另請參閱  
 [DCOM 範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)
