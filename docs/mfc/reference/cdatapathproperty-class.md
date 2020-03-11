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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890820"
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
|[CDataPathProperty：： CDataPathProperty](#cdatapathproperty)|建構 `CDataPathProperty` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDataPathProperty：： GetControl](#getcontrol)|抓取與 `CDataPathProperty` 物件相關聯的非同步 OLE 控制項。|
|[CDataPathProperty：： GetPath](#getpath)|抓取屬性的路徑名稱。|
|[CDataPathProperty：： Open](#open)|起始載入相關聯 ActiveX （OLE）控制項的非同步屬性。|
|[CDataPathProperty：： ResetData](#resetdata)|呼叫 `CAsyncMonikerFile::OnDataAvailable`，以通知容器控制項屬性已變更。|
|[CDataPathProperty：： SetControl](#setcontrol)|設定與屬性相關聯的非同步 ActiveX （OLE）控制項。|
|[CDataPathProperty：： SetPath](#setpath)|設定屬性的路徑名稱。|

## <a name="remarks"></a>備註

非同步屬性會在同步初始之後載入。

類別 `CDataPathProperty` 衍生自 `CAysncMonikerFile`。 若要在您的 OLE 控制項中執行非同步屬性，請從 `CDataPathProperty`衍生類別，並覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。

如需如何在網際網路應用程式中使用非同步名字和 ActiveX 控制項的詳細資訊，請參閱下列文章：

- [網際網路的第一個步驟： ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)

- [網際網路第一個步驟：非同步名字](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>需求

**標頭：** afxctl.h。h

##  <a name="cdatapathproperty"></a>CDataPathProperty：： CDataPathProperty

建構 `CDataPathProperty` 物件。

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>參數

*pControl*<br/>
要與這個 `CDataPathProperty` 物件相關聯之 OLE 控制項物件的指標。

*lpszPath*<br/>
可以是絕對或相對路徑，用來建立可參考屬性實際絕對位置的非同步名字標記。 `CDataPathProperty` 使用 Url，而不是檔案名。 如果您想要檔案的 `CDataPathProperty` 物件，請在路徑前面加上 `file://`。

### <a name="remarks"></a>備註

*PControl*所指向的 `COleControl` 物件是由衍生類別用 `Open` 和抓取。 如果*pControl*為 Null，則與 `Open` 搭配使用的控制項應設定 `SetControl`。 如果*lpszPath*為 Null，您可以透過 `Open` 傳入路徑，或使用 `SetPath`加以設定。

##  <a name="getcontrol"></a>CDataPathProperty：： GetControl

呼叫這個成員函式，以抓取與 `CDataPathProperty` 物件相關聯的 `COleControl` 物件。

```
COleControl* GetControl();
```

### <a name="return-value"></a>傳回值

傳回與 `CDataPathProperty` 物件相關聯之 OLE 控制項的指標。 如果沒有相關聯的控制項，則為 Null。

##  <a name="getpath"></a>CDataPathProperty：： GetPath

呼叫這個成員函式來抓取路徑、設定 `CDataPathProperty` 物件的建立時間，或在 `Open`中指定，或在先前的 `SetPath` 成員函式呼叫中指定。

```
CString GetPath() const;
```

### <a name="return-value"></a>傳回值

傳回屬性本身的路徑名稱。 如果未指定路徑，則可以是空的。

##  <a name="open"></a>CDataPathProperty：： Open

呼叫這個成員函式，起始相關聯控制項之非同步屬性的載入。

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
要與這個 `CDataPathProperty` 物件相關聯之 OLE 控制項物件的指標。

*pError*<br/>
檔案例外狀況的指標。 發生錯誤時，將會設定為原因。

*lpszPath*<br/>
可以是絕對或相對路徑，用來建立可參考屬性實際絕對位置的非同步名字標記。 `CDataPathProperty` 使用 Url，而不是檔案名。 如果您想要檔案的 `CDataPathProperty` 物件，請在路徑前面加上 `file://`。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

函式會嘗試從控制項取得 `IBindHost` 介面。

在不使用路徑呼叫 `Open` 之前，必須設定屬性的路徑值。 這可以在建立物件時，或藉由呼叫 `SetPath` 成員函式來完成。

在不使用控制項呼叫 `Open` 之前，ActiveX 控制項（先前稱為 OLE 控制項）可以與物件建立關聯。 這可以在建立物件時，或藉由呼叫 `SetControl`來完成。

`CDataPathProperty`也可以使用[CAsyncMonikerFile：： Open](../../mfc/reference/casyncmonikerfile-class.md#open)的所有多載。

##  <a name="resetdata"></a>CDataPathProperty：： ResetData

呼叫此函式可取得 `CAsyncMonikerFile::OnDataAvailable`，以通知容器控制項屬性已變更，而且以非同步方式載入的所有資訊都不再有用。

```
virtual void ResetData();
```

### <a name="remarks"></a>備註

開啟應該重新開機。 衍生類別可以針對不同的預設值覆寫此函數。

##  <a name="setcontrol"></a>CDataPathProperty：： SetControl

呼叫這個成員函式，將非同步 OLE 控制項與 `CDataPathProperty` 物件產生關聯。

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>參數

*pControl*<br/>
要與屬性相關聯之非同步 OLE 控制項的指標。

##  <a name="setpath"></a>CDataPathProperty：： SetPath

呼叫這個成員函式以設定屬性的路徑名稱。

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
以非同步方式載入的屬性路徑，可能是絕對或相對路徑。 `CDataPathProperty` 使用 Url，而不是檔案名。 如果您想要檔案的 `CDataPathProperty` 物件，請在路徑前面加上 `file://`。

## <a name="see-also"></a>另請參閱

[MFC 範例影像](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
