---
title: "CSettingsStore 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSettingsStore
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStore class
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
caps.latest.revision: 29
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
ms.sourcegitcommit: 0b07f6b12e178d8e324313ea3b0f6de9ae7420c9
ms.openlocfilehash: 0918c8dd9b6284adecb61bc95ddfd41c22d16cb8
ms.lasthandoff: 02/24/2017

---
# <a name="csettingsstore-class"></a>CSettingsStore Class
包裝 Windows 應用程式開發介面函式，提供用來存取登錄的物件導向介面。  
  
## <a name="syntax"></a>語法  
  
```  
class CSettingsStore : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSettingsStore::CSettingsStore](#csettingsstore)|建構 `CSettingsStore` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSettingsStore::Close](#close)|關閉開啟登錄機碼。|  
|[CSettingsStore::CreateKey](#createkey)|開啟指定的索引鍵，或不存在時建立。|  
|[CSettingsStore::DeleteKey](#deletekey)|刪除指定的索引鍵和其所有子系。|  
|[CSettingsStore::DeleteValue](#deletevalue)|刪除的開放式金鑰指定的值。|  
|[CSettingsStore::Open](#open)|開啟指定的索引鍵。|  
|[CSettingsStore::Read](#read)|擷取指定之索引鍵值的資料。|  
|[CSettingsStore::Write](#write)|將值寫入開啟登錄機碼底下。|  
  
## <a name="remarks"></a>備註  
 成員函式`CreateKey`和`Open`非常類似。 如果登錄機碼已經存在，`CreateKey`和`Open`函式相同的方式。 不過，如果登錄機碼不存在，`CreateKey`會建立它而`Open`會傳回錯誤值。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用的開啟和讀取方法`CSettingsStore`類別。 此程式碼片段是一部分[工具提示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_ToolTipDemo #&1;](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSettingsStore`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxsettingsstore.h  
  
