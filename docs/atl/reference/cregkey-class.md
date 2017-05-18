---
title: "CRegKey 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 25
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d0ab2a2a0c74ed3d6b48297cc052ebbf09bd3291
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cregkey-class"></a>CRegKey 類別
這個類別提供方法來操作系統登錄中的項目。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CRegKey
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CRegKey::CRegKey](#cregkey)|建構函式。|  
|[CRegKey:: ~ CRegKey](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRegKey::Attach](#attach)|呼叫這個方法來附加至 HKEY`CRegKey`藉由設定物件[m_hKey](#m_hkey)成員控制代碼`hKey`。|  
|[CRegKey::Close](#close)|呼叫此方法以釋放[m_hKey](#m_hkey)成員處理，並將它設定為 NULL。|  
|[CRegKey::Create](#create)|呼叫這個方法來建立指定的索引鍵，如果不存在的子機碼為`hKeyParent`。|  
|[CRegKey::DeleteSubKey](#deletesubkey)|呼叫此方法以從登錄中移除指定的索引鍵。|  
|[CRegKey::DeleteValue](#deletevalue)|呼叫這個方法來移除值欄位從[m_hKey](#m_hkey)。|  
|[CRegKey::Detach](#detach)|呼叫這個方法來卸離[m_hKey](#m_hkey)中的成員代碼`CRegKey`物件，並設定`m_hKey`為 NULL。|  
|[CRegKey::EnumKey](#enumkey)|呼叫這個方法來列舉開啟登錄機碼的子機碼。|  
|[CRegKey::Flush](#flush)|呼叫這個方法將所有開啟的登錄機碼的屬性寫入登錄。|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|呼叫此方法以擷取一份保護開啟登錄機碼的安全性描述元。|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|這個方法會通知呼叫端相關變更的屬性或開啟登錄機碼的內容。|  
|[CRegKey::Open](#open)|呼叫這個方法來開啟指定的索引鍵，然後設定[m_hKey](#m_hkey)這個機碼的控制代碼。|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|呼叫這個方法來擷取指定的值名稱的二進位資料。|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|呼叫這個方法來擷取指定的值名稱的 DWORD 資料。|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|呼叫這個方法來擷取指定的值名稱的 GUID 資料。|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|呼叫這個方法來擷取指定的值名稱的 multistring 資料。|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|呼叫這個方法來擷取指定的值名稱的 QWORD 資料。|  
|[CRegKey::QueryStringValue](#querystringvalue)|呼叫這個方法來擷取指定的值名稱的字串資料。|  
|[CRegKey::QueryValue](#queryvalue)|呼叫這個方法來擷取指定的值欄位的資料[m_hKey](#m_hkey)。 這個方法的先前版本已不再受到支援，並會標示為**ATL_DEPRECATED**。|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|呼叫此方法來從登錄中移除指定的索引鍵，並明確地移除任何子機碼。|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|呼叫這個方法來設定登錄機碼的二進位值。|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|呼叫這個方法來設定登錄機碼的 DWORD 值。|  
|[CRegKey::SetGUIDValue](#setguidvalue)|呼叫這個方法來設定登錄機碼的 GUID 值。|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|呼叫這個方法來設定登錄機碼的安全性。|  
|[CRegKey::SetKeyValue](#setkeyvalue)|呼叫這個方法將資料儲存在指定的值欄位的指定索引鍵。|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|呼叫這個方法來設定 multistring 的登錄機碼值。|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|呼叫這個方法來設定登錄機碼的 QWORD 值。|  
|[CRegKey::SetStringValue](#setstringvalue)|呼叫這個方法來設定登錄機碼的字串值。|  
|[CRegKey::SetValue](#setvalue)|呼叫此方法以將資料儲存在指定的值欄位的[m_hKey](#m_hkey)。 這個方法的先前版本已不再受到支援，並會標示為**ATL_DEPRECATED**。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CRegKey::operator HKEY](#operator_hkey)|將轉換`CRegKey`HKEY 的物件。|  
|[CRegKey::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CRegKey::m_hKey](#m_hkey)|包含與相關聯的登錄機碼的控制代碼`CRegKey`物件。|  
|[CRegKey::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件|  
  
## <a name="remarks"></a>備註  
 `CRegKey`提供方法來建立和刪除機碼和系統登錄中的值。 登錄包含特定安裝的一組定義的系統元件，例如軟體版本號碼、 安裝的硬體和 COM 物件的邏輯實體對應。  
  
 `CRegKey`提供指定的電腦系統登錄的程式設計介面。 例如，若要開啟特定的登錄機碼，呼叫`CRegKey::Open`。 若要擷取或修改資料值，呼叫`CRegKey::QueryValue`或`CRegKey::SetValue`分別。 若要關閉金鑰，呼叫`CRegKey::Close`。  
  
 當您關閉索引鍵時，其登錄資料會寫入 （排清） 到硬碟。 此程序可能需要幾秒鐘的時間。 如果您的應用程式必須明確地登錄資料寫入硬碟，您可以呼叫[RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32 函式。 不過， **RegFlushKey**使用多系統資源，應該只在絕對必要時呼叫。  
  
> [!IMPORTANT]
>  任何方法可讓呼叫端指定的登錄位置可能會讀取不受信任的資料。 使用方法讓[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)應該納入考量，此函式不會明確地處理 NULL 結尾字串。 兩個條件必須檢查呼叫程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="attach"></a>CRegKey::Attach  
 呼叫這個方法來附加至 HKEY`CRegKey`藉由設定物件[m_hKey](#m_hkey)成員控制代碼`hKey`。  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 登錄機碼的控制代碼。  
  
### <a name="remarks"></a>備註  
 **附加**會判斷提示，如果`m_hKey`不是 null。  
  
##  <a name="close"></a>CRegKey::Close  
 呼叫此方法以釋放[m_hKey](#m_hkey)成員處理，並將它設定為 NULL。  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則會傳回錯誤值。  
  
##  <a name="create"></a>CRegKey::Create  
 呼叫這個方法來建立指定的索引鍵，如果不存在的子機碼為`hKeyParent`。  
  
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
 開啟機碼的控制代碼。  
  
 `lpszKeyName`  
 指定用來建立或開啟金鑰的名稱。 此名稱必須是子機碼的`hKeyParent`。  
  
 `lpszClass`  
 指定要建立或開啟之索引鍵的類別。 預設值是 REG_NONE。  
  
 `dwOptions`  
 索引鍵的選項。 預設值是 REG_OPTION_NON_VOLATILE。 如需可能的值和描述的清單，請參閱[RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `samDesired`  
 金鑰的安全性存取權。 預設值是 KEY_READ |KEY_WRITE。 如需可能的值和描述的清單，請參閱**RegCreateKeyEx**。  
  
 *lpSecAttr*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，表示金鑰的控制代碼是否可以由子處理序繼承。 根據預設，這個參數是 NULL （亦即無法繼承控制代碼）。  
  
 *lpdwDisposition*  
 [out]如果不是 NULL，擷取 REG_CREATED_NEW_KEY （如果索引鍵不存在，而且已建立） 或 REG_OPENED_EXISTING_KEY （如果索引鍵存在，而且已開啟）。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS，並開啟金鑰。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 **建立**設定[m_hKey](#m_hkey)這個機碼的控制代碼的成員。  
  
##  <a name="cregkey"></a>CRegKey::CRegKey  
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
 登錄機碼的控制代碼。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 建立新的 `CRegKey` 物件。 可以建立從現有的物件`CRegKey`物件，或從登錄機碼的控制代碼。  
  
##  <a name="dtor"></a>CRegKey:: ~ CRegKey  
 解構函式。  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式版本`m_hKey`。  
  
##  <a name="deletesubkey"></a>CRegKey::DeleteSubKey  
 呼叫此方法以從登錄中移除指定的索引鍵。  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszSubKey`  
 指定要刪除的索引鍵名稱。 此名稱必須是子機碼的[m_hKey](#m_hkey)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 `DeleteSubKey`只能刪除有任何子機碼的索引鍵。 如果機碼具有子機碼，呼叫[RecurseDeleteKey](#recursedeletekey)改。  
  
##  <a name="deletevalue"></a>CRegKey::DeleteValue  
 呼叫這個方法來移除值欄位從[m_hKey](#m_hkey)。  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszValue`  
 指定要移除的值欄位。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
##  <a name="detach"></a>CRegKey::Detach  
 呼叫這個方法來卸離[m_hKey](#m_hkey)中的成員代碼`CRegKey`物件，並設定`m_hKey`為 NULL。  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 與相關聯的 HKEY`CRegKey`物件。  
  
##  <a name="enumkey"></a>CRegKey::EnumKey  
 呼叫這個方法來列舉開啟登錄機碼的子機碼。  
  
```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 子機碼的索引。 這個參數應該是第一次呼叫的零，則遞增的後續呼叫  
  
 `pszName`  
 接收包括結束的 null 字元的子機碼名稱的緩衝區指標。 子機碼名稱會複製到緩衝區，而不是完整金鑰的階層。  
  
 *pnNameLength*  
 指標，此變數會指定 TCHARs，所指定的緩衝區的大小，`pszName`參數。 此大小應該包含結束的 null 字元。 此方法傳回時，所指向之變數*pnNameLength*包含儲存在緩衝區的字元數。 傳回的計數不包含結束的 null 字元。  
  
 *pftLastWriteTime*  
 此變數會接收時間指標列舉子機碼上次被寫入。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 若要列舉子機碼，呼叫`CRegKey::EnumKey`以索引為零。 遞增的索引值，並重複，直到此方法會傳回 ERROR_NO_MORE_ITEMS。 如需詳細資訊，請參閱[RegEnumKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724862)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="flush"></a>CRegKey::Flush  
 呼叫這個方法將所有開啟的登錄機碼的屬性寫入登錄。  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[RegEnumFlush](http://msdn.microsoft.com/library/windows/desktop/ms724867)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getkeysecurity"></a>CRegKey::GetKeySecurity  
 呼叫此方法以擷取一份保護開啟登錄機碼的安全性描述元。  
  
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
 接收要求的安全性描述元複製緩衝區的指標。  
  
 `pnBytes`  
 大小，以位元組為單位的緩衝區所指`psd`。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，傳回的值會是 WINERROR 中定義為非零的錯誤碼。H.  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[RegGetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379313)。  
  
##  <a name="m_hkey"></a>CRegKey::m_hKey  
 包含與相關聯的登錄機碼的控制代碼`CRegKey`物件。  
  
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
 指定的旗標，指出是否要報告在指定的機碼及其所有子機碼或只在指定索引鍵中的變更。 如果此參數為 TRUE，則該方法會回報機碼及其子機碼中的變更。 如果參數為 FALSE，該方法會回報變更只存在於索引鍵。  
  
 *dwNotifyFilter*  
 指定應該報告一組旗標，以控制哪些變更。 這個參數可以是下列值的組合︰  
  
|值|意義|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|如果新增或刪除子機碼時，通知呼叫端。|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知呼叫端的金鑰，例如安全性描述元資訊屬性的變更。|  
|REG_NOTIFY_CHANGE_LAST_SET|通知呼叫端的索引鍵的值變更。 這可以包括新增或刪除某個值，或變更現有的值。|  
|REG_NOTIFY_CHANGE_SECURITY|通知呼叫端的索引鍵的安全性描述元變更。|  
  
 `hEvent`  
 事件的控制代碼。 如果*bAsync*參數為 TRUE 時，此方法會立即傳回而變更會發出此事件報告。 如果`bAsync`為 FALSE，`hEvent`會被忽略。  
  
 `bAsync`  
 指定旗標，指出方法報告變更的方式。 如果此參數為 TRUE，則方法會立即傳回，而發出指定的事件報告變更。 當此參數為 FALSE 時，此方法不會傳回之前已經發生變更。 如果`hEvent`未指定有效的事件，`bAsync`參數不可以是 TRUE。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法不會通知呼叫端，如果刪除指定的索引鍵。  
  
 如需詳細資訊和範例程式，請參閱[RegNotifyChangeKeyValue](http://msdn.microsoft.com/library/windows/desktop/ms724892)。  
  
##  <a name="open"></a>CRegKey::Open  
 呼叫這個方法來開啟指定的索引鍵，然後設定[m_hKey](#m_hkey)這個機碼的控制代碼。  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>參數  
 `hKeyParent`  
 開啟機碼的控制代碼。  
  
 `lpszKeyName`  
 指定用來建立或開啟金鑰的名稱。 此名稱必須是子機碼的`hKeyParent`。  
  
 `samDesired`  
 金鑰的安全性存取權。 預設值是 KEY_ALL_ACCESS。 如需可能的值和描述的清單，請參閱[RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，WINERROR 中定義的非零的錯誤值。H.  
  
### <a name="remarks"></a>備註  
 如果`lpszKeyName`參數為 NULL 或點設為空字串，**開啟**會開啟新的控制代碼所識別的索引鍵的`hKeyParent`，但不會關閉任何先前所開啟的控制代碼。  
  
 不同於[CRegKey::Create](#create)，**開啟**如果不存在，則不會建立指定之索引鍵。  
  
##  <a name="operator_hkey"></a>CRegKey::operator HKEY  
 將轉換`CRegKey`HKEY 的物件。  
  
```  
operator HKEY() const throw();
```  
  
##  <a name="operator_eq"></a>CRegKey::operator =  
 指派運算子。  
  
```
CRegKey& operator= (CRegKey& key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要複製的金鑰。  
  
### <a name="return-value"></a>傳回值  
 傳回新的索引鍵的參考。  
  
### <a name="remarks"></a>備註  
 這個運算子會卸離`key`從其目前的物件並將其指派給`CRegKey`物件。  
  
##  <a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue  
 呼叫這個方法來擷取指定的值名稱的二進位資料。  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 以 null 終止的字串，包含要查詢之值的名稱的指標。  
  
 `pValue`  
 接收到的值的資料緩衝區的指標。  
  
 `pnBytes`  
 變數所指定的大小，以位元組為單位的緩衝區指標所指`pValue`參數。 方法傳回時，此變數包含資料複製到緩衝區的大小。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是 REG_BINARY 類型，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會利用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函式，用這個方法不會明確地處理 NULL 結尾字串。 兩個條件必須檢查呼叫程式碼。  
  
##  <a name="querydwordvalue"></a>CRegKey::QueryDWORDValue  
 呼叫這個方法來擷取指定的值名稱的 DWORD 資料。  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 以 null 終止的字串，包含要查詢之值的名稱的指標。  
  
 `dwValue`  
 DWORD 的接收緩衝區的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是型別呼叫完成，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會利用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函式，用這個方法不會明確地處理 NULL 結尾字串。 兩個條件必須檢查呼叫程式碼。  
  
##  <a name="queryguidvalue"></a>CRegKey::QueryGUIDValue  
 呼叫這個方法來擷取指定的值名稱的 GUID 資料。  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 以 null 終止的字串，包含要查詢之值的名稱的指標。  
  
 `guidValue`  
 此變數會接收 GUID 的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是有效的 GUID，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會利用`CRegKey::QueryStringValue`將字串轉換成 GUID 使用[CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589)。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。  
  
##  <a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue  
 呼叫這個方法來擷取指定的值名稱的 multistring 資料。  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 以 null 終止的字串，包含要查詢之值的名稱的指標。  
  
 `pszValue`  
 接收到的 multistring 資料緩衝區的指標。 Multistring 是以 null 結束的字串，以兩個 null 字元結束的陣列。  
  
 `pnChars`  
 TCHARs，所指向的緩衝區的大小， `pszValue`。 方法傳回時，`pnChars`包含以 TCHARs，multistring 擷取，包括結束的 null 字元的大小。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是類型為 REG_MULTI_SZ，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會利用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函式，用這個方法不會明確地處理 NULL 結尾字串。 兩個條件必須檢查呼叫程式碼。  
  
##  <a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue  
 呼叫這個方法來擷取指定的值名稱的 QWORD 資料。  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 以 null 終止的字串，包含要查詢之值的名稱的指標。  
  
 `qwValue`  
 接收 QWORD 緩衝區的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是型別 REG_QWORD，則會傳回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>備註  
 這個方法會利用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函式，用這個方法不會明確地處理 NULL 結尾字串。 兩個條件必須檢查呼叫程式碼。  
  
##  <a name="querystringvalue"></a>CRegKey::QueryStringValue  
 呼叫這個方法來擷取指定的值名稱的字串資料。  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 以 null 終止的字串，包含要查詢之值的名稱的指標。  
  
 `pszValue`  
 接收到的字串資料緩衝區的指標。  
  
 `pnChars`  
 TCHARs，所指向的緩衝區的大小， `pszValue`。 方法傳回時，`pnChars`包含大小，以 TCHARs，擷取，包括結束的 null 字元的字串。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，則會傳回 ERROR_SUCCESS。 如果方法無法讀取的值，它會傳回 WINERROR 中定義的非零的錯誤代碼。H. 如果參考的資料不是類型為 REG_SZ，則會傳回 ERROR_INVALID_DATA。 如果此方法會傳回 ERROR_MORE_DATA，`pnChars`等於零，不必要的緩衝區大小 （位元組）。  
  
### <a name="remarks"></a>備註  
 這個方法會利用**RegQueryValueEx** ，並確認會傳回正確的資料類型。 請參閱[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)如需詳細資訊。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函式，用這個方法不會明確地處理 NULL 結尾字串。 兩個條件必須檢查呼叫程式碼。  
  
##  <a name="queryvalue"></a>CRegKey::QueryValue  
 呼叫這個方法來擷取指定的值欄位的資料[m_hKey](#m_hkey)。 這個方法的先前版本已不再受到支援，並會標示為**ATL_DEPRECATED**。  
  
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
 以 null 終止的字串，包含要查詢之值的名稱的指標。 如果`pszValueName`是 NULL 或空字串，"」，方法會擷取型別和索引鍵資料的未命名或預設值，如果有的話。  
  
 `pdwType`  
 此變數會接收代碼，表示指定的值中儲存的資料類型的指標。 `pdwType`參數可以是 NULL，如果不需要的類型程式碼。  
  
 `pData`  
 接收到的值的資料緩衝區的指標。 如果資料不需要這個參數可以是 NULL。  
  
 `pnBytes`  
 變數所指定的大小，以位元組為單位的緩衝區指標所指`pData`參數。 方法傳回時，此變數包含要複製的資料大小*pData。*  
  
 `dwValue`  
 [值] 欄位的數值資料。  
  
 `lpszValueName`  
 指定要查詢的 [值] 欄位。  
  
 `szValue`  
 [值] 欄位的字串資料。  
  
 `pdwCount`  
 字串資料的大小。 其值一開始會設大小`szValue`緩衝區。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，為非零的錯誤碼 WINERROR 中定義。H.  
  
### <a name="remarks"></a>備註  
 兩個原始版本`QueryValue`已不再受到支援，並會標示為**ATL_DEPRECATED**。 如果使用這些表單，則編譯器會發出警告。  
  
 其餘的方法會呼叫 RegQueryValueEx。  
  
> [!IMPORTANT]
>  此方法可讓呼叫端指定任何登錄位置，可能會讀取不能是受信任的資料。 此外，這個方法所用的 RegQueryValueEx 函式不會明確地處理字串，其為`NULL`終止。 兩個條件必須檢查呼叫程式碼。  
  
##  <a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey  
 呼叫此方法來從登錄中移除指定的索引鍵，並明確地移除任何子機碼。  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszKey*  
 指定要刪除的索引鍵名稱。 此名稱必須是子機碼的[m_hKey](#m_hkey)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，WINERROR 中定義的非零的錯誤值。H.  
  
### <a name="remarks"></a>備註  
 如果機碼具有子機碼，您必須呼叫這個方法，以刪除機碼。  
  
##  <a name="setbinaryvalue"></a>CRegKey::SetBinaryValue  
 呼叫這個方法來設定登錄機碼的二進位值。  
  
```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於，此方法會將它加入索引鍵。  
  
 `pValue`  
 包含要與指定的值名稱一起儲存的資料緩衝區的指標。  
  
 `nBytes`  
 指定的大小，以位元組為單位的資訊指向`pValue`參數。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)來將值寫入至登錄。  
  
##  <a name="setdwordvalue"></a>CRegKey::SetDWORDValue  
 呼叫這個方法來設定登錄機碼的 DWORD 值。  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於，此方法會將它加入索引鍵。  
  
 `dwValue`  
 要與指定的值名稱一起儲存的 DWORD 資料。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)來將值寫入至登錄。  
  
##  <a name="setguidvalue"></a>CRegKey::SetGUIDValue  
 呼叫這個方法來設定登錄機碼的 GUID 值。  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於，此方法會將它加入索引鍵。  
  
 `guidValue`  
 參考要與指定的值名稱一起儲存的 GUID。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會利用`CRegKey::SetStringValue`，並將 GUID 轉換成字串，使用[StringFromGUID2](http://msdn.microsoft.com/library/windows/desktop/ms683893)。  
  
##  <a name="setkeyvalue"></a>CRegKey::SetKeyValue  
 呼叫這個方法將資料儲存在指定的值欄位的指定索引鍵。  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszKeyName`  
 指定要建立或開啟的索引鍵名稱。 此名稱必須是子機碼的[m_hKey](#m_hkey)。  
  
 `lpszValue`  
 指定要儲存的資料。 這個參數必須為非 NULL。  
  
 `lpszValueName`  
 指定要設定的值欄位。 如果機碼中已存在具有此名稱的值欄位，會將它加入。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，為非零的錯誤碼 WINERROR 中定義。H.  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來建立或開啟`lpszKeyName`鍵，然後儲存`lpszValue`中的資料`lpszValueName`值欄位。  
  
##  <a name="setkeysecurity"></a>CRegKey::SetKeySecurity  
 呼叫這個方法來設定登錄機碼的安全性。  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>參數  
 `si`  
 指定的元件設定的安全性描述元。 值可以是下列值的組合︰  
  
|值|意義|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|設定索引鍵的判別存取控制清單 (DACL)。 索引鍵必須具有 WRITE_DAC 存取，或呼叫程序必須是物件的擁有者。|  
|GROUP_SECURITY_INFORMATION|設定機碼的主要群組安全性識別碼 (SID)。 索引鍵必須具有 WRITE_OWNER 存取，或呼叫程序必須是物件的擁有者。|  
|OWNER_SECURITY_INFORMATION|設定金鑰的擁有者 SID。 索引鍵必須具有 WRITE_OWNER 存取，或呼叫程序必須是物件的擁有者或具有已啟用 SE_TAKE_OWNERSHIP_NAME 權限。|  
|SACL_SECURITY_INFORMATION|設定機碼的系統存取控制清單 (SACL)。 索引鍵必須 ACCESS_SYSTEM_SECURITY 存取。 若要取得此存取權的正確方式是啟用 SE_SECURITY_NAME[權限](http://msdn.microsoft.com/library/windows/desktop/aa379306)在呼叫端的目前存取權杖中，開啟 ACCESS_SYSTEM_SECURITY 存取的控制代碼，然後停用權限。|  
  
 `psd`  
 指標[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)結構，指定安全性屬性來設定指定的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 設定金鑰的安全性屬性。 請參閱[RegSetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379314)如需詳細資訊。  
  
##  <a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue  
 呼叫這個方法來設定 multistring 的登錄機碼值。  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於，此方法會將它加入索引鍵。  
  
 `pszValue`  
 要儲存在指定的值名稱一起 multistring 的資料指標。 Multistring 是以 null 結束的字串，以兩個 null 字元結束的陣列。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)來將值寫入至登錄。  
  
##  <a name="setqwordvalue"></a>CRegKey::SetQWORDValue  
 呼叫這個方法來設定登錄機碼的 QWORD 值。  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於，此方法會將它加入索引鍵。  
  
 `qwValue`  
 QWORD 来儲存的資料具有指定的值名稱。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)來將值寫入至登錄。  
  
##  <a name="setstringvalue"></a>CRegKey::SetStringValue  
 呼叫這個方法來設定登錄機碼的字串值。  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszValueName`  
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於，此方法會將它加入索引鍵。  
  
 `pszValue`  
 要以指定的值名稱的字串資料的指標。  
  
 `dwType`  
 將字串寫入登錄的型別︰ REG_SZ （預設值） 或 REG_EXPAND_SZ （適用於 multistring)。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是 ERROR_SUCCESS。 如果方法失敗，則傳回的值會是 WINERROR 中定義的非零的錯誤代碼。H.  
  
### <a name="remarks"></a>備註  
 這個方法會使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923\(v=vs.85\).aspx)來將值寫入至登錄。  
  
##  <a name="setvalue"></a>CRegKey::SetValue  
 呼叫此方法以將資料儲存在指定的值欄位的[m_hKey](#m_hkey)。 這個方法的先前版本已不再受到支援，並會標示為**ATL_DEPRECATED**。  
  
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
 包含要設定的值名稱的字串指標。 如果具有此名稱的值已不存在於索引鍵中，此方法會將它加入索引鍵。 如果`pszValueName`是 NULL 或空字串，""、 方法設定的型別和索引鍵資料的未命名或預設值。  
  
 `dwType`  
 指定程式碼，指出所指的資料型別`pValue`參數。  
  
 `pValue`  
 包含要與指定的值名稱一起儲存的資料緩衝區的指標。  
  
 `nBytes`  
 指定的大小，以位元組為單位的資訊指向`pValue`參數。 如果資料類型 REG_SZ、 REG_EXPAND_SZ 或 REG_MULTI_SZ，`nBytes`必須包含結束的 null 字元的大小。  
  
 `hKeyParent`  
 開啟機碼的控制代碼。  
  
 `lpszKeyName`  
 指定用來建立或開啟金鑰的名稱。 此名稱必須是子機碼的`hKeyParent`。  
  
 `lpszValue`  
 指定要儲存的資料。 這個參數必須為非 NULL。  
  
 `lpszValueName`  
 指定要設定的值欄位。 如果機碼中已存在具有此名稱的值欄位，會將它加入。  
  
 `dwValue`  
 指定要儲存的資料。  
  
 `bMulti`  
 如果為 false，指出字串的類型為 REG_SZ。 如果為 true，表示字串的型別 REG_MULTI_SZ multistring。  
  
 `nValueLen`  
 如果`bMulti`為 true，`nValueLen`的長度*lpszValue*中字元的字串。 如果`bMulti`為 false，-1 值表示此方法將會自動計算長度。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回 ERROR_SUCCESS;否則，為非零的錯誤碼 WINERROR 中定義。H.  
  
### <a name="remarks"></a>備註  
 兩個原始版本`SetValue`標示為**ATL_DEPRECATED** ，應該不會再使用。 如果使用這些表單，則編譯器會發出警告。  
  
 第三個方法呼叫[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)。  
  
## <a name="see-also"></a>另請參閱  
 [DCOM 範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)

