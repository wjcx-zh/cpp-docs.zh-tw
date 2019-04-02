---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: 1e1373da86c1c3fea3b1ddd6ff17f0fac4f76980
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770391"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

包裝 Windows 應用程式開發介面函式，提供用來存取登錄的物件導向介面。

## <a name="syntax"></a>語法

```
class CSettingsStore : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|建構 `CSettingsStore` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSettingsStore::Close](#close)|關閉開啟登錄機碼。|
|[CSettingsStore::CreateKey](#createkey)|開啟指定的索引鍵，或建立它，如果不存在。|
|[CSettingsStore::DeleteKey](#deletekey)|刪除指定的索引鍵和其所有子系。|
|[CSettingsStore::DeleteValue](#deletevalue)|刪除開啟的索引鍵指定的值。|
|[CSettingsStore::Open](#open)|開啟指定的索引鍵。|
|[CSettingsStore::Read](#read)|擷取指定的索引鍵值的資料。|
|[CSettingsStore::Write](#write)|您可以將值寫入開啟機碼下登錄。|

## <a name="remarks"></a>備註

成員函式`CreateKey`和`Open`非常類似。 如果登錄機碼已經存在，`CreateKey`和`Open`函式相同的方式。 不過，如果登錄機碼不存在，`CreateKey`會建立它而`Open`會傳回錯誤值。

## <a name="example"></a>範例

下列範例示範如何使用的開啟和讀取方法`CSettingsStore`類別。 此程式碼片段是一部分[工具提示示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>需求

**標頭：** afxsettingsstore.h

##  <a name="close"></a>  CSettingsStore::Close

關閉開啟登錄機碼。

```
virtual void Close();
```

### <a name="remarks"></a>備註

根據預設，此方法從的解構函式呼叫[CSettingsStore 類別](../../mfc/reference/csettingsstore-class.md)。

##  <a name="createkey"></a>  CSettingsStore::CreateKey

開啟登錄機碼，或如果不存在，請建立它。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
[in]指定要建立或開啟金鑰的名稱。

### <a name="return-value"></a>傳回值

如果成功則為 0否則為非零值。

### <a name="remarks"></a>備註

`CreateKey` 使用`m_hKey`登錄查詢的根。 它會搜尋*pszPath*的子機碼為`m_hKey`。 如果索引鍵不存在，`CreateKey`會加以建立。 否則，它會開啟索引鍵。 `CreateKey` 然後設定`m_hKey`建立或開啟索引鍵。

##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore

建立 `CSettngsStore` 物件。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>參數

*bAdmin*<br/>
[in]布林值參數，指定是否`CSettingsStore`物件扮演系統管理員模式。

*bReadOnly*<br/>
[in]布林值參數，指定是否`CSettingsStore`唯讀模式中建立物件。

### <a name="remarks"></a>備註

如果*bAdmin*設定為 TRUE，`m_hKey`成員變數會設為**HKEY_LOCAL_MACHINE**。 如果您設定*bAdmin*設為 FALSE，`m_hKey`設定為**HKEY_CURRENT_USER**。

安全性存取權取決於*bReadOnly*參數。 如果*bReadonly*為 FALSE 時，安全性存取將會設定為**KEY_ALL_ACCESS**。 如果*bReadyOnly*為 TRUE 時，安全性存取將會設定為一連串**KEY_QUERY_VALUE、 KEY_NOTIFY**並**KEY_ENUMERATE_SUB_KEYS**。 如需詳細的安全性存取權，以及登錄的詳細資訊，請參閱[登錄機碼的安全性和存取權限](/windows/desktop/SysInfo/registry-key-security-and-access-rights)。

解構函式`CSettingsStore`釋放`m_hKey`自動。

##  <a name="deletekey"></a>  CSettingsStore::DeleteKey

從登錄中刪除機碼及其所有子系。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
[in]若要刪除的索引鍵名稱。

*bAdmin*<br/>
[in]指定要刪除的金鑰位置的參數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

這個方法將會失敗，如果`CSettingsStore`物件處於唯讀模式。

如果參數*bAdmin*為零，`DeleteKey`搜尋下刪除鍵**HKEY_CURRENT_USER**。 如果*bAdmin*為非零值，`DeleteKey`搜尋下刪除鍵**HKEY_LOCAL_MACHINE**。

##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue

刪除值，以從`m_hKey`。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>參數

*pszValue*<br/>
[in]指定要移除的值欄位。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="open"></a>  CSettingsStore::Open

開啟登錄機碼。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
[in]登錄機碼的名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

這個方法已成功開啟指定的索引鍵之後，它會設定`m_hKey`這個機碼的控制代碼。

##  <a name="read"></a>  CSettingsStore::Read

讀取登錄機碼值。

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

*pszKey*<br/>
[in]以 null 終止的字串，其中包含要從登錄讀取的值名稱的指標。

*iVal*<br/>
[out]接收讀取登錄機碼值的整數變數的參考。

*dwVal*<br/>
[out]接收從登錄機碼讀取值的 32 位元雙字組變數的參考。

*sVal*<br/>
[out]接收讀取登錄機碼值的字串變數的參考。

*scStringList*<br/>
[out]接收從登錄機碼讀取值的字串清單變數參考。

*scArray*<br/>
[out]接收從登錄機碼讀取值的字串陣列變數的參考。

*dwcArray*<br/>
[out]接收從登錄機碼讀取值的 32 位元雙字組陣列變數的參考。

*wcArray*<br/>
[out]接收從登錄機碼讀取值的 16 位元字組陣列變數的參考。

*bcArray*<br/>
[out]接收從登錄機碼讀取值的位元組陣列變數的參考。

*lpPoint*<br/>
[out]參考的指標`POINT`接收值的結構會讀取登錄機碼。

*rect*<br/>
[out]若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)接收值的變數會讀取登錄機碼。

*ppData*<br/>
[out]指標，接收值的資料指標讀取的登錄機碼。

*pBytes*<br/>
[out]不帶正負號的整數變數的指標。 此變數會接收緩衝區的大小， *ppData*指向。

*list*<br/>
[out]若要參考[CObList](../../mfc/reference/coblist-class.md)接收值的變數會讀取登錄機碼。

*obj*<br/>
[out]若要參考[CObject](../../mfc/reference/cobject-class.md)接收值的變數會讀取登錄機碼。

*pObj*<br/>
[out]參考的指標`CObject`接收值的變數會讀取登錄機碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Read` 會檢查*pszKey*的子機碼為`m_hKey`。

