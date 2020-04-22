---
title: CDataPathProperty 類別
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 479f5d47d9cff72d36dbd25e434182af1ba01ef4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754646"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 類別

實作可以非同步載入的 OLE 控制項屬性。

## <a name="syntax"></a>語法

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDataPath 屬性:CDataPath 屬性](#cdatapathproperty)|建構 `CDataPathProperty` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDataPath 屬性:取得控制](#getcontrol)|檢索與`CDataPathProperty`物件關聯的非同步 OLE 控制件。|
|[CDataPath 屬性:抓取路徑](#getpath)|檢索屬性的路徑名稱。|
|[CDataPath 屬性::開啟](#open)|啟動關聯 ActiveX (OLE) 控制元件的非同步屬性載入。|
|[CDataPath 屬性::重置資料](#resetdata)|呼叫`CAsyncMonikerFile::OnDataAvailable`以通知容器控制件屬性已更改。|
|[CDataPath 屬性:設定控制](#setcontrol)|設置與屬性關聯的非同步活動X (OLE) 控制項。|
|[CDataPath 屬性:設定路徑](#setpath)|設置屬性的路徑名稱。|

## <a name="remarks"></a>備註

非同步屬性會在同步初始之後載入。

類別`CDataPathProperty`的類別`CAysncMonikerFile`。 在 OLE 控制項中實現非同步屬性,`CDataPathProperty`請從指定的類別並重寫[OnData 可用](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。

有關如何在 Internet 應用程式中使用非同步名字器和 ActiveX 控制件的詳細資訊,請參閱以下文章:

- [互聯網第一步:主動X控制](../../mfc/activex-controls-on-the-internet.md)

- [互聯網第一步:異步月友](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream 檔案](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPath 屬性:CDataPath 屬性

建構 `CDataPathProperty` 物件。

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>參數

*pControl*<br/>
指向要與此`CDataPathProperty`物件關聯的 OLE 控制件物件的指標。

*lpszPath*<br/>
路徑可以是絕對的或相對的,用於創建引用屬性的實際絕對位置的異步名字物件。 `CDataPathProperty`使用 URL,而不是檔案名。 如果需要檔`CDataPathProperty`的物件,則準備`file://`路徑。

### <a name="remarks"></a>備註

`COleControl` *pControl*指向的物件`Open`由 派生類使用並檢索。 如果*pControl*為 NULL,則應`Open`使用`SetControl`設定與使用的控制項。 如果*lpszPath*為 NULL,則`Open`可以在路徑中`SetPath`透過或設定它 。

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPath 屬性:取得控制

調用此成員函數以檢索與`COleControl``CDataPathProperty`對象關聯的物件。

```
COleControl* GetControl();
```

### <a name="return-value"></a>傳回值

返回指向與物件關聯的 OLE 控制`CDataPathProperty`的指標。 NULL(如果不是控制項)是關聯的。

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPath 屬性:抓取路徑

調用此成員函數以檢索路徑、在構造`CDataPathProperty`物件時設置或在`Open`中 指定,或在上`SetPath`一次對成員函數的調用中指定。

```
CString GetPath() const;
```

### <a name="return-value"></a>傳回值

將路徑名稱返回到屬性本身。 如果未指定路徑,則可以為空。

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPath 屬性::開啟

調用此成員函數以啟動關聯控制件的非同步屬性載入。

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*pControl*<br/>
指向要與此`CDataPathProperty`物件關聯的 OLE 控制件物件的指標。

*pError*<br/>
指向文件異常的指標。 如果出現錯誤,將設置為原因。

*lpszPath*<br/>
路徑可以是絕對的或相對的,用於創建引用屬性的實際絕對位置的異步名字物件。 `CDataPathProperty`使用 URL,而不是檔案名。 如果需要檔`CDataPathProperty`的物件,則準備`file://`路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

函數嘗試從控制項獲取`IBindHost`介面。

在調用`Open`沒有路徑之前,必須設置屬性路徑的值。 這在構造物件時或調用`SetPath`成員函數可以完成。

在沒有控制項`Open`的情況下調用之前,可以與物件關聯 ActiveX 控制件(以前稱為 OLE 控制件)。 這可以在建構物件時完成,也可以呼叫`SetControl`。

[CAsyncMonikerFile 的所有過載功能::打開](../../mfc/reference/casyncmonikerfile-class.md#open)`CDataPathProperty`也可從 獲得。

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPath 屬性::重置資料

呼叫此函數以通知`CAsyncMonikerFile::OnDataAvailable`容器控制屬性已更改,並且以非同步方式載入的所有資訊不再有用。

```
virtual void ResetData();
```

### <a name="remarks"></a>備註

應重新啟動打開。 派生類可以針對不同的預設值重寫此函數。

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPath 屬性:設定控制

調用此成員函數將非同步 OLE 控制`CDataPathProperty`件與 物件關聯。

```cpp
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>參數

*pControl*<br/>
指向要與屬性關聯的非同步 OLE 控制件的指標。

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPath 屬性:設定路徑

調用此成員函數以設置屬性的路徑名稱。

```cpp
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
路徑(可以是絕對的或相對的)與非同步載入的屬性。 `CDataPathProperty`使用 URL,而不是檔案名。 如果需要檔`CDataPathProperty`的物件,則準備`file://`路徑。

## <a name="see-also"></a>另請參閱

[MFC 樣本影像](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
