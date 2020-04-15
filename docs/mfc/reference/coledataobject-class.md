---
title: COleDataObject 類別
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: 5e1545a033ab482e838fbc944b0ca9b3e543d651
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366136"
---
# <a name="coledataobject-class"></a>COleDataObject 類別

用於資料傳輸以透過剪貼簿、拖放作業或內嵌 OLE 項目擷取各種格式的資料。

## <a name="syntax"></a>語法

```
class COleDataObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleData物件:COleData物件](#coledataobject)|建構 `COleDataObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleData物件:附加](#attach)|將指定的 OLE 資料物件`COleDataObject`附加到 。|
|[COleData物件::附加剪板](#attachclipboard)|附加剪貼簿上的數據物件。|
|[COleData物件::開始貨幣格式](#beginenumformats)|準備一個或多個後續`GetNextFormat`呼叫。|
|[COleData物件::D](#detach)|分離關聯的`IDataObject`物件。|
|[COleData物件:取得資料](#getdata)|以指定格式複製附加的 OLE 資料物件的資料。|
|[COleData物件:取得檔案資料](#getfiledata)|以指定格式將附加的 OLE`CFile`資料 物件的資料複製到指標中。|
|[COleData物件:取得全球資料](#getglobaldata)|指定格式會附加的 OLE`HGLOBAL`資料的資料複製到 。|
|[COleData物件:取得下一個格式](#getnextformat)|傳回下一種可用的資料格式。|
|[COleData物件:資料可用](#isdataavailable)|檢查資料是否以指定格式可用。|
|[COleData物件:發佈](#release)|分離並釋放關聯的`IDataObject`物件。|

## <a name="remarks"></a>備註

`COleDataObject`沒有基類。

這些類型的數據傳輸包括源和目標。 數據源作為[COleDataSource](../../mfc/reference/coledatasource-class.md)類的物件實現。 每當目標應用程式將數據丟棄到其中或被要求從剪貼簿執行粘貼操作時,必須創建`COleDataObject`類的物件。

此類使您能夠確定數據是否存在指定格式。 您還可以枚舉可用的數據格式或檢查給定格式是否可用,然後以首選格式檢索數據。 對象檢索可以通過幾種不同的方式完成,包括使用[CFile、HGLOBAL](../../mfc/reference/cfile-class.md)或`STGMEDIUM`結構。

有關詳細資訊,請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

有關在應用程式中使用數據物件的詳細資訊,請參閱文章[「數據物件和數據來源 (OLE)」。。](../../mfc/data-objects-and-data-sources-ole.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`COleDataObject`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleData物件:附加

調用此函數將`COleDataObject`物件與 OLE 數據物件相關聯。

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>參數

*lpDataObject*<br/>
指向 OLE 資料物件。

*B 自動釋放*<br/>
如果應在銷毀物件時釋放 OLE`COleDataObject`數據物件 ,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[IDataObject。](/windows/win32/api/objidl/nn-objidl-idataobject)

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleData物件::附加剪板

呼叫此函數以將當前剪貼簿上的數據物件附加到`COleDataObject`該物件。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 調用此函數將鎖定剪貼簿,直到釋放此數據物件。 數據物件在的`COleDataObject`析構函數中釋放。 有關詳細資訊,請參閱 Win32 文檔中的[「打開剪板](/windows/win32/api/winuser/nf-winuser-openclipboard)」和[「關閉剪貼簿](/windows/win32/api/winuser/nf-winuser-closeclipboard)」。

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleData物件::開始貨幣格式

呼叫此函數以準備後續呼叫,`GetNextFormat`以便從項目索資料格式的清單。

```
void BeginEnumFormats();
```

### <a name="remarks"></a>備註

呼叫`BeginEnumFormats`後 將儲存此資料物件支援的第一個格式的位置。 對`GetNextFormat`的連續調用將枚舉數據物件中可用格式的清單。

要檢查給定格式的資料可用性,請使用[COleDataObject::isData 可用](#isdataavailable)。

有關詳細資訊,請參閱 Windows SDK 中的[IDataObject:enumFormatEtc。](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc)

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleData物件:COleData物件

建構 `COleDataObject` 物件。

```
COleDataObject();
```

### <a name="remarks"></a>備註

呼叫[COleDataObject::附加](#attach)或[COleDataObject:在](#attachclipboard)呼叫其他`COleDataObject`函數之前必須進行附加剪板。

> [!NOTE]
> 由於拖放處理程式的參數之一是指向的`COleDataObject`指標,因此無需調用此構造函數來支援拖放。

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleData物件::D

調用此函數以將其`COleDataObject`物件從其關聯的 OLE 數據物件中分離出來,而不釋放數據物件。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>傳回值

指向分離的 OLE 資料物件的指標。

### <a name="remarks"></a>備註

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleData物件:取得資料

呼叫此函數以從指定格式的項檢索資料。

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
返回數據的格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpStg 中*<br/>
指向將接收數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

*lpFormatEtc*<br/>
指向描述要返回數據的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[IDataObject:獲取資料](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)[、STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleData物件:取得檔案資料

呼叫此函數以建立`CFile``CFile`或派生物件,並將指定格式的數據檢索`CFile`到指標中。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
返回數據的格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpFormatEtc*<br/>
指向描述要返回數據的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="return-value"></a>傳回值

指標指向包含數據`CFile`的新`CFile`物件或派生物件(如果成功);否則 NULL。

### <a name="remarks"></a>備註

從資料儲存的媒體,傳回值指向的實際類型可以是`CFile`,`CSharedFile``COleStreamFile`或 。

> [!NOTE]
> 由`CFile`此函數的返回值訪問的對象歸調用方所有。 呼叫者有責任**刪除**該物件`CFile`, 從而關閉檔案。

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleData物件:取得全球資料

呼叫此函數以分配全域記憶體區塊,並將指定格式的資料檢索到 HGLOBAL 中。

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
返回數據的格式。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpFormatEtc*<br/>
指向描述要返回數據的格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 如果要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊,請提供此參數的值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果成功,則包含數據的全域記憶體塊的句柄;否則 NULL。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleData物件:取得下一個格式

重複呼叫此函數以獲取可用於從項檢索資料的所有格式。

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向在函數調用返回時接收格式資訊的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

### <a name="return-value"></a>傳回值

如果其他格式可用,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫[COleDataObject::BeginEnum 格式](#beginenumformats)後,儲存此資料物件支援的第一個格式的位置。 對`GetNextFormat`的連續調用將枚舉數據物件中可用格式的清單。 使用這些函數列出可用的格式。

要檢查給定格式的可用性,請致電[COleDataObject::IsData 可用](#isdataavailable)。

有關詳細資訊,請參閱[IEnumXXXX::下一個](/previous-versions//ms695273\(v=vs.85\))在 Windows SDK 中。

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleData物件:資料可用

呼叫此函數以確定特定格式是否可用於從 OLE 項檢索資料。

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
剪貼簿數據格式用於*lpFormatEtc*指向的結構中。 此參數可以是預先定義的剪貼簿格式之一,也可以是本機 Windows[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數傳回的值。

*lpFormatEtc*<br/>
指向描述所需格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。 僅當要指定*cfFormat*指定的剪貼簿格式之外的其他格式資訊時,才為此參數提供值。 如果為 NULL,則預設值`FORMATETC`用於結構中的其他欄位。

### <a name="return-value"></a>傳回值

如果數據以指定格式可用,則非零;否則 0。

### <a name="remarks"></a>備註

在呼叫`GetData`之前,此功能很有`GetFileData``GetGlobalData`用 。

有關詳細資訊,請參閱[IDataObject::在](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata)Windows SDK 中查詢獲取數據和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

有關詳細資訊,請參閱 Windows SDK 中的[註冊剪貼簿格式](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:查詢接受資料](../../mfc/reference/cricheditview-class.md#queryacceptdata)。

## <a name="coledataobjectrelease"></a><a name="release"></a>COleData物件:發佈

呼叫此函數以釋放以前與`COleDataObject`該物件關聯的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)物件的擁有權。

```
void Release();
```

### <a name="remarks"></a>備註

通過調用`Attach``AttachClipboard`或顯式或由框架與關聯`IDataObject``COleDataObject`。 如果的`Attach` *bAutoRelease*`IDataObject`參數為 FALSE,則不會釋放物件。 在這種情況下,調用方負責`IDataObject`通過調用[IUnknown::::釋放](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)來釋放 。

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 類別](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
