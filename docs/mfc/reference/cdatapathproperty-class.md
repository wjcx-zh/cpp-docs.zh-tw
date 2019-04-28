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
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253527"
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
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|建構 `CDataPathProperty` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDataPathProperty::GetControl](#getcontrol)|擷取相關聯的非同步 OLE 控制項`CDataPathProperty`物件。|
|[CDataPathProperty::GetPath](#getpath)|擷取屬性的路徑名稱。|
|[CDataPathProperty::Open](#open)|會起始載入相關聯的 ActiveX (OLE) 控制項的非同步屬性。|
|[CDataPathProperty::ResetData](#resetdata)|呼叫`CAsyncMonikerFile::OnDataAvailable`以告知容器控制項的屬性已變更。|
|[CDataPathProperty::SetControl](#setcontrol)|設定與屬性相關聯的非同步 ActiveX (OLE) 控制。|
|[CDataPathProperty::SetPath](#setpath)|設定屬性的路徑名稱。|

## <a name="remarks"></a>備註

非同步屬性會在同步初始之後載入。

此類別`CDataPathProperty`衍生自`CAysncMonikerFile`。 若要實作非同步屬性中 OLE 控制項，衍生的類別`CDataPathProperty`，並覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。

如需如何在網際網路應用程式中使用非同步 moniker 和 ActiveX 控制項的詳細資訊，請參閱下列文章：

- [網際網路的第一個步驟：ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)

- [網際網路的第一個步驟：非同步 Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>需求

**標頭：** afxctl.h

##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty

建構 `CDataPathProperty` 物件。

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>參數

*pControl*<br/>
要與此相關聯的 OLE 控制項物件的指標`CDataPathProperty`物件。

*lpszPath*<br/>
此路徑，可能是絕對或相對，以用來建立實際的絕對位置的屬性會參考非同步 moniker。 `CDataPathProperty` 使用不是檔案名稱的 Url。 如果您想`CDataPathProperty`物件的檔案，在前面加上`file://`的路徑。

### <a name="remarks"></a>備註

`COleControl`指向的物件*pControl*正由`Open`，並且擷取衍生的類別。 如果*pControl*是 NULL，搭配使用的控制項`Open`應該設有`SetControl`。 如果*lpszPath*是 NULL 時，您可以透過路徑中傳遞`Open`，或將它與`SetPath`。

##  <a name="getcontrol"></a>  CDataPathProperty::GetControl

呼叫此成員函式，來擷取`COleControl`相關聯的物件`CDataPathProperty`物件。

```
COleControl* GetControl();
```

### <a name="return-value"></a>傳回值

傳回指向 OLE 控制項的相關聯`CDataPathProperty`物件。 NULL，如果沒有控制項有關聯。

##  <a name="getpath"></a>  CDataPathProperty::GetPath

呼叫此成員函式，若要擷取的路徑，設定何時`CDataPathProperty`物件已建構，或指定`Open`，或由先前呼叫中指定`SetPath`成員函式。

```
CString GetPath() const;
```

### <a name="return-value"></a>傳回值

屬性本身傳回的路徑名稱。 可以是空白，如果已指定沒有路徑。

##  <a name="open"></a>  CDataPathProperty::Open

呼叫此成員函式，來起始非同步屬性相關聯控制項的載入。

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
要與此相關聯的 OLE 控制項物件的指標`CDataPathProperty`物件。

*pError*<br/>
檔案例外狀況的指標。 發生錯誤時，將可能的原因。

*lpszPath*<br/>
此路徑，可能是絕對或相對，以用來建立實際的絕對位置的屬性會參考非同步 moniker。 `CDataPathProperty` 使用不是檔案名稱的 Url。 如果您想`CDataPathProperty`物件的檔案，在前面加上`file://`的路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

函式會嘗試取得`IBindHost`從控制項的介面。

然後再呼叫`Open`沒有路徑，您必須設定的屬性路徑的值。 這可以建構，或藉由呼叫物件時完成`SetPath`成員函式。

然後再呼叫`Open`沒有控制，ActiveX 控制項 （先前稱為 OLE 控制項） 可以是與物件相關聯。 這可以建構，或藉由呼叫物件時完成`SetControl`。

所有多載[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)也會提供從`CDataPathProperty`。

##  <a name="resetdata"></a>  CDataPathProperty::ResetData

呼叫此函式可取得`CAsyncMonikerFile::OnDataAvailable`以告知容器控制項的屬性已變更，，和以非同步方式載入的所有資訊都都不再有用。

```
virtual void ResetData();
```

### <a name="remarks"></a>備註

開啟應該重新啟動。 在衍生的類別可以覆寫這個函式供不同的預設值。

##  <a name="setcontrol"></a>  CDataPathProperty::SetControl

呼叫此成員函式，將非同步 OLE 控制項與`CDataPathProperty`物件。

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>參數

*pControl*<br/>
以非同步的 OLE 控制項要與屬性相關聯的指標。

##  <a name="setpath"></a>  CDataPathProperty::SetPath

呼叫此成員函式，若要設定之屬性的路徑名稱。

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
路徑，可能是絕對或相對路徑，以非同步方式載入的屬性。 `CDataPathProperty` 使用不是檔案名稱的 Url。 如果您想`CDataPathProperty`物件的檔案，在前面加上`file://`的路徑。

## <a name="see-also"></a>另請參閱

[MFC 範例映像](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