##  <a name="write"></a>  CSettingsStore::Write

您可以將值寫入開啟機碼下登錄。

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

*pszKey*<br/>
[in]包含要設定的值名稱的字串指標。

*iVal*<br/>
[in]包含要儲存資料的整數變數的參考。

*dwVal*<br/>
[in]32 位元雙字組變數，其中包含要儲存的資料參考。

*pszVal*<br/>
[in]以 null 終止的字串變數，其中包含要儲存的資料指標。

*scStringList*<br/>
[in]若要參考[CStringList](../../mfc/reference/cstringlist-class.md)變數，其中包含要儲存的資料。

*bcArray*<br/>
[in]包含要儲存資料的位元組陣列變數的參考。

*scArray*<br/>
[in]包含要儲存資料的字串陣列變數的參考。

*dwcArray*<br/>
[in]32 位元雙字組陣列變數，其中包含要儲存的資料參考。

*wcArray*<br/>
[in]包含要儲存資料的 16 位元字組陣列變數的參考。

*rect*<br/>
[in]若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)變數，其中包含要儲存的資料。

*lpPoint*<br/>
[in]參考的指標`POINT`變數，其中包含要儲存的資料。

*pData*<br/>
[in]其中包含要儲存的資料緩衝區的指標。

*nBytes*<br/>
[in]指定的大小，以位元組為單位的資料*pData*參數所指向。

*list*<br/>
[in]若要參考[CObList](../../mfc/reference/coblist-class.md)變數，其中包含要儲存的資料。

*obj*<br/>
[in]若要參考[CObject](../../mfc/reference/cobject-class.md)變數，其中包含要儲存的資料。

*pObj*<br/>
[in]指標的指標`CObject`變數，其中包含要儲存的資料。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

若要寫入至登錄，您必須設定*bReadOnly*為非零值，當您建立[CSettingsStore](../../mfc/reference/csettingsstore-class.md)物件。 如需詳細資訊，請參閱 < [CSettingsStore::CSettingsStore](#csettingsstore)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
