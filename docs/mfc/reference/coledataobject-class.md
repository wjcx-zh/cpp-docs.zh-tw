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
ms.openlocfilehash: 95a19b20e0acc4ae45a953eee5a1c4d2bfb3e9da
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326721"
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
|[COleDataObject::COleDataObject](#coledataobject)|建構 `COleDataObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDataObject::Attach](#attach)|附加至指定的 OLE 資料物件`COleDataObject`。|
|[COleDataObject::AttachClipboard](#attachclipboard)|將剪貼簿上的資料物件。|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|準備一或更後續`GetNextFormat`呼叫。|
|[COleDataObject::Detach](#detach)|卸離相關聯`IDataObject`物件。|
|[COleDataObject::GetData](#getdata)|從附加的 OLE 資料物件中指定的格式資料複製。|
|[COleDataObject::GetFileData](#getfiledata)|將資料複製到附加的 OLE 資料物件從`CFile`指標指定的格式。|
|[COleDataObject::GetGlobalData](#getglobaldata)|將資料複製到附加的 OLE 資料物件從`HGLOBAL`中指定的格式。|
|[COleDataObject::GetNextFormat](#getnextformat)|傳回下一步 的資料格式。|
|[COleDataObject::IsDataAvailable](#isdataavailable)|檢查是否有指定的格式資料。|
|[COleDataObject::Release](#release)|卸離，並釋放相關聯`IDataObject`物件。|

## <a name="remarks"></a>備註

`COleDataObject` 沒有基底類別。

這些類型的資料傳輸包括來源和目的地。 資料來源實作物件的形式[COleDataSource](../../mfc/reference/coledatasource-class.md)類別。 每當接收端應用程式在其中放入的資料，或被要求從剪貼簿 的物件執行貼上作業`COleDataObject`必須建立類別。

這個類別可讓您判斷資料是否存在於指定的格式。 您可以也列舉 可用的資料格式或檢查指定的格式是否可用，並接著擷取的資料以偏好的格式。 可以透過幾種不同的方式，包括使用完成物件擷取[CFile](../../mfc/reference/cfile-class.md)、 HGLOBAL，或在`STGMEDIUM`結構。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) Windows SDK 中的結構。

如需有關如何在您的應用程式中使用資料物件的詳細資訊，請參閱[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`COleDataObject`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="attach"></a>  COleDataObject::Attach

呼叫此函式來建立關聯`COleDataObject`與 OLE 資料物件的物件。

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>參數

*lpDataObject*<br/>
OLE 資料物件的點。

*bAutoRelease*<br/>
如果應該 OLE 資料物件，則為 TRUE 時釋放`COleDataObject`物件已終結，否則為 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) Windows SDK 中。

##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard

呼叫此函式以目前在剪貼簿的資料物件連接`COleDataObject`物件。

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
>  呼叫此函式鎖定剪貼簿，直到釋放這個資料物件。 釋放資料物件的解構函式中`COleDataObject`。 如需詳細資訊，請參閱 < [OpenClipboard](/windows/desktop/api/winuser/nf-winuser-openclipboard)並[CloseClipboard](/windows/desktop/api/winuser/nf-winuser-closeclipboard) Win32 文件中。

##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats

呼叫此函式，以準備進行後續呼叫`GetNextFormat`從項目擷取的資料格式的清單。

```
void BeginEnumFormats();
```

### <a name="remarks"></a>備註

若要在呼叫之後`BeginEnumFormats`，儲存這個資料物件支援的第一個格式的位置。 後續呼叫`GetNextFormat`會列舉資料物件中的可用格式的清單。

若要檢查的指定格式的資料可用性，請使用[COleDataObject::IsDataAvailable](#isdataavailable)。

如需詳細資訊，請參閱 < [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) Windows SDK 中。

##  <a name="coledataobject"></a>  COleDataObject::COleDataObject

建構 `COleDataObject` 物件。

```
COleDataObject();
```

### <a name="remarks"></a>備註

呼叫[COleDataObject::Attach](#attach)或是[COleDataObject::AttachClipboard](#attachclipboard)必須進行其他呼叫之前`COleDataObject`函式。

> [!NOTE]
>  因為其中一個拖放處理常式的參數是一個指向`COleDataObject`，則不需要呼叫這個建構函式，以支援拖曳和卸除。

##  <a name="detach"></a>  COleDataObject::Detach

呼叫此函式可卸離`COleDataObject`來自未釋放的資料物件，而其相關聯 OLE 資料物件的物件。

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>傳回值

卸離 OLE 資料物件的指標。

### <a name="remarks"></a>備註

##  <a name="getdata"></a>  COleDataObject::GetData

呼叫此函式可擷取指定的格式中的項目中的資料。

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)會接收資料的結構。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，描述要傳回的資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果為 NULL，預設值會用於中的其他欄位`FORMATETC`結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)， [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)，並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="getfiledata"></a>  COleDataObject::GetFileData

呼叫此函式來建立`CFile`或是`CFile`-衍生物件，並擷取資料到指定的格式`CFile`指標。

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，描述要傳回的資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果為 NULL，預設值會用於中的其他欄位`FORMATETC`結構。

### <a name="return-value"></a>傳回值

新指標`CFile`或`CFile`-衍生物件，包含資料，如果成功，否則為 NULL。

### <a name="remarks"></a>備註

根據資料儲存在媒體，可能的傳回值所指向的實際型別`CFile`， `CSharedFile`，或`COleStreamFile`。

> [!NOTE]
>  `CFile`由呼叫端擁有存取此函式的傳回值的物件。 呼叫端負責**刪除**`CFile`物件，藉此關閉檔案。

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData

呼叫此函式來配置全域記憶體區塊，並在指定的格式中的資料擷取至 HGLOBAL。

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
要傳回資料的格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，描述要傳回的資料格式。 如果您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果為 NULL，預設值會用於中的其他欄位`FORMATETC`結構。

### <a name="return-value"></a>傳回值

包含成功; 如果資料的全域記憶體區塊的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat

呼叫此函式重複，以取得所有可用項目從擷取資料的格式。

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)函式呼叫傳回時，會接收之格式資訊的結構。

### <a name="return-value"></a>傳回值

另一種格式可使用; 如果為非零否則為 0。

### <a name="remarks"></a>備註

若要在呼叫之後[COleDataObject::BeginEnumFormats](#beginenumformats)，儲存這個資料物件支援的第一個格式的位置。 後續呼叫`GetNextFormat`會列舉資料物件中的可用格式的清單。 您可以使用這些函式，列出可用的格式。

若要檢查指定的格式的可用性，請呼叫[COleDataObject::IsDataAvailable](#isdataavailable)。

如需詳細資訊，請參閱 < [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) Windows SDK 中。

##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable

呼叫此函式來判斷特定的格式是否可供擷取 OLE 項目中的資料。

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>參數

*cfFormat*<br/>
使用結構中的剪貼簿資料格式所指向*lpFormatEtc*。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata)函式。

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構描述所需的格式。 只有當您想要指定超過所指定的剪貼簿格式的其他格式資訊，請為此參數提供值*cfFormat*。 如果為 NULL，預設值會用於中的其他欄位`FORMATETC`結構。

### <a name="return-value"></a>傳回值

如果指定的格式，在可用資料，非零值。否則為 0。

### <a name="remarks"></a>備註

這個功能很有用，再呼叫`GetData`， `GetFileData`，或`GetGlobalData`。

如需詳細資訊，請參閱 < [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata)並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

如需詳細資訊，請參閱 < [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)。

##  <a name="release"></a>  COleDataObject::Release

呼叫此函式來釋放擁有權[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)物件，先前關聯`COleDataObject`物件。

```
void Release();
```

### <a name="remarks"></a>備註

`IDataObject`與相關聯`COleDataObject`藉由呼叫`Attach`或`AttachClipboard`明確或由架構。 如果*bAutoRelease*的參數`Attach`為 FALSE，`IDataObject`將不會釋放物件。 在此情況下，呼叫端負責釋放`IDataObject`藉由呼叫[iunknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 類別](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