##  <a name="a-nameclosea--csettingsstoreclose"></a><a name="close"></a>CSettingsStore::Close  
 關閉開啟登錄機碼。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 根據預設，呼叫這個方法的解構函式從[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。  
  
##  <a name="a-namecreatekeya--csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore::CreateKey  
 開啟登錄機碼，或不存在時建立。  
  
```  
virtual BOOL CreateKey(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszPath`  
 指定用來建立或開啟金鑰的名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為&0;否則為非零值。  
  
### <a name="remarks"></a>備註  
 `CreateKey`使用`m_hKey`登錄查詢的根。 它會搜尋`pszPath`的子機碼為`m_hKey`。 如果索引鍵不存在，`CreateKey`會加以建立。 否則，它會開啟索引鍵。 `CreateKey`然後設定`m_hKey`建立或開啟的索引鍵。  
  
##  <a name="a-namecsettingsstorea--csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore::CSettingsStore  
 建立 `CSettngsStore` 物件。  
  
```  
CSettingsStore(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAdmin`  
 布林值參數，指定是否`CSettingsStore`物件就會把自己以系統管理員模式。  
  
 [in] `bReadOnly`  
 布林值參數，指定是否`CSettingsStore`唯讀模式中建立物件。  
  
### <a name="remarks"></a>備註  
 如果`bAdmin`設為`false`、`m_hKey`成員變數會設為`HKEY_LOCAL_MACHINE`。 If you set `bAdmin` to `true`, `m_hKey` is set to `HKEY_CURRENT_USER`.  
  
 安全性存取權取決於`bReadOnly`參數。 如果`bReadonly`是`false`，安全性的存取將會設定為`KEY_ALL_ACCESS`。 如果`bReadyOnly`是`true`，安全性存取將會設定為結合`KEY_QUERY_VALUE, KEY_NOTIFY`和`KEY_ENUMERATE_SUB_KEYS`。 如需詳細的安全性存取權，以及登錄的詳細資訊，請參閱[登錄機碼的安全性和存取權限](http://msdn.microsoft.com/library/windows/desktop/ms724878)。  
  
 解構函式的`CSettingsStore`釋放`m_hKey`自動。  
  
##  <a name="a-namedeletekeya--csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::DeleteKey  
 刪除登錄機碼及其所有子系。  
  
```  
virtual BOOL DeleteKey(
    LPCTSTR pszPath,  
    BOOL bAdmin = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszPath`  
 若要刪除的索引鍵名稱。  
  
 [in] `bAdmin`  
 指定要刪除之索引鍵位置的參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果此方法將會失敗`CSettingsStore`物件處於唯讀模式。  
  
 如果參數`bAdmin`為零，`DeleteKey`搜尋索引鍵，以刪除下`HKEY_CURRENT_USER`。 如果`bAdmin`是零，`DeleteKey`搜尋索引鍵，以刪除下`HKEY_LOCAL_MACHINE`。  
  
##  <a name="a-namedeletevaluea--csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::DeleteValue  
 刪除值，以從`m_hKey`。  
  
```  
virtual BOOL DeleteValue(LPCTSTR pszValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszValue`  
 指定要移除的值欄位。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="a-nameopena--csettingsstoreopen"></a><a name="open"></a>CSettingsStore::Open  
 開啟登錄機碼。  
  
```  
virtual BOOL Open(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszPath`  
 登錄機碼名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法已成功開啟指定的索引鍵之後，它會設定`m_hKey`這個機碼的控制代碼。  
  
##  <a name="a-namereada--csettingsstoreread"></a><a name="read"></a>CSettingsStore::Read  
 從登錄機碼讀取值。  
  
```  
virtual BOOL Read(
    LPCTSTR pszKey,  
    int& iVal);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    DWORD& dwVal);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CString& sVal);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CStringList& scStringList);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CStringArray& scArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CDWordArray& dwcArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CWordArray& wcArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CByteArray& bcArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    LPPOINT& lpPoint);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CRect& rect);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    BYTE** ppData,  
    UINT* pBytes);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CObList& list);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CObject& obj);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CObject*& pObj);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszKey`  
 以 null 終止的字串，其中包含要讀取登錄值名稱的指標。  
  
 [輸出] `iVal`  
 接收從登錄機碼讀取值的整數變數的參考。  
  
 [輸出] `dwVal`  
 接收從登錄機碼讀取值的 32 位元雙字組變數參考。  
  
 [輸出] `sVal`  
 接收從登錄機碼讀取值的字串變數的參考。  
  
 [輸出] `scStringList`  
 接收從登錄機碼讀取值的字串清單變數參考。  
  
 [輸出] `scArray`  
 接收從登錄機碼讀取值的字串陣列變數參考。  
  
 [輸出] `dwcArray`  
 接收從登錄機碼讀取值的 32 位元雙字組陣列變數參考。  
  
 [輸出] `wcArray`  
 接收從登錄機碼讀取值的 16 位元字組陣列變數參考。  
  
 [輸出] `bcArray`  
 接收從登錄機碼讀取值的位元組陣列變數參考。  
  
 [輸出] `lpPoint`  
 參考的指標`POINT`接收值的結構讀取登錄機碼。  
  
 [輸出] `rect`  
 若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)變數接收值讀取登錄機碼。  
  
 [輸出] `ppData`  
 從登錄機碼讀取接收值的資料指標的指標。  
  
 [輸出] `pBytes`  
 不帶正負號的整數變數的指標。 此變數會接收緩衝區的大小，`ppData`指向。  
  
 [輸出] `list`  
 若要參考[CObList](../../mfc/reference/coblist-class.md)變數接收值讀取登錄機碼。  
  
 [輸出] `obj`  
 若要參考[CObject](../../mfc/reference/cobject-class.md)變數接收值讀取登錄機碼。  
  
 [輸出] `pObj`  
 參考的指標`CObject`變數接收值讀取登錄機碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `Read`檢查是否有`pszKey`的子機碼為`m_hKey`。  
  
##  <a name="a-namewritea--csettingsstorewrite"></a><a name="write"></a>CSettingsStore::Write  
 將值寫入開啟登錄機碼底下。  
  
```  
virtual BOOL Write(
    LPCTSTR pszKey,  
    int iVal);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    DWORD dwVal);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    LPCTSTR pszVal);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CStringList& scStringList);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CByteArray& bcArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CStringArray& scArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CDWordArray& dwcArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CWordArray& wcArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    const CRect& rect);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    LPPOINT& lpPoint);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    LPBYTE pData,  
    UINT nBytes);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CObList& list);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CObject& obj);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CObject* pObj);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszKey`  
 字串，其中包含要設定的值名稱的指標。  
  
 [in] `iVal`  
 整數變數，其中包含要儲存資料的參考。  
  
 [in] `dwVal`  
 32 位元雙字組變數，其中包含要儲存資料的參考。  
  
 [in] `pszVal`  
 Null 結束的字串變數，其中包含要儲存的資料指標。  
  
 [in] `scStringList`  
 若要參考[CStringList](../../mfc/reference/cstringlist-class.md)變數，其中包含要儲存的資料。  
  
 [in] `bcArray`  
 包含要儲存資料的位元組陣列變數參考。  
  
 [in] `scArray`  
 包含要儲存資料的字串陣列變數參考。  
  
 [in] `dwcArray`  
 包含要儲存資料的 32 位元雙字組陣列變數參考。  
  
 [in] `wcArray`  
 包含要儲存資料的 16 位元字組陣列變數參考。  
  
 [in] `rect`  
 若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)變數，其中包含要儲存的資料。  
  
 [in] `lpPoint`  
 參考的指標`POINT`變數，其中包含要儲存的資料。  
  
 [in] `pData`  
 包含要儲存資料的緩衝區指標。  
  
 [in] `nBytes`  
 指定的大小，以位元組為單位之資料`pData`參數點。  
  
 [in] `list`  
 若要參考[CObList](../../mfc/reference/coblist-class.md)變數，其中包含要儲存的資料。  
  
 [in] `obj`  
 若要參考[CObject](../../mfc/reference/cobject-class.md)變數，其中包含要儲存的資料。  
  
 [in] `pObj`  
 指標的指標`CObject`變數，其中包含要儲存的資料。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 若要寫入登錄，您必須為`bReadOnly`為非零值，當您建立[CSettingsStore](../../mfc/reference/csettingsstore-class.md)物件。 如需詳細資訊，請參閱[CSettingsStore::CSettingsStore](#csettingsstore)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [Cwinappex 衍生類別](../../mfc/reference/cwinappex-class.md)

