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
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318460"
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
|[CSettingsStore:CSettingsStore](#csettingsstore)|建構 `CSettingsStore` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSettingsStore:關閉](#close)|關閉打開的註冊表項。|
|[CSettingsStore:建立金鑰](#createkey)|打開指定的密鑰,如果不存在,則將其創建。|
|[CSettingsStore::Delete密鑰](#deletekey)|刪除指定的金鑰及其所有子級。|
|[CSettingsStore::Delete值](#deletevalue)|刪除開啟金鑰的指定值。|
|[CSettingsStore::打開](#open)|開啟指定的金鑰。|
|[設定儲存:閱讀](#read)|檢索指定鍵值的數據。|
|[CSettingsStore:寫入](#write)|在打開的鍵下向註冊表寫入值。|

## <a name="remarks"></a>備註

成員的功能`CreateKey``Open`和非常相似。 如果註冊表項已存在,`CreateKey``Open`並且 以相同的方式運行。 但是,如果註冊表項不存在,`CreateKey`將建立它,`Open`而將返回錯誤值。

## <a name="example"></a>範例

下面的範例示範如何使用`CSettingsStore`類的"打開"和"讀取"方法。 此代碼段是[工具提示演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>需求

**標題:** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore:關閉

關閉打開的註冊表項。

```
virtual void Close();
```

### <a name="remarks"></a>備註

默認情況下,此方法是從[CSettingsStore 類](../../mfc/reference/csettingsstore-class.md)的析構函數調用的。

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore:建立金鑰

打開註冊表項或創建註冊表項(如果不存在)。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
[在]指定要建立或打開的鍵的名稱。

### <a name="return-value"></a>傳回值

0 如果成功;否則為非零值。

### <a name="remarks"></a>備註

`CreateKey`用作`m_hKey`註冊表查詢的根。 它搜索*pszPath*`m_hKey`作為的子鍵。 如果金鑰不存在,`CreateKey`請建立它。 否則,它將打開密鑰。 `CreateKey`然後設置`m_hKey`到創建或打開的鍵。

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore:CSettingsStore

建立 `CSettngsStore` 物件。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>參數

*bAdmin*<br/>
[在]布爾參數,用於指定`CSettingsStore`物件是否在管理員模式下運行。

*b 唯讀*<br/>
[在]布爾參數,用於指定物件是否`CSettingsStore`以唯讀模式創建。

### <a name="remarks"></a>備註

如果*bAdmin*設定為`m_hKey`TRUE, 則成員變數設定為**HKEY_LOCAL_MACHINE**。 如果將*bAdmin*設定為 FALSE,`m_hKey`則設定為**HKEY_CURRENT_USER**。

安全訪問取決於*bReadOnly*參數。 如果*bReadONLY*為 FALSE,則安全訪問將設定為**KEY_ALL_ACCESS**。 如果*bReadyOnly*為 TRUE,則安全訪問將設置為**KEY_QUERY_VALUE、KEY_NOTIFY**和**KEY_ENUMERATE_SUB_KEYS**的組合。 有關安全存取與註冊表的詳細資訊,請參閱[註冊表金鑰安全和存取權限](/windows/win32/SysInfo/registry-key-security-and-access-rights)。

自動釋放`CSettingsStore``m_hKey`的析構函數。

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::Delete密鑰

從註冊表中刪除金鑰及其所有子級。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
[在]要刪除的鍵的名稱。

*bAdmin*<br/>
[在]指定要刪除的鍵的位置的交換機。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果物件處於唯讀模式`CSettingsStore`,此方法將失敗。

如果參數*bAdmin*`DeleteKey`為零 ,則搜尋**要刪除的鍵HKEY_CURRENT_USER**。 如果*bAdmin*是`DeleteKey`非零 ,則搜索要刪除**的HKEY_LOCAL_MACHINE**下的密鑰。

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::Delete值

從`m_hKey`中刪除值。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>參數

*pszValue*<br/>
[在]指定要刪除的值欄位。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore::打開

打開註冊表項。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
[在]註冊表項的名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此方法成功打開指定的密鑰後,它將設置`m_hKey`為此密鑰的句柄。

## <a name="csettingsstoreread"></a><a name="read"></a>設定儲存:閱讀

從註冊表中的鍵讀取值。

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
[在]指向 null 終止字串的指標,該字串包含要從註冊表讀取的值的名稱。

*伊瓦爾*<br/>
[出]引用從註冊表鍵讀取的值的整數變數。

*德瓦爾*<br/>
[出]引用從註冊表鍵讀取的值的 32 位雙字變數。

*斯瓦爾*<br/>
[出]引用從註冊表鍵讀取的值的字串變數。

*scStringlist*<br/>
[出]引用從註冊表鍵讀取的值的字串清單變數。

*scArray*<br/>
[出]引用從註冊表鍵讀取的值的字串陣列變數。

*dwcArray*<br/>
[出]引用 32 位元雙字陣組變數,該變數接收從註冊表項讀取的值。

*wcArray*<br/>
[出]引用從註冊表鍵讀取的值的 16 位單片組變數。

*bcArray*<br/>
[出]引用從註冊表鍵讀取的值的位元組變數組變數。

*lpPoint*<br/>
[出]引用指向從註冊表鍵讀取`POINT`的值的結構的指標。

*矩形*<br/>
[出]引用從註冊表項讀取的值的[CRect](../../atl-mfc-shared/reference/crect-class.md)變數。

*ppData*<br/>
[出]指向從註冊表鍵讀取的值的數據的指標。

*p 位元組*<br/>
[出]指向無符號整數變數的指標。 此變數接收*ppData*指向的緩衝區的大小。

list<br/>
[出]引用從註冊表項讀取的值的[CObList](../../mfc/reference/coblist-class.md)變數。

*obj*<br/>
[出]引用從註冊表鍵讀取的值的[CObject](../../mfc/reference/cobject-class.md)變數。

*pObj*<br/>
[出]引用指向從註冊表鍵讀取`CObject`的值的變數的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Read`檢查*pszKey*`m_hKey`作為的子鍵。

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore:寫入

在打開的鍵下向註冊表寫入值。

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
[在]指向包含要設定的值名稱的字串的指標。

*伊瓦爾*<br/>
[在]對包含要存儲的數據的整數變數的引用。

*德瓦爾*<br/>
[在]引用包含要存儲的數據的 32 位元雙字變數。

*pszVal*<br/>
[在]包含要儲存資料的 null 中斷字串變數的指標。

*scStringlist*<br/>
[在]引用包含要存儲的數據的[CStringList](../../mfc/reference/cstringlist-class.md)變數。

*bcArray*<br/>
[在]對包含要存儲的數據的位元組變數的引用。

*scArray*<br/>
[在]對包含要儲存資料的字串陣列變數的引用。

*dwcArray*<br/>
[在]引用包含要存儲的數據的 32 位元雙字陣組變數。

*wcArray*<br/>
[在]引用包含要存儲的數據的 16 位元單字元組變數。

*矩形*<br/>
[在]對包含要存儲的數據的[CRect](../../atl-mfc-shared/reference/crect-class.md)變數的引用。

*lpPoint*<br/>
[在]引用指向包含要存儲的數據`POINT`的變數的指標。

*pData*<br/>
[在]指向包含要存儲的數據的緩衝區的指標。

*n 位元組*<br/>
[在]指定*pData*參數指向的資料大小(以位元組為單位)。

list<br/>
[在]引用包含要儲存的數據的[CObList](../../mfc/reference/coblist-class.md)變數。

*obj*<br/>
[在]對包含要儲存資料的[CObject](../../mfc/reference/cobject-class.md)變數的引用。

*pObj*<br/>
[在]指向包含要存儲的數據的`CObject`變數的指標。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

為了寫入註冊表,在創建[CSettingsStore](../../mfc/reference/csettingsstore-class.md)物件時,必須將*bReadOnly*設置為非零值。 有關詳細資訊,請參閱[CSettingsStore:CSettingsStore](#csettingsstore)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
