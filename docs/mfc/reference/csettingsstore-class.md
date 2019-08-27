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
ms.openlocfilehash: 75d86b81d9651e5892913af5919ae0a78fe6bbc5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502914"
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
|[Csettingsstore 協助程式:: Csettingsstore 協助程式](#csettingsstore)|建構 `CSettingsStore` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSettingsStore::Close](#close)|關閉開啟的登錄機碼。|
|[CSettingsStore::CreateKey](#createkey)|開啟指定的索引鍵, 如果不存在, 則加以建立。|
|[CSettingsStore::DeleteKey](#deletekey)|刪除指定的索引鍵和其所有子系。|
|[CSettingsStore::DeleteValue](#deletevalue)|刪除 open 索引鍵的指定值。|
|[CSettingsStore::Open](#open)|開啟指定的索引鍵。|
|[CSettingsStore::Read](#read)|抓取指定之索引鍵值的資料。|
|[CSettingsStore::Write](#write)|以 open 鍵將值寫入登錄。|

## <a name="remarks"></a>備註

成員`CreateKey`函式和`Open`非常類似。 如果登錄機碼已經存在, `CreateKey`且`Open`以相同的方式運作。 不過, 如果登錄機碼不存在, 則`CreateKey`會建立它, `Open`而會傳回錯誤值。

## <a name="example"></a>範例

下列範例示範如何使用`CSettingsStore`類別的 Open 和 Read 方法。 此程式碼片段是[工具提示示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>需求

**標頭:** afxsettingsstore。h

##  <a name="close"></a>Csettingsstore 協助程式:: Close

關閉開啟的登錄機碼。

```
virtual void Close();
```

### <a name="remarks"></a>備註

根據預設, 會從[Csettingsstore 協助程式類別](../../mfc/reference/csettingsstore-class.md)的析構函式呼叫這個方法。

##  <a name="createkey"></a>Csettingsstore 協助程式:: CreateKey

開啟登錄機碼, 如果不存在, 則會建立它。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
在指定要建立或開啟之金鑰的名稱。

### <a name="return-value"></a>傳回值

如果成功, 則為 0;否則為非零值。

### <a name="remarks"></a>備註

`CreateKey`使用`m_hKey`做為登錄查詢的根目錄。 它會搜尋*pszPath*作為的`m_hKey`子機碼。 如果機碼不存在, `CreateKey`則會建立它。 否則, 它會開啟金鑰。 `CreateKey`然後將`m_hKey`設定為已建立或已開啟的索引鍵。

##  <a name="csettingsstore"></a>Csettingsstore 協助程式:: Csettingsstore 協助程式

建立 `CSettngsStore` 物件。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>參數

*bAdmin*<br/>
在布林值參數, 指定`CSettingsStore`物件是否在系統管理員模式下作用。

*bReadOnly*<br/>
在布林值參數, 指定是否`CSettingsStore`在唯讀模式中建立物件。

### <a name="remarks"></a>備註

如果*bAdmin*設定為 TRUE, 則`m_hKey`成員變數會設定為**HKEY_LOCAL_MACHINE**。 如果您將*bAdmin*設定為 FALSE `m_hKey` , 會設定為**HKEY_CURRENT_USER**。

安全性存取權取決於*bReadOnly*參數。 如果*bReadonly*為 FALSE, 安全性存取將會設定為**KEY_ALL_ACCESS**。 如果*bReadyOnly*為 TRUE, 安全性存取將會設定為**KEY_QUERY_VALUE、KEY_NOTIFY**和**KEY_ENUMERATE_SUB_KEYS**的組合。 如需有關安全性存取與登錄的詳細資訊, 請參閱登錄機[碼安全性和存取權限](/windows/win32/SysInfo/registry-key-security-and-access-rights)。

自動`CSettingsStore` 釋放`m_hKey`的析構函式。

##  <a name="deletekey"></a>Csettingsstore 協助程式::D eleteKey

從登錄中刪除機碼及其所有子系。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
在要刪除的索引鍵名稱。

*bAdmin*<br/>
在指定要刪除之索引鍵位置的參數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果`CSettingsStore`物件處於唯讀模式, 這個方法將會失敗。

如果參數*bAdmin*為零, `DeleteKey`則會在**HKEY_CURRENT_USER**下搜尋要刪除的索引鍵。 如果*bAdmin*為非零`DeleteKey`值, 會在**HKEY_LOCAL_MACHINE**下搜尋要刪除的金鑰。

##  <a name="deletevalue"></a>Csettingsstore 協助程式::D eleteValue

從`m_hKey`刪除值。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>參數

*pszValue*<br/>
在指定要移除的值欄位。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="open"></a>Csettingsstore 協助程式:: Open

開啟登錄機碼。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
在登錄機碼的名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

當這個方法成功開啟指定的索引鍵之後, `m_hKey`它會將設定為這個機碼的控制碼。

##  <a name="read"></a>Csettingsstore 協助程式:: Read

從登錄中的機碼讀取值。

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
在以 null 結束的字串指標, 其中包含要從登錄讀取的值名稱。

*iVal*<br/>
脫銷參考從登錄機碼讀取值的整數變數。

*dwVal*<br/>
脫銷參考32位雙重單字變數, 其會接收從登錄機碼讀取的值。

*sVal*<br/>
脫銷參考會接收從登錄機碼讀取之值的字串變數。

*scStringList*<br/>
脫銷參考字串清單變數, 其會接收從登錄機碼讀取的值。

*scArray*<br/>
脫銷參考字串陣列變數, 其會接收從登錄機碼讀取的值。

*dwcArray*<br/>
脫銷參考32位的雙字陣列變數, 其會接收從登錄機碼讀取的值。

*wcArray*<br/>
脫銷參考接受從登錄機碼讀取之值的16位字組陣列變數。

*bcArray*<br/>
脫銷接收從登錄機碼讀取之值的位元組陣列變數的參考。

*lpPoint*<br/>
脫銷參考`POINT`結構的指標, 該結構會接收從登錄機碼讀取的值。

*rect*<br/>
脫銷[CRect](../../atl-mfc-shared/reference/crect-class.md)變數的參考, 它會接收從登錄機碼讀取的值。

*ppData*<br/>
脫銷資料指標的指標, 可接收從登錄機碼讀取的值。

*pBytes*<br/>
脫銷不帶正負號整數變數的指標。 這個變數會接收*ppData*指向的緩衝區大小。

*list*<br/>
脫銷[CObList](../../mfc/reference/coblist-class.md)變數的參考, 它會接收從登錄機碼讀取的值。

*obj*<br/>
脫銷可接收從登錄機碼讀取之值的[CObject](../../mfc/reference/cobject-class.md)變數的參考。

*pObj*<br/>
脫銷參考會接收從登錄機`CObject`碼讀取之值的變數指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Read`檢查*pszKey*是否為的子`m_hKey`機碼。

##  <a name="write"></a>Csettingsstore 協助程式:: Write

以 open 鍵將值寫入登錄。

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
在字串的指標, 其中包含要設定的值名稱。

*iVal*<br/>
在參考包含要儲存之資料的整數變數。

*dwVal*<br/>
在參考包含要儲存之資料的32位雙重單字變數。

*pszVal*<br/>
在以 null 結束的字串變數的指標, 其中包含要儲存的資料。

*scStringList*<br/>
在參考包含要儲存之資料的[CStringList](../../mfc/reference/cstringlist-class.md)變數。

*bcArray*<br/>
在包含要儲存之資料的位元組陣列變數的參考。

*scArray*<br/>
在參考包含要儲存之資料的字串陣列變數。

*dwcArray*<br/>
在參考包含要儲存之資料的32位雙字陣列變數。

*wcArray*<br/>
在參考包含要儲存之資料的16位字組陣列變數。

*rect*<br/>
在參考包含要儲存之資料的[CRect](../../atl-mfc-shared/reference/crect-class.md)變數。

*lpPoint*<br/>
在參考包含要儲存之資料`POINT`的變數指標。

*pData*<br/>
在包含要儲存之資料的緩衝區指標。

*nBytes*<br/>
在指定*pData*參數所指向的資料大小 (以位元組為單位)。

*list*<br/>
在參考包含要儲存之資料的[CObList](../../mfc/reference/coblist-class.md)變數。

*obj*<br/>
在包含要儲存之資料的[CObject](../../mfc/reference/cobject-class.md)變數的參考。

*pObj*<br/>
在指向包含要儲存之資料`CObject`的變數指標。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

若要寫入登錄, 您必須在建立[csettingsstore 協助程式](../../mfc/reference/csettingsstore-class.md)物件時, 將*bReadOnly*設定為非零值。 如需詳細資訊, 請參閱[csettingsstore 協助程式:: csettingsstore 協助程式](#csettingsstore)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
